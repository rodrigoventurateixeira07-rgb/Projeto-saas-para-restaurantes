# Segurança e LGPD

Atualização: 24/11/2026. Status: plano inicial de controles e pendências para o piloto. Documentação não comprova implementação, conformidade nem ausência de risco. As definições jurídicas e contratuais precisam refletir a operação real antes de receber dados de consumidores.

## Papéis e finalidade

Como hipótese de desenho, o restaurante determina finalidades dos dados do pedido e o SaaS atua como operador sob suas instruções. A plataforma pode ser controladora em atividades próprias, como cadastro e cobrança de seus clientes. A classificação depende da atividade efetiva, não apenas do nome escrito no contrato. LGPD: arts. 5º, 6º, 7º, 18, 37 e 46–48 [L1].

Registrar finalidade, base legal, acesso, compartilhamento e retenção por atividade. Consentimento não deve ser usado como justificativa genérica para tudo; pedido e marketing precisam de análise separada. Marketing não integra o MVP.

## Inventário proposto de dados

| Grupo | Dados mínimos pretendidos | Finalidade | Acesso proposto | Retenção |
| --- | --- | --- | --- | --- |
| Equipe da loja | Nome, e-mail, vínculo, função e credencial protegida | Autenticar e autorizar operação | Próprio usuário, gerente e suporte autorizado conforme necessidade | Definir ciclo de conta e obrigação aplicável |
| Consumidor | Nome de contato e telefone | Identificar e contatar sobre o pedido | Equipe da respectiva loja; suporte excepcional auditado | Definir prazo operacional e obrigações antes do piloto |
| Entrega | Endereço, bairro e complemento necessário | Entregar o pedido | Apenas quem participa da operação | Eliminar/anonimizar após finalidade e retenções aplicáveis |
| Pedido | Itens, totais, modalidade, horários e estado | Atender e gerar histórico operacional | Loja correspondente | Definir preservação do histórico e desvinculação dos dados pessoais |
| Logs e auditoria | ID técnico, ator, loja, evento e horário | Investigar falhas e acessos | Equipe técnica autorizada | Prazo mínimo necessário, registrado em política |

Não coletar CPF, data de nascimento, documento, cartão ou endereço de quem retira no balcão sem necessidade específica. Não criar campos para alergias ou informações de saúde no MVP; orientar a não inserir dados sensíveis em texto livre. A necessidade futura exige análise própria.

**Pendência de liberação:** a política precisa ter prazos concretos por categoria, responsável e mecanismo de descarte. Definir também expiração do link de acompanhamento e ciclo dos backups; este documento não fixa um prazo legal único para todos os dados.

## Controles técnicos propostos

- Isolar restaurantes e aplicar autorização em cada rota, consulta, exportação e acesso administrativo.
- Usar mecanismo consolidado de autenticação, hash de senha adequado, recuperação com token expirável e limitação de tentativas. Não desenvolver criptografia própria.
- Proteger sessões em produção com cookies `Secure`, `HttpOnly` e política `SameSite` adequada; ativar proteção CSRF nos fluxos pertinentes.
- Validar no servidor preços, quantidades, adicionais, formato e tamanho das entradas; usar consultas parametrizadas e escape de saída.
- Validar imagem por tipo real, dimensão e tamanho; reprocessar e remover metadados quando possível. Não aceitar HTML/SVG ativo como imagem de catálogo no MVP.
- Exigir HTTPS, restringir banco e arquivos privados e aplicar permissões mínimas nos provedores.
- Manter segredos fora do Git, separados por ambiente. Em caso de exposição, revogar/rotacionar; apagar o arquivo do último commit não basta.
- Evitar telefone, endereço, corpo de pedido, cookies e tokens nos logs, monitoramento, analytics e URLs de terceiros.
- Proteger o acompanhamento com token de alta entropia, hash armazenado, expiração, limitação de acesso e política de referência que evite vazamento do token.
- Exportar somente colunas necessárias e neutralizar injeção de fórmulas em CSV/planilha.
- Manter cópias protegidas, testar restauração e registrar atualização/correção de dependências.

