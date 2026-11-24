# Modelo de negócio

Atualização: 24/11/2026. Status: hipóteses de negócio. Não há preço, receita, cliente ou margem confirmados.

## Cliente e oferta inicial

Atender inicialmente um pequeno restaurante com operação local, oferecendo configuração acompanhada do cardápio, treinamento curto e organização de pedidos. O primeiro piloto serve para aprender quais tarefas justificam uma assinatura.

O produto não precisa substituir todos os sistemas do estabelecimento. É necessário validar se o uso de mais um painel resolve uma dor ou aumenta o trabalho.

## Receita proposta

- Assinatura mensal por estabelecimento, com limites e suporte descritos de forma objetiva.
- Possível taxa de implantação quando houver cadastro e treinamento que consumam horas relevantes, informada antes da contratação.
- Serviços extras somente após demanda comprovada e orçamento separado.

**Sem preço definido.** Entrada gratuita e cobrança por faixas já aparecem na pesquisa de concorrentes. Não escolher um valor apenas para ficar abaixo deles; primeiro estimar custo, atendimento e disposição para pagar.

Cobrança da assinatura do restaurante e pagamento de pedidos do consumidor são processos diferentes. No MVP, o consumidor paga fora da plataforma. Uma eventual automação da assinatura também depende de escolha de provedor e regras próprias.

## Custos a levantar

| Grupo | O que incluir | Como medir |
| --- | --- | --- |
| Infraestrutura | Aplicação, banco, domínio, imagens, backup e monitoramento | Cotações com região, franquia, excedente e tributos |
| Serviços variáveis | E-mail transacional, armazenamento, tráfego e futuras APIs | Uso por loja e custo unitário |
| Implantação | Cadastro, configuração e treinamento | Horas por novo cliente |
| Suporte e manutenção | Dúvidas, incidentes, atualizações e correções | Horas semanais e valor atribuído à hora |
| Comercial e administração | Prospecção, meios de cobrança, contabilidade e contratos | Custo efetivo e obrigações da forma de atuação escolhida |

Não há contratação autorizada por este documento. Definir orçamento e limites antes de contratar serviços.

## Simulação interna, não orçamento

Exemplo inteiramente hipotético: mensalidade de **R$ 99**, custo variável de **R$ 15 por loja**, uma hora mensal de suporte por loja avaliada em **R$ 25** e custo fixo de **R$ 150/mês**.

```text
Contribuição por loja = 99 - 15 - 25 = R$ 59/mês
Ponto de equilíbrio simplificado = teto(150 / 59) = 3 lojas
```

Se o suporte dobrar para duas horas, a contribuição cai para R$ 34 e o equilíbrio simplificado passa para cinco lojas. A conta não inclui desenvolvimento inicial, implantação, tributos, inadimplência, aquisição de clientes nem remuneração completa da equipe. Não é previsão de lucro nem recomendação de preço.

## Validação comercial

1. Perguntar o custo total atual, incluindo tempo de operação e dificuldades reais.
2. Apresentar proposta escrita com preço testado, limites, suporte e cancelamento.
3. Negociar um piloto limitado e medir uso, ocorrências e horas de atendimento.
4. Verificar se o estabelecimento continuaria pagando após o acompanhamento inicial.
5. Ampliar só quando a contribuição e a capacidade de suporte forem sustentáveis.

Manter preços negociados, dados financeiros e contatos identificáveis fora do repositório público. Publicar apenas sínteses anonimizadas.

## Questões em aberto

- Qual problema leva o cliente a pagar e quais ferramentas ele manterá?
- Quanto trabalho de implantação e suporte cada loja demanda?
- Qual limite de lojas a equipe consegue atender nos horários de pico?
- Quem será responsável pela contratação, emissão de cobrança e atendimento?
- Como serão tratadas exportação de dados, encerramento e reajuste?

## Fontes e bases

Consulta externa: 24/11/2026. Simulação e hipóteses comerciais são próprias.

- [InstaDelivery — termos](https://tools.instadelivery.com.br/termos-de-servico): exemplo de cobrança relacionada ao faturamento na plataforma, com divergências registradas na análise.
- [Anota AI — preços e planos](https://anota.ai/blog/precos-e-planos/): exemplo de faixas por volume de pedidos.
- [Análise de concorrentes](analise-de-concorrentes.md): tabela completa e condições observadas; não é pesquisa de disposição para pagar.
