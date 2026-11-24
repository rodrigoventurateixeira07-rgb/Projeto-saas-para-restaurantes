# Requisitos funcionais

Atualização: 24/11/2026. Status: backlog proposto, sem funcionalidades implementadas. **MVP** é obrigatório para o piloto; **depois** depende da validação. Revisar com o estabelecimento antes de desenvolver.

## Perfis

- **Consumidor:** consulta cardápio e faz pedido sem conta obrigatória.
- **Atendente:** opera os pedidos do restaurante ao qual tem acesso.
- **Dono/gerente:** configura sua loja, usuários e relatórios.
- **Administrador da plataforma:** provisiona lojas e presta suporte com acesso restrito e auditado; não é um perfil comum da loja.

O identificador de restaurante enviado pelo navegador não concede permissão. Toda operação interna precisa de autenticação e vínculo válido com a loja.

## Backlog e critérios de aceite

| ID | Requisito | Prioridade | Critério de aceite principal |
| --- | --- | --- | --- |
| RF-01 | Provisionar restaurante e primeiro gerente | MVP | Administrador cria loja com endereço público único e convite de uso único; não define senha compartilhada |
| RF-02 | Entrar, sair e recuperar acesso | MVP | Credencial inválida não abre sessão; logout invalida a sessão; recuperação expira, é de uso único e não revela se um e-mail existe |
| RF-03 | Gerenciar equipe e funções | MVP | Gerente convida/desativa atendente; atendente não altera permissões nem acessa outra loja |
| RF-04 | Configurar identidade e operação | MVP | Gerente define nome, imagem validada, horários, pausa manual, retirada e bairros/taxas de entrega; configuração persiste |
| RF-05 | Gerenciar categorias e produtos | MVP | Gerente cria/edita nome, descrição, preço, imagem e disponibilidade; produto indisponível não pode ser comprado |
| RF-06 | Configurar adicionais | MVP | Grupo define mínimo e máximo de escolhas e preços; servidor rejeita seleção fora dos limites ou de outro produto |
| RF-07 | Consultar cardápio público | MVP | Consumidor acessa por link sem login e vê apenas o catálogo público da loja escolhida |
| RF-08 | Montar carrinho | MVP | Quantidades, adicionais, subtotal, taxa e total ficam claros; servidor recalcula tudo antes de gravar e exige nova confirmação se o preço mudou |
| RF-09 | Informar retirada ou entrega | MVP | Entrega exige bairro atendido e endereço; retirada não exige endereço residencial; telefone e nome para contato são validados |
| RF-10 | Enviar pedido | MVP | Pedido e itens são gravados juntos; reenvio da mesma tentativa retorna o mesmo pedido; tela só informa recebimento após sucesso do servidor |
| RF-11 | Aceitar e acompanhar pedidos | MVP | Painel mostra novos pedidos e horário; atendente aceita ou cancela e segue apenas transições válidas; duas ações concorrentes não corrompem o status |
| RF-12 | Consultar andamento pelo consumidor | MVP | Token aleatório permite ver apenas status e resumo mínimo do próprio pedido; código sequencial ou ID sozinho não dá acesso; outro pedido não é exposto |
| RF-13 | Consultar histórico e resumo | MVP | Gerente filtra período; soma somente pedidos concluídos e separa cancelados; não classifica venda como pagamento confirmado |
| RF-14 | Exportar pedidos da loja | MVP | Gerente exporta somente sua loja, com colunas mínimas; operação é auditada e saída impede fórmulas executáveis em planilhas |
| RF-15 | Apoiar solicitações de privacidade | MVP | Canal de contato definido e procedimento restrito para localizar, exportar, corrigir ou excluir/anonimizar dados conforme análise de identidade e retenção |
| RF-16 | Registrar forma de pagamento combinada | MVP | Consumidor escolhe entre formas presenciais aceitas; tela informa que não há cobrança online nem confirmação automática de pagamento |
| RF-17 | Integrar pagamentos por provedor externo | Depois | Só entra com desenho de autorização, assinatura de eventos, conciliação e tratamento de falhas |
| RF-18 | Integrar marketplaces, fiscal ou automação de mensagens | Depois | Só entra após validar API oficial, permissões, contrato, custo e necessidade comercial |

## Regras do pedido

- **Estados:** `recebido` → `aceito` → `em_preparo` → `pronto`. Na retirada: `pronto` → `concluido`. Na entrega: `pronto` → `saiu_para_entrega` → `concluido`.
- Permitir cancelamento de qualquer estado não terminal por atendente/gerente, com motivo e histórico. `concluido` e `cancelado` são terminais. Uma eventual correção posterior exige fluxo próprio, fora do MVP.
- Enviar pedido não significa aceite. Mostrar isso ao consumidor e não iniciar preparo automaticamente.
- Rejeitar novo pedido fora do horário, durante pausa ou sem itens válidos. Mostrar o motivo sem apagar o carrinho.
- Trabalhar em reais, com cálculo decimal ou centavos inteiros. Não usar ponto flutuante binário para dinheiro.
- Congelar nome, quantidade, adicionais e preço dos itens no momento da compra. Edição futura do catálogo não altera pedidos anteriores.
- Vínculos entre itens, adicionais e loja precisam ser consistentes. Não aceitar ID de outra loja nem em campos ocultos.
- Toda mudança de status registra ator, instante e versão anterior; notificações não podem anteceder a confirmação da gravação.
- O link de acompanhamento é uma credencial de acesso: não incluir em analytics, logs ou mensagem pública. Mostrar só informação necessária; proteger contra tentativas em massa e expirar o acesso conforme política definida antes do piloto.

## Cenários críticos para implementação futura

1. Trocar IDs de loja, produto, pedido e exportação nunca permite ler ou alterar outra loja.
2. Alterar o preço no navegador não muda o total calculado no servidor.
3. Um duplo clique ou retry após timeout não gera dois pedidos.
4. Produto fica indisponível entre carrinho e envio: servidor rejeita e orienta revisão.
5. Falha ao salvar um item desfaz o pedido inteiro.
6. Loja fechada não aceita novo pedido; pedidos já recebidos continuam visíveis à operação.

## Fontes e bases

Consulta externa: 24/11/2026. As regras e os critérios acima são propostas próprias, não comportamento atribuído aos concorrentes.

- [Goomer — planos](https://goomer.com.br/planos): referência de catálogo, opcionais e operação; não implica equivalência de escopo.
- [Análise de concorrentes](analise-de-concorrentes.md): origem da comparação de mercado.
- [Django — transações](https://docs.djangoproject.com/en/stable/topics/db/transactions/): referência técnica para gravação atômica, caso a stack sugerida seja adotada.
- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/): base para verificar autorização e controles de aplicação.