São propostas de implementação para este projeto, orientadas pelas referências [S1], [S2] e [S3]; não são controles já existentes. O framework pode oferecer mecanismos úteis, mas sua configuração e o código da aplicação continuam precisando de revisão.

## Preparação administrativa

Antes do piloto, definir responsável e canal de privacidade; inventário de operações; termos e aviso compreensíveis; regras de acesso de suporte; fornecedores e suboperadores; procedimentos de exportação, correção, exclusão e encerramento. Avaliar localização dos dados e eventual transferência internacional conforme fornecedores efetivamente escolhidos.

Solicitações de titulares devem ter verificação proporcional de identidade e tratamento das retenções aplicáveis. Registrar atendimento sem exigir cópia de documento por padrão. Exclusão na base ativa deve considerar backups e evitar reintrodução de dados descartados após restauração.

## Resposta a incidente

1. Registrar conhecimento, horário, sistemas envolvidos e responsável; preservar evidências com acesso restrito.
2. Conter a falha, bloquear acesso indevido e rotacionar credenciais quando necessário.
3. Identificar lojas, titulares e categorias afetadas; avisar o controlador sem demora injustificada e fornecer informações para avaliação [I1].
4. Avaliar risco e comunicações devidas. A Resolução CD/ANPD nº 15/2024 prevê, em regra, **três dias úteis** para comunicação pelo controlador à ANPD e aos titulares nos casos exigidos; há regras específicas e contagem em dobro para agentes de pequeno porte efetivamente enquadrados [I2]. Não assumir enquadramento automático.
5. Corrigir, recuperar, acompanhar efeitos e manter registro do incidente. O regulamento prevê retenção do registro por ao menos cinco anos, inclusive incidentes não comunicados [I2].

O prazo legal de comunicação não é prazo para começar a agir. Definir contatos e responsabilidades em contrato e ensaiar o procedimento antes do piloto.

## Evidências para liberar o piloto

- [ ] Testes de acesso entre duas lojas e funções diferentes aprovados.
- [ ] Logs revisados sem credenciais ou dados pessoais desnecessários.
- [ ] Segredos e MFA dos provedores configurados; acesso de suporte rastreável.
- [ ] Backup restaurado em ambiente isolado.
- [ ] Inventário, prazos de retenção e descarte definidos e executáveis.
- [ ] Avisos, contrato, papéis, fornecedores e canal de privacidade revisados.
- [ ] Procedimentos de incidente e solicitação de titular testados.

## Fontes

Consultadas em **24/11/2026**. As referências fundamentam o plano; não substituem a avaliação do caso concreto.

- L1 — [Lei nº 13.709/2018 — LGPD, texto no Planalto](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm).
- S1 — [ANPD — Guia de segurança para agentes de pequeno porte](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-sobre-seguranca-da-informacao-para-agentes-de-tratamento-de-pequeno-porte).
- S2 — [ANPD — Checklist de medidas de segurança](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/checklist-vf.pdf/@@display-file/file).
- S3 — [OWASP — Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/).
- I1 — [ANPD — Comunicação de incidente de segurança](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis).
- I2 — [Resolução CD/ANPD nº 15/2024 — publicação no DOU, cópia na Biblioteca Digital do Ministério da Justiça](https://bibliotecadigital.mj.gov.br/bitstream/1/12879/1/RES_ANPD_2024_15.pdf).

[L1]: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm
[S1]: https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-sobre-seguranca-da-informacao-para-agentes-de-tratamento-de-pequeno-porte
[S2]: https://www.gov.br/anpd/pt-br/centrais-de-conteudo/checklist-vf.pdf/@@display-file/file
[S3]: https://owasp.org/www-project-application-security-verification-standard/
[I1]: https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis
[I2]: https://bibliotecadigital.mj.gov.br/bitstream/1/12879/1/RES_ANPD_2024_15.pdf
