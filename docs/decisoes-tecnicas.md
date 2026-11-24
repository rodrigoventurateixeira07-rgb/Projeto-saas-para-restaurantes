# Decisões técnicas

Atualização: 24/11/2026. Registro inicial. **Todas as decisões abaixo estão propostas e aguardam revisão da equipe; nenhuma escolha de stack foi confirmada nem implementada.**

## Registro

| ID | Proposta | Motivo | Alternativa e custo | Quando revisar |
| --- | --- | --- | --- | --- |
| DT-01 | Começar com aplicação web responsiva | Acesso por link em aparelhos existentes | Aplicativo nativo adiciona publicação e manutenção por plataforma | Se houver necessidade validada de recurso nativo |
| DT-02 | Usar monólito modular | Menos serviços para desenvolver e operar | Microserviços acrescentam comunicação, implantação e observabilidade distribuídas | Quando escala ou organização justificarem separação |
| DT-03 | Avaliar Python/Django com templates HTML | Aproveita Python da equipe e reúne autenticação, formulários e persistência | Stack JavaScript pode fazer sentido se a experiência do parceiro for maior | Antes do primeiro código, após pequeno experimento com dados fictícios |
| DT-04 | Avaliar PostgreSQL como banco principal | Modelagem relacional de pedidos e necessidade de integridade | SQLite é simples para experimentos, mas não deve representar sozinho os testes do banco de produção proposto | Na escolha do provedor e dos requisitos de recuperação |
| DT-05 | Compartilhar banco com escopo de restaurante obrigatório | Custo inicial menor que infraestrutura por cliente | Banco ou schema por loja aumenta isolamento operacional e esforço de migrations | Antes de hospedar múltiplas lojas; avaliar também RLS |
| DT-06 | Manter pagamento do consumidor fora da plataforma no MVP | Reduz dependências e complexidade de conciliação | Provedor externo com checkout hospedado exige integração e tratamento de eventos | Após demanda validada e desenho de segurança |
| DT-07 | Começar painel com consultas periódicas | Implementação e depuração mais simples | WebSocket adiciona conexões e estado operacional | Se medição mostrar atraso ou carga inadequados |
| DT-08 | Provisionar lojas manualmente no piloto | Evita onboarding e cobrança automática prematuros | Autosserviço reduz esforço futuro, mas amplia abuso e suporte inicial | Após aprender com implantações acompanhadas |
| DT-09 | Versionar apenas código, exemplos e documentação pública | Repositório é público e não é arquivo operacional de clientes | Armazenamento privado adequado para contratos, dados e evidências restritas | A cada nova classe de arquivo |

## Critérios para escolher a stack

Comparar experiência real dos dois integrantes; tempo para entregar uma fatia completa; autenticação e autorização; migrations; testes; manutenção; custo e recuperação do provedor. Registrar versões suportadas, política de atualização e dependências quando a escolha for feita. Não selecionar tecnologia apenas pela popularidade.

## Pendências antes do desenvolvimento

- Definir stack final e versões, incluindo estratégia de frontend.
- Escolher autenticação e recuperação de conta; avaliar MFA para gestores e administração.
- Decidir aplicação de RLS ou justificativa para outra estratégia, com testes de isolamento.
- Escolher hospedagem, banco, região, e-mail, imagens e backup com orçamento real.
- Definir configurações lidas pela aplicação e atualizar `.env.example` sem segredos.
- Definir retenção, expiração do acompanhamento, backup e rotina de incidentes.

## Como registrar novas decisões

Para cada mudança relevante, incluir ID, data, status (`proposta`, `aceita`, `substituída`), contexto, escolha, alternativas, consequências, responsável e link para evidência/issue/PR. Se a decisão for substituída, manter a justificativa histórica e apontar a nova.

## Fontes e bases

Consulta externa: 24/11/2026. Recomendações e trade-offs são avaliação interna para este projeto.

- [Django — segurança](https://docs.djangoproject.com/en/stable/topics/security/): recursos a avaliar na stack sugerida.
- [PostgreSQL — segurança por linha](https://www.postgresql.org/docs/current/ddl-rowsecurity.html): possibilidades e limites da proteção no banco.
- [Arquitetura proposta](arquitetura.md), [requisitos não funcionais](requisitos-nao-funcionais.md) e [roadmap](roadmap.md): contexto das decisões.
