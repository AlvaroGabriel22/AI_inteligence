# S16 — Catálogo de sistemas e seletor no chat

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S02](S02_autenticacao_permissoes.md), [S05](S05_jobs_filas_eventos.md), [S12](S12_contexto_memoria.md), [S13](S13_chat_resultados_ricos.md)
- Requisitos: R16, R17, R18, R24 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Representar fontes internas e capacidades autorizadas, com uma seleção de sistema por solicitação.

## Inspecionar antes de editar

Política de acesso, sistemas conhecidos, URLs/documentação fornecidas e contratos de execução.

## Trabalho de implementação

1. Criar registro de sistema, ambiente, conexão e capacidades com descrição, parâmetros, saídas e pré-condições.
2. Adicionar opções PLM, GMQIS e GMES no compositor; fontes não configuradas exibem estado honesto e não respondem com dados simulados.
3. Validar no backend no máximo um sistema por solicitação e persistir a escolha no job, mesmo se o usuário mudar a seleção para a próxima mensagem.
4. Resolver intenção contra capacidades disponíveis; fazer perguntas somente sobre parâmetros indispensáveis ausentes.
5. Armazenar referências de conexão/segredo com escopo; preparar interfaces de executor web/desktop e entrada de dados coletados no pipeline.
6. Registrar origem, filtros, momento da coleta e política de atualização; distinguir dados atuais de cache autorizado.

## Entregáveis

Catálogo de fontes, seletor no chat, schemas de capacidades e conexão com o coordenador.

## Critérios de aceite

- [ ] Solicitação com duas fontes é rejeitada de forma clara no backend.
- [ ] Trocar a fonte no compositor não altera a fonte de um job já criado.
- [ ] Sistema sem executor/configuração não aparece como integrado ou disponível para consulta real.
- [ ] Parâmetros conhecidos são reutilizados; faltantes geram pergunta contextual sem pedir novamente dados já válidos.

## Verificação obrigatória

Testar fonte não configurada, usuário sem permissão, alteração durante job, parâmetros incompletos e snapshot/cache.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Inventar URLs/seletores ou pressupor que citar PLM concede acesso ao sistema.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S16 de docs/sprints/S16_catalogo_sistemas.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Modele o contrato e a experiência de seleção; não alegue integração real antes da execução comprovada.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S16.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
