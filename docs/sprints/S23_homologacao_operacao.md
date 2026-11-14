# S23 — Homologação final, desempenho e operação

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S21](S21_prompts_guias_central.md), [S22](S22_integracoes_corporativas.md)
- Requisitos: R01, R02, R05, R07, R10, R11, R14, R15, R20, R23 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PLANO_DE_TESTES.md](PLANO_DE_TESTES.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Verificar o produto completo, dimensionar limites e preparar operação recuperável no ambiente autorizado.

## Inspecionar antes de editar

PLANO_DE_TESTES.md, requisitos, evidências S00–S22, quotas reais, runbooks e infraestrutura de destino.

## Trabalho de implementação

1. Executar regressão das jornadas de anexos grandes, lote sequencial, tradução completa, análise tabular, edição/export HTML e automação importada.
2. Medir carga e recursos com concorrência-alvo confirmada; ajustar quotas, budgets, índices, cache e workers com evidência.
3. Auditar isolamento de usuários, conexões, cache, memória, arquivos compartilhados e preview; verificar saneamento de logs e efeitos de exclusão.
4. Testar restauração de backup com banco, arquivos, índices reconstruíveis e jobs; documentar RPO/RTO observados e rotina operacional.
5. Instrumentar métricas e alertas de fila, erro A2A, tokens/chamadas, storage, OCR, falha de executor e tempo até primeira entrega útil.
6. Preparar migração, rollback, atualização de dependências e runbook; consolidar pendências e obter liberação de produção conforme autorização aplicável.

## Entregáveis

Relatório final de cobertura, desempenho, segurança operacional, backup/restauração, runbooks e pacote de release.

## Critérios de aceite

- [ ] Todos os requisitos têm implementação/evidência ou pendência explicitamente aceita; nenhuma lacuna é escondida por status geral.
- [ ] Carga-alvo respeita recursos e limites do gateway com métricas reproduzíveis.
- [ ] Recuperação após falha e restauração de backup foram exercitadas, não apenas documentadas.
- [ ] Primeira entrega útil, conclusão, erros e custos de chamada podem ser acompanhados.
- [ ] Produção só é declarada pronta com gates externos necessários realmente homologados.

## Verificação obrigatória

Regressão integrada, carga sintética controlada, interrupções de worker/gateway/runner, restauração em ambiente limpo e smoke test no destino autorizado.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Publicar ou migrar produção sem autorização pertinente; inventar SLOs e números de testes aprovados.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S23 de docs/sprints/S23_homologacao_operacao.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Entregue relatório de prontidão com evidências e limitações. Se houver pendências, separe o que está pronto do que ainda depende de homologação.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S23.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
