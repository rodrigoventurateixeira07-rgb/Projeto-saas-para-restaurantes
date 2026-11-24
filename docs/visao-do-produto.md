# Visão do produto

Atualização: 24/11/2026. Status: proposta para validação; sem implementação ou clientes confirmados.

## Público e problema

O recorte inicial são hamburguerias e lanchonetes pequenas, com dono presente na operação e pedidos por WhatsApp, retirada e entrega local. A equipe deve confirmar em campo se há retrabalho para explicar opções, calcular totais e organizar o preparo.

| Pessoa | Necessidade a investigar | Resultado esperado |
| --- | --- | --- |
| Dono ou gerente | Configurar o cardápio e acompanhar a operação | Atualizar produto sem depender do desenvolvedor |
| Atendente | Conferir e organizar pedidos | Receber itens e adicionais de forma estruturada |
| Consumidor | Saber opções, preço final e andamento | Pedir pelo celular com poucos obstáculos |

Não assumir que todo restaurante precisa trocar de sistema. Perguntar também por que a ferramenta atual funciona e quais dificuldades impediriam uma mudança.

## Proposta de valor a testar

Permitir que uma hamburgueria publique seu cardápio e acompanhe pedidos em uma interface simples, com implantação acompanhada e cobrança compreensível.

Essa frase é uma hipótese comercial. A pesquisa encontrou personalização, pedidos digitais e gestão em concorrentes; portanto, esses itens são requisitos básicos para competir, não exclusividades. Ver [análise de concorrentes](analise-de-concorrentes.md).

## MVP proposto

1. A equipe configura restaurante, horários, bairros atendidos e taxa por bairro.
2. O cliente abre um link público, escolhe itens e adicionais e visualiza o total.
3. Informa apenas os dados necessários para retirada ou entrega e envia o pedido.
4. O servidor grava o pedido; a tela avisa que ele aguarda aceite do restaurante.
5. O atendente aceita ou cancela, acompanha o preparo e conclui o atendimento.
6. O dono consulta histórico e resumo dos pedidos concluídos.

O pagamento é combinado com o estabelecimento e realizado fora da plataforma. Registrar a forma escolhida não comprova pagamento. O MVP não emite documento fiscal nem substitui o caixa ou o sistema fiscal existente.

## Fora do MVP

- Aplicativos nativos, marketplace próprio e operação offline.
- Estoque de ingredientes, ficha técnica, compras e contabilidade.
- Emissão fiscal, conciliação bancária e cobrança online do consumidor.
- Integração iFood, chatbot, disparos de marketing e roteirização.
- Franquias, múltiplas unidades por conta e programa de fidelidade.

## Hipóteses e experimentos

| Hipótese | Experimento | Sinal inicial para prosseguir |
| --- | --- | --- |
| O retrabalho com pedidos é relevante | Entrevistar 3–5 estabelecimentos e observar um turno autorizado | Problema recorrente com exemplos concretos |
| O fluxo é compreensível | Teste de protótipo com 5 consumidores e 2 pessoas da operação | Pelo menos 4 consumidores concluem sem ajuda; operação encontra e atualiza pedido |
| Há disposição para pagar | Apresentar proposta com valor, limites e suporte explícitos | Um estabelecimento aceita negociar piloto pago após teste |
| A operação cabe na rotina da equipe | Medir horas de suporte durante o piloto | Custo e disponibilidade compatíveis com o preço negociado |

Essas amostras ajudam a tomar decisões iniciais; não demonstram demanda de todo o mercado. Documentar falhas e razões de desistência, não só opiniões favoráveis.

## Métricas do piloto

- Pedidos iniciados, enviados, aceitos, cancelados e concluídos, com definições estáveis.
- Tempo entre envio e aceite; tempo entre aceite e conclusão.
- Erros de itens/adicionais e intervenções manuais por pedido.
- Minutos de suporte por restaurante por semana.
- Receita contratada menos custos diretos e tempo de atendimento.

Coletar métricas agregadas e necessárias, sem copiar conversas privadas ou registrar dados pessoais em ferramentas de analytics.

## Fontes e bases

Consulta das fontes externas: 24/11/2026. As metas e a proposta acima são decisões internas sugeridas.

- [Goomer — planos](https://goomer.com.br/planos): referência de recursos já oferecidos no segmento.
- [InstaDelivery — termos](https://tools.instadelivery.com.br/termos-de-servico): referência de cardápio e operação de pedidos.
- [Análise comparativa do projeto](analise-de-concorrentes.md): evidências e limitações da pesquisa.
