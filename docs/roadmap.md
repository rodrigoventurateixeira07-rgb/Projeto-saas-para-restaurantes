# Roadmap

Atualização: 24/11/2026. **Somente a documentação inicial foi preparada.** Entrevistas, protótipos, desenvolvimento e piloto ainda não foram realizados. Ordem sugerida para uma equipe pequena; não há prazo de lançamento comprometido.

## Etapas e condições para avançar

| Etapa | Trabalho | Entregas | Condição de saída | Situação |
| --- | --- | --- | --- | --- |
| 0. Organizar | Estrutura, visão, pesquisa e backlog | Documentos deste repositório e fontes datadas | Equipe lê e identifica pendências | Base inicial preparada; revisão pendente |
| 1. Descobrir | Entrevistar 3–5 estabelecimentos, mapear operação e custos atuais | Notas anonimizadas e lista das dores recorrentes | Problema prioritário e possível piloto identificados | Pendente |
| 2. Validar solução | Desenhar cardápio, checkout e painel; testar com 5 consumidores e 2 operadores | Protótipo, roteiro e resultados em `design/prototipos/` | Fluxo compreensível; escopo e regras revisados com piloto | Pendente |
| 3. Definir base técnica e dados | Comparar stack/provedores, modelar dados e revisar segurança | Decisões registradas, orçamento, inventário e desenho de permissões | Stack escolhida, custos aceitos pela equipe e controles planejados | Pendente |
| 4. Construir uma fatia completa | Loja, autenticação, cardápio, carrinho, pedido e painel | Fluxo completo com dados fictícios em homologação | Pedido persiste, reaparece após recarga e pode ser atendido | Pendente |
| 5. Preparar operação | Completar RF do MVP; testar isolamento, recuperação e privacidade | Evidências de teste, backup restaurado, avisos e procedimento de suporte | Critérios de liberação abaixo atendidos | Pendente |
| 6. Rodar piloto limitado | Acompanhar um estabelecimento e comparar com a rotina anterior | Métricas, ocorrências, horas de suporte e feedback | Fluxo estável e disposição para continuar/pagar | Pendente |
| 7. Revisar viabilidade | Avaliar retenção, margem e pedidos de melhoria | Decisão de continuar, ajustar recorte ou interromper | Evidência suficiente para ampliar com suporte sustentável | Pendente |

Não iniciar integrações de pagamento ou fiscal por estarem no produto de um concorrente. Cada expansão precisa ter demanda comprovada e revisão própria de riscos e custos.

## Ordem sugerida dentro da implementação

1. Provisionamento, sessões e autorização por restaurante (RF-01 a RF-03).
2. Configuração operacional e catálogo (RF-04 a RF-07).
3. Carrinho, entrega/retirada e gravação atômica (RF-08 a RF-10 e RF-16).
4. Operação, status, acompanhamento e histórico (RF-11 a RF-13).
5. Exportação, atendimento à privacidade e rotinas de produção (RF-14 e RF-15).

Testes críticos acompanham cada fluxo, especialmente isolamento entre lojas. Não deixar autorização para o fim.

## Condições para receber dados reais no piloto

- [ ] Requisitos do MVP revisados com o restaurante e responsáveis definidos.
- [ ] Testes de duas lojas, preços manipulados, repetição e concorrência aprovados.
- [ ] HTTPS, segredos separados, contas individuais e MFA nos provedores disponíveis.
- [ ] Dados reais ausentes do repositório e da homologação.
- [ ] Restauração de backup ensaiada e limites de recuperação conhecidos.
- [ ] Aviso de privacidade, contrato, papéis, fornecedores e retenção revisados para o caso concreto.
- [ ] Canal de suporte, horário de atendimento e procedimento de incidente definidos.
- [ ] Contingência combinada: em indisponibilidade, pausar o canal digital e receber pedidos pelo contato habitual; conferir pedidos existentes para evitar duplicação.

## Organização da equipe

Definir uma pessoa responsável por produto/piloto e outra por implementação/operação, com revisão cruzada. Essa é uma sugestão de divisão, não uma atribuição já feita. Cada issue deve apontar o RF/RNF relacionado, critério de aceite e responsável.

Semanas ou datas só devem ser atribuídas após a equipe estimar sua disponibilidade. Registrar evidências de conclusão no pull request ou issue correspondente.

## Fontes e bases

Consulta externa: 24/11/2026. A sequência de execução é uma proposta interna.

- [Análise de concorrentes](analise-de-concorrentes.md): base para limitar escopo e investigar diferenciação.
- [ANPD — checklist de segurança](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/checklist-vf.pdf/@@display-file/file): apoio à preparação operacional.
- [Requisitos](requisitos-funcionais.md), [metas de qualidade](requisitos-nao-funcionais.md) e [segurança](seguranca-e-lgpd.md): critérios de liberação do projeto.
