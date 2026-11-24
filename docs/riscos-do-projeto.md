# Riscos do projeto

Atualização: 24/11/2026. Avaliação qualitativa inicial, sem histórico de produção. Probabilidade e impacto são estimativas da equipe a revisar. Responsáveis abaixo são **papéis sugeridos**, ainda sem atribuição nominal.

## Registro inicial

| ID | Risco | Probabilidade / impacto | Sinal de alerta | Redução e contingência | Responsável proposto |
| --- | --- | --- | --- | --- | --- |
| R-01 | Construir algo sem demanda suficiente | Alta / Alto | Entrevistados elogiam a ideia, mas não aceitam testar ou pagar | Validar dor concreta e proposta antes do desenvolvimento amplo; rever recorte | Produto |
| R-02 | Crescer o escopo para copiar sistemas completos | Alta / Alto | Piloto passa a exigir fiscal, estoque e IA simultaneamente | Manter limites do MVP; estimar cada expansão e recusar prazo sem capacidade | Produto e técnica |
| R-03 | Expor dados de uma loja a outra | Média / Crítico | Rotas aceitam IDs sem verificar vínculo | Escopo centralizado, testes com duas lojas e revisão de exportações/arquivos; conter acesso e iniciar resposta a incidente | Técnica |
| R-04 | Comprometer conta ou credencial | Média / Alto | Senha compartilhada, segredo no Git ou sessão indevida | Contas individuais, MFA nos provedores, recuperação segura e revisão de segredos; revogar e rotacionar se expostos | Técnica |
| R-05 | Perder ou duplicar pedido | Média / Alto | Timeout gera reenvio e dois registros; itens incompletos | Transações, idempotência e testes de concorrência; conciliar com a loja antes de repetir preparo | Técnica e operação |
| R-06 | Ficar indisponível no horário de pico | Média / Alto | Erros, lentidão e falha de conexão | Monitoramento e carga testada; contato alternativo e procedimento para conferir pedidos pendentes | Operação |
| R-07 | Não recuperar dados após falha | Média / Alto | Backup existe, mas nunca foi restaurado | Ensaio real de restauração e revisão de RPO/RTO; informar limites ao piloto | Técnica |
| R-08 | Tratar dados sem organização ou prazo de descarte | Média / Alto | Coleta cresce sem finalidade, fornecedor ou retenção definidos | Inventário, revisão de papéis, avisos e políticas; suspender coleta desnecessária | Produto e privacidade |
| R-09 | Suporte custar mais que a receita | Alta / Alto | Implantação longa e chamados constantes | Medir horas, reduzir atritos, delimitar suporte e revisar preço antes de ampliar | Negócio |
| R-10 | Depender de APIs ou preços de terceiros | Média / Médio | Oferta muda, integração bloqueia ou custo cresce | Confirmar termos, manter dados exportáveis e alternativa operacional; adiar integrações dispensáveis | Técnica e negócio |
| R-11 | Faltar tempo ou conhecimento na equipe | Alta / Alto | Entregas acumuladas e ausência de revisão | Dividir responsabilidades e construir fatias pequenas; documentar operação e limitar número de pilotos | Equipe |
| R-12 | Confundir pedido recebido com aceito ou pago | Média / Alto | Consumidor espera preparo ou loja considera pagamento concluído | Mensagens e estados distintos; pagamento externo explícito; testar entendimento com usuários | Produto |
| R-13 | Expor arquivos privados no repositório público | Média / Alto | Prints de pedidos, planilhas reais ou `.env` em commit | Dados fictícios, revisão de diff e regras de exclusão; remover exposição e rotacionar segredos quando necessário | Equipe |
| R-14 | Usar preço de concorrente desatualizado como referência | Alta / Médio | Páginas exibem campanhas ou valores contraditórios | Registrar data e condições, pedir cotação e recalcular custo total | Negócio |

## Rotina de revisão

- Revisar ao fim de cada etapa do roadmap e após incidente ou mudança relevante.
- Atribuir responsáveis nominais antes do piloto e transformar ações em issues com critério de conclusão.
- Registrar evidência da redução do risco; um documento ou checkbox não é evidência suficiente de um controle técnico.
- Bloquear piloto com falha de isolamento ou autorização conhecida, restauração inviável ou fluxo que possa perder pedidos sem detecção.
- Se demanda, capacidade ou contribuição não se sustentarem, ajustar o recorte ou interromper expansão antes de assumir mais clientes.

## Fontes e bases

Consulta externa: 24/11/2026. Classificações e ações são avaliação própria do projeto, não estatísticas externas.

- [Análise de concorrentes](analise-de-concorrentes.md): concorrência e divergências comerciais observadas.
- [ANPD — guia de segurança para agentes de pequeno porte](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-sobre-seguranca-da-informacao-para-agentes-de-tratamento-de-pequeno-porte): referência para planejar controles.
- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/): referência para verificação de segurança.
- [Segurança e LGPD](seguranca-e-lgpd.md), [metas de qualidade](requisitos-nao-funcionais.md) e [modelo de negócio](modelo-de-negocio.md): ações e pendências relacionadas.
