# Fontes, premissas e decisões a confirmar

## Fontes primárias consultadas para o planejamento

Consulta em 13/11/2026 (America/Manaus). Versões e documentação devem ser conferidas novamente ao instalar dependências. Estas fontes descrevem capacidades gerais; não certificam compatibilidade do gateway corporativo nem dos arquivos do usuário.

- [A2A 1.0.0 — especificação](https://a2a-protocol.org/v1.0.0/specification/): mensagens, tasks, artifacts, atualizações e operações. O gateway expõe somente seu subconjunto confirmado.
- [A2A — ciclo de vida](https://a2a-protocol.org/latest/topics/life-of-a-task/): continuidade e estados de tarefas; conferir nomes no contrato 1.0 utilizado.
- [Docling — formatos](https://docling-project.github.io/docling/usage/supported_formats/): extração e conversão de formatos documentais e Office.
- [Docling — OCR](https://docling-project.github.io/docling/concepts/OCR/): OCR e limitações de texto extraído.
- [pgvector](https://github.com/pgvector/pgvector): busca vetorial e combinação com full-text do PostgreSQL.
- [PostgreSQL — busca textual](https://www.postgresql.org/docs/current/textsearch-controls.html): normalização, consulta e ranking lexical.
- [Sai Learn](https://platform.simular.ai/documentation/api-reference/learn): referência de produto para converter execuções em código parametrizado, em preview. Não foi escolhido como dependência obrigatória.

## Confirmado pelo usuário

Plataforma completa, reaproveitamento do chat A2A, trabalho pesado por código, arquivos grandes, processamento sequencial com entregas parciais, HTML editável, sistemas PLM/GMQIS/GMES com uma seleção por solicitação, web/desktop, exportação de automações, contas, memória, biblioteca, prompts e guias.

## Ainda não confirmado

Código e stack reais; infraestrutura/hosting; SSO; quotas; capacidade simultânea; contratos exatos do gateway; permissões e URLs dos sistemas; SO/ambiente dos executores; provedor autorizado de embeddings/visão; política de compartilhamento e retenção; datasets de homologação; editor visual e formatos de export adicionais.

## Alternativas que não são decisões

Hermes, Agent S/Sai e outras bases de automação podem ser avaliadas por licença, operação corporativa, controle de ferramentas, integração, portabilidade e manutenção. Nenhum fork ou serviço externo foi selecionado. Uma avaliação deve usar a mesma tarefa, ambiente e critérios de sucesso e registrar falhas observadas.

Não migrar para Vercel ou qualquer provedor público só porque uma ferramenta de planejamento sugere esse padrão. A rede e os dados corporativos e a aplicação existente orientam a decisão.
