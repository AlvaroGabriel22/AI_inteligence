# S07 — Extração estruturada de formatos

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S05](S05_jobs_filas_eventos.md), [S06](S06_biblioteca_upload.md)
- Requisitos: R06, R08, R09 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PIPELINE_DOCUMENTOS.md](PIPELINE_DOCUMENTOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Transformar documentos em conteúdo estruturado rastreável, usando processamento por código.

## Inspecionar antes de editar

PIPELINE_DOCUMENTOS.md, corpus de testes e leitores existentes; verificar licenças e dependências autorizadas.

## Trabalho de implementação

1. Implementar roteamento por assinatura/formato para PDF textual, DOCX, XLSX, CSV, PPTX, Markdown e TXT.
2. Adicionar conversão isolada de PPT legado com ferramenta validada; documentar requisitos do runtime.
3. Preservar títulos, tabelas, slides, abas/células e referências à versão original; registrar cobertura e elementos não interpretados.
4. Tratar encodings, zeros à esquerda, células mescladas, separadores e tipos; separar valores de fórmulas e cache de resultados.
5. Aplicar limites de memória/tempo/expansão e processamento incremental quando pertinente; marcar páginas para OCR sem executar OCR em tudo.
6. Versionar derivados e permitir reprocessamento sem sobrescrever original ou invalidar citações antigas silenciosamente.

## Entregáveis

Leitores/adaptadores, modelo de unidade extraída, mapa de cobertura e fixtures multiformato.

## Critérios de aceite

- [ ] Todos os formatos deste escopo têm fixture verificada ou limitação explicitamente bloqueadora.
- [ ] Texto e tabelas possuem ponteiro estável para origem; códigos e unidades são preservados.
- [ ] Extração vazia ou parcial não aparece como análise concluída.
- [ ] Falha em um arquivo mantém resultados de outros jobs e expõe motivo acionável.

## Verificação obrigatória

Comparar extração com corpus de resultado conhecido; testar PPT legado realista, CSV com encoding e XLSX com fórmulas não calculadas.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Interpretar números com o LLM durante extração; considerar OCR equivalente a compreender imagens.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S07 de docs/sprints/S07_extracao_formatos.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Use bibliotecas do formato e teste cobertura. Não implemente um parser caseiro geral para todos os documentos.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S07.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
