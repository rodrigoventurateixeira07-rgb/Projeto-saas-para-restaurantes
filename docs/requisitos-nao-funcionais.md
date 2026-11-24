# Requisitos não funcionais

Atualização: 24/11/2026. Status: metas propostas para o piloto, **ainda não medidas nem atendidas**. Os números são parâmetros internos iniciais, não promessa contratual.

## Metas e verificação

| ID | Área | Meta inicial proposta | Como verificar antes do piloto |
| --- | --- | --- | --- |
| RNF-01 | Isolamento | Nenhuma leitura ou alteração indevida entre restaurantes | Testes de integração de listagem, detalhe, escrita, arquivos, buscas e exportações com duas lojas |
| RNF-02 | Autenticação | Sessões protegidas, recuperação segura e limitação de tentativas | Testar expiração, logout, cookies de produção e abuso de login/recuperação |
| RNF-03 | Integridade | Não haver pedidos parciais ou duplicados na mesma tentativa | Simular rollback, duplo clique, retry e concorrência de status |
| RNF-04 | Desempenho | p95 das consultas principais abaixo de 800 ms e criação abaixo de 1,5 s, sem serviços externos | Carga de 20 usuários simultâneos durante 10 min, 3 lojas, 100 produtos/loja e 10 mil pedidos no total; registrar hardware e erros |
| RNF-05 | Experiência móvel | Cardápio utilizável entre 360 e 1440 px; conteúdo principal em até 3 s no cenário definido | Medir 5 cargas frias em aparelho intermediário ou simulação registrada de 4G; relatar mediana, LCP e peso das imagens |
| RNF-06 | Acessibilidade | Adotar WCAG 2.2 AA como referência de projeto | Verificar teclado, foco, rótulos, erros, contraste e leitor de tela; documentar pendências antes de alegar conformidade |
| RNF-07 | Disponibilidade | Objetivo interno inicial de 99,5% por mês após entrada em operação | Monitor externo a cada minuto; calcular tempo indisponível/tempo total e registrar manutenção; não vender como SLA antes de medir |
| RNF-08 | Recuperação | Proposta: RPO de 24 h e RTO de 4 h | Backup diário protegido e restauração ensaiada em ambiente isolado; medir perda máxima e tempo real |
| RNF-09 | Observabilidade | Identificar falhas sem expor dados do consumidor | Logs com request ID, loja, tipo de evento e erro sanitizado; testar ausência de senhas, tokens, telefones e endereços |
| RNF-10 | Manutenção | Regras críticas verificadas em toda mudança relevante | Automatizar testes de autorização, total, estados e idempotência; revisar migrations e configuração |
| RNF-11 | Privacidade | Coleta e retenção limitadas à finalidade definida | Revisar inventário, aviso, solicitações de titulares, fornecedores e descarte em produção e backup |
| RNF-12 | Custo | Medir custo mensal e por restaurante antes de fixar preço | Registrar infraestrutura, armazenamento, e-mail, suporte e serviços variáveis; equipe define teto antes de contratar |
| RNF-13 | Ambientes | Desenvolvimento, homologação e produção com dados/segredos separados | Conferir contas, banco, permissões, debug desativado em produção e dados fictícios nos testes |
| RNF-14 | Segurança de entrega | Nenhuma vulnerabilidade crítica conhecida sem tratamento antes do piloto | Revisão de dependências e código, teste dos controles e registro de correção/mitigação; findings altos exigem análise explícita |

**p95**: 95% das medições ficam abaixo desse valor. **RPO**: perda de dados máxima tolerada. **RTO**: tempo desejado para recuperar o serviço. Se perder até um dia de pedidos for inaceitável para o piloto, contratar recuperação mais frequente e rever custo antes de operar.

## Condições de liberação

- Os testes de isolamento, autorização, preços, gravação e reenvio precisam passar.
- Backup precisa ter sido restaurado de verdade; apenas existir no painel do provedor não basta.
- O restaurante precisa conhecer os limites de disponibilidade, suporte e recuperação e ter contingência combinada.
- Falhas e metas não atingidas devem ficar registradas, com responsável e prazo. Não marcar um requisito como concluído sem evidência.

## Fontes e bases

Consultadas em 24/11/2026. Os limites numéricos desta página são escolhas internas para validação.

- [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/): referência de verificação de segurança.
- [W3C — WCAG 2.2](https://www.w3.org/TR/WCAG22/): referência de acessibilidade.
- [ANPD — guia de segurança para agentes de pequeno porte](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-sobre-seguranca-da-informacao-para-agentes-de-tratamento-de-pequeno-porte): referência para preparação dos controles.
- [Requisitos funcionais](requisitos-funcionais.md) e [riscos](riscos-do-projeto.md): contexto das prioridades.
