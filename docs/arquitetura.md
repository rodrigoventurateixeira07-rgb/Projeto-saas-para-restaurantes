# Arquitetura

Atualização: 24/11/2026. Status: **proposta**, ainda sem código, infraestrutura ou escolha definitiva de stack. Ver [registro de decisões](decisoes-tecnicas.md).

## Abordagem inicial

Aplicação web responsiva em um monólito modular: catálogo, pedidos e administração no mesmo serviço, com limites claros entre módulos. A recomendação inicial é avaliar **Python/Django, páginas renderizadas no servidor com HTML/CSS e JavaScript pontual, e PostgreSQL**. Isso aproveita a base de Python da equipe e reduz o número de componentes a operar; confirmar experiência do outro integrante antes da escolha.

Um frontend separado continua possível se a equipe justificar o custo. Não há necessidade comprovada de microserviços, fila, Kubernetes ou aplicativo nativo para o piloto.

## Componentes e responsabilidades

| Componente | Responsabilidade | Limite de confiança |
| --- | --- | --- |
| Cardápio e checkout públicos | Exibir catálogo e coletar intenção de pedido | Entrada do navegador nunca define preço ou permissão |
| Painel autenticado | Configurar loja e operar pedidos | Sessão e vínculo com a loja verificados a cada operação |
| Aplicação no servidor | Autorizar, validar, calcular e gravar | Centraliza regras; rejeita campos inconsistentes |
| PostgreSQL | Persistência transacional, integridade e índices | Conta da aplicação com privilégios mínimos; sem acesso público irrestrito |
| Armazenamento de imagens | Guardar mídia de catálogo validada | Conteúdo não executável e sem dados privados do consumidor |
| E-mail transacional | Convites e recuperação de conta | Sem senhas, tokens ou conteúdo completo de pedidos em logs |
| Operação | Backup, monitoramento e alertas | Acesso individual, restrito e auditado |

## Modelo conceitual

| Entidade | Campos e relações essenciais |
| --- | --- |
| Restaurante | Identificador, slug público, nome, fuso, horários e situação operacional |
| Usuário e vínculo | Identidade, restaurante, função, situação e convites; autorização deriva do vínculo autenticado |
| Categoria e produto | Restaurante, nome, preço em decimal/centavos, disponibilidade e imagem |
| Grupo e opção de adicional | Restaurante, produto associado, mínimo/máximo e preço |
| Região de entrega | Restaurante, bairro ativo e taxa; MVP não calcula rota |
| Pedido | Restaurante, estado, versão, totais, modalidade, contato mínimo, endereço se entrega e chave de idempotência |
| Item do pedido | Pedido e cópia histórica de nome, quantidade, preços e adicionais |
| Evento do pedido | Pedido, ator, estado anterior/novo, horário e motivo quando necessário |
| Acesso de acompanhamento | Pedido, hash de token aleatório, validade e revogação |

Relacionamentos entre entidades operacionais precisam preservar a mesma loja. Usar restrições e validações transacionais adequadas; um `restaurant_id` em cada tabela, sozinho, não impõe isolamento.

## Separação dos restaurantes

- Resolver a loja a partir da rota pública para catálogo e criação de pedido. Isso não permite acessar o painel interno.
- No painel, exigir sessão e vínculo ativo; validar o escopo em leitura, escrita, exportação, arquivos e tarefas administrativas.
- Centralizar consultas com escopo de restaurante e testar tentativas de trocar identificadores.
- Incluir loja em índices e chaves de unicidade, como `(restaurant_id, idempotency_key)`.
- Evitar cache privado no início. Se adicionado, a chave deve incluir loja, identidade e política de autorização pertinente.
- Avaliar RLS do PostgreSQL como defesa adicional antes de hospedar várias lojas. RLS depende de configuração de políticas, papéis e contexto de conexão; não substitui autorização da aplicação. A decisão e os testes precisam constar do registro técnico.

## Fluxo de criação do pedido

1. Navegador envia itens, modalidade, dados mínimos e chave aleatória da tentativa.
2. Servidor resolve loja, verifica horário/pausa e aplica limites contra abuso.
3. Busca catálogo da loja, valida adicionais e endereço e recalcula preços. Se houver mudança no valor mostrado, pede nova confirmação.
4. Em transação, grava pedido, itens e evento inicial. Restrição de unicidade impede duplicação da tentativa; retry retorna o pedido existente após conferir o contexto e os dados da tentativa.
5. Somente após commit responde com confirmação de recebimento e acesso de acompanhamento.
6. Painel busca novidades periodicamente no início; mudança de status confere a versão para tratar concorrência.

O atendimento não depende de disparo no WhatsApp. Um contato externo pode ser exibido como alternativa, mas não é prova de persistência ou de aceite do pedido. Não enviar dados pessoais em parâmetros de URLs externas.

## Ambientes e operação

- Desenvolvimento e homologação usam dados fictícios e credenciais próprias.
- Produção recebe HTTPS, debug desativado, segredos por ambiente, backup e monitoramento.
- Datas são armazenadas em UTC; horários de atendimento usam o fuso configurado da loja, com padrão proposto `America/Sao_Paulo`.
- Migrações devem ser revisadas; antes de alteração com risco de perda, preparar recuperação e testar em homologação.
- Escolher provedor por custo total, região, restauração, suporte, contrato e capacidade da equipe. Nenhum serviço está contratado.

## Fontes e bases

Consultadas em 24/11/2026. O desenho e as escolhas acima são propostas internas.

- [Django — segurança](https://docs.djangoproject.com/en/stable/topics/security/): recursos e limites do framework sugerido.
- [Django — transações](https://docs.djangoproject.com/en/stable/topics/db/transactions/): referência de atomicidade.
- [PostgreSQL — políticas de segurança por linha](https://www.postgresql.org/docs/current/ddl-rowsecurity.html): referência para avaliar RLS, incluindo exceções de papéis privilegiados.
- [Requisitos funcionais](requisitos-funcionais.md) e [segurança e LGPD](seguranca-e-lgpd.md): regras que o desenho precisa atender.
