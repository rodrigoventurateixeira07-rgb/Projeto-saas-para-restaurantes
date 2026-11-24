# Projeto SaaS para restaurantes

Planejamento de uma plataforma de cardápio digital e gestão de pedidos para pequenos restaurantes, começando por hamburguerias de bairro.

**Fase atual:** descoberta e documentação inicial. Não há aplicação executável neste repositório. Os requisitos, a arquitetura e as metas abaixo são propostas para discussão e validação com um restaurante piloto; nenhuma funcionalidade está implementada.

**Base documental:** 24/11/2026. Nome comercial, preço, tecnologias e responsáveis por frente ainda precisam ser definidos pela equipe.

## O que queremos resolver

Investigar se pequenos estabelecimentos perdem tempo esclarecendo cardápio, adicionais, valores e andamento de pedidos recebidos por mensagens. A proposta inicial é permitir que o cliente monte seu pedido pelo celular e que a equipe do restaurante o acompanhe em um painel simples.

Já existem concorrentes com recursos semelhantes. A oportunidade precisa ser comprovada por entrevistas e testes: aparência, preço baixo e cardápio próprio, isoladamente, não comprovam diferenciação.

## Estrutura

```text
repositorio/
├── README.md
├── docs/
│   ├── visao-do-produto.md
│   ├── analise-de-concorrentes.md
│   ├── requisitos-funcionais.md
│   ├── requisitos-nao-funcionais.md
│   ├── roadmap.md
│   ├── modelo-de-negocio.md
│   ├── arquitetura.md
│   ├── seguranca-e-lgpd.md
│   ├── decisoes-tecnicas.md
│   └── riscos-do-projeto.md
├── design/
│   ├── referencias/
│   └── prototipos/
├── src/
├── tests/
├── .gitignore
└── .env.example
```

As pastas inicialmente vazias contêm `.gitkeep`, pois o Git não versiona diretórios vazios.

## Guia da documentação

| Documento | Para que serve |
| --- | --- |
| [Visão do produto](docs/visao-do-produto.md) | Público inicial, problema, proposta e limites do MVP |
| [Análise de concorrentes](docs/analise-de-concorrentes.md) | Comparação de cinco fornecedores, preços consultados, divergências e fontes |
| [Requisitos funcionais](docs/requisitos-funcionais.md) | Funcionalidades propostas e critérios de aceite |
| [Requisitos não funcionais](docs/requisitos-nao-funcionais.md) | Metas verificáveis de qualidade, segurança e operação |
| [Roadmap](docs/roadmap.md) | Etapas, entregas e condições para avançar |
| [Modelo de negócio](docs/modelo-de-negocio.md) | Hipóteses de receita, custos e validação comercial |
| [Arquitetura](docs/arquitetura.md) | Componentes, dados, fluxo do pedido e isolamento entre restaurantes |
| [Segurança e LGPD](docs/seguranca-e-lgpd.md) | Dados necessários, controles propostos e preparação do piloto |
| [Decisões técnicas](docs/decisoes-tecnicas.md) | Decisões propostas, alternativas e pendências |
| [Riscos do projeto](docs/riscos-do-projeto.md) | Riscos, sinais de alerta e ações de redução |

## Escopo inicial proposto

- Cardápio responsivo com categorias, produtos, adicionais e disponibilidade.
- Carrinho com preços e regras conferidos no servidor.
- Pedido de retirada ou entrega, sem cadastro obrigatório do consumidor.
- Painel do restaurante com aceite e atualização de status.
- Histórico e resumo operacional de vendas, sem pretensão de contabilidade.
- Acesso individual da equipe e separação dos dados de cada restaurante.

Pagamento online, emissão fiscal, estoque completo, chatbot com IA e integrações com marketplaces ficam fora do MVP. O restaurante mantém seus processos existentes para essas atividades.

## Próximos passos

1. Entrevistar de três a cinco estabelecimentos e selecionar um possível piloto.
2. Confirmar quais problemas justificam trocar ou complementar a solução atual.
3. Testar um protótipo com dono, atendente e consumidores.
4. Revisar o escopo, registrar a escolha da stack e só então iniciar a implementação.

As etapas e critérios completos estão no [roadmap](docs/roadmap.md). As quantidades são metas internas iniciais, não resultados já obtidos.

## Como colaborar

- Registrar demandas como issues com problema, resultado esperado e critério de aceite.
- Trabalhar em branches como `docs/descricao`, `feat/descricao` e `fix/descricao` e revisar por pull request.
- Atualizar requisitos e decisões quando houver mudança de escopo.
- Colocar referências com URL, data de consulta e observação em `design/referencias/`; protótipos e instruções de teste em `design/prototipos/`.
- Reservar `src/` para a aplicação e `tests/` para testes das regras e dos fluxos críticos, quando o desenvolvimento começar.
- Usar dados fictícios nos exemplos. Não publicar credenciais, contatos de clientes, pedidos reais, contratos ou relatórios privados.

## Configuração futura

O arquivo [.env.example](.env.example) contém apenas nomes de configuração propostos e valores locais fictícios. Ele ainda não é lido por uma aplicação. Quando a stack for definida, adaptar esse contrato e documentar instalação e execução. Credenciais reais devem ficar fora do Git.

## Fontes e bases

- [Pesquisa de concorrentes e fontes primárias](docs/analise-de-concorrentes.md), consultadas em 24/11/2026.
- Levantamento inicial da equipe, **Saas concorrentes.docx**, usado como ponto de partida e confrontado com as páginas públicas. O arquivo original não foi publicado neste repositório.
- Os demais documentos distinguem referências externas, hipóteses comerciais e decisões internas propostas.
