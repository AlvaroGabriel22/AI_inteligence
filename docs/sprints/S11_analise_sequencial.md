# S11 — Análise sequencial e entregas por arquivo

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S04](S04_adaptador_a2a.md), [S05](S05_jobs_filas_eventos.md), [S07](S07_extracao_formatos.md), [S08](S08_ocr_qualidade.md), [S09](S09_dados_calculos.md), [S10](S10_rag_busca_hibrida.md)
- Requisitos: R05, R07, R08, R10, R11, R22 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PIPELINE_DOCUMENTOS.md](PIPELINE_DOCUMENTOS.md), [CONTRATO_A2A.md](CONTRATO_A2A.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Entregar a jornada central de arquivos grandes em fila, com respostas úteis por arquivo e consolidação posterior.

## Inspecionar antes de editar

PIPELINE_DOCUMENTOS.md, contratos de jobs/eventos, limites A2A comprovados e serviços tabulares/RAG.

## Trabalho de implementação

1. Implementar roteador por intenção: pergunta localizada, análise integral, tradução, comparação e preparação de artefato.
2. Construir lotes/payloads com limite de bytes e contexto, reservando resposta e instruções; aplicar budgets por etapa e job.
3. Processar o arquivo atual, validar a resposta e publicar entrega persistida antes de iniciar análise do seguinte.
4. Controlar cobertura de páginas/trechos para tarefas integrais; consolidar preservando fontes e evitando perda de unidades.
5. Tratar comparações que dependem dos próximos arquivos: publicar somente achados válidos no escopo atual e marcar dependências pendentes.
6. Permitir cancelamento, perguntas, erros por arquivo e reprocessamento seletivo, com mapa de tarefas/contextos A2A.

## Entregáveis

Fluxo completo de lote com outputs por arquivo, consolidação, orçamento e retomada.

## Critérios de aceite

- [ ] Três arquivos grandes geram eventos e entregas na ordem exigida, comprovada por teste.
- [ ] Nenhuma chamada excede o limite efetivo de arquivos/bytes/contexto configurado.
- [ ] Tradução integral cobre todas as unidades legíveis ou informa exatamente as faltantes.
- [ ] Resultado parcial é identificado e não é apresentado como conclusão definitiva do conjunto.
- [ ] Falha no segundo arquivo não apaga a análise do primeiro e retomada não a duplica.

## Verificação obrigatória

E2E de lote A/B/C, tradução longa, payload de fronteira, gateway lento/429, reinício de worker e comparação com dependência entre arquivos.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Chamar a API simultaneamente para todos os arquivos do mesmo lote ou esconder partes não processadas.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S11 de docs/sprints/S11_analise_sequencial.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Esta sprint só termina com a jornada observável de upload até entregas parciais e consolidação; separar homologação real de simulação.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S11.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
