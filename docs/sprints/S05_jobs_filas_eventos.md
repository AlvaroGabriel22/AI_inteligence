# S05 — Jobs duráveis, fila e eventos de progresso

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S01](S01_fundacao_dominio.md), [S02](S02_autenticacao_permissoes.md), [S04](S04_adaptador_a2a.md)
- Requisitos: R07, R10, R11, R23 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [CONTRATOS_INTERNOS.md](CONTRATOS_INTERNOS.md), [CONTRATO_A2A.md](CONTRATO_A2A.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Desacoplar trabalhos longos das requisições HTTP e preservar progresso, sequência e entregas durante falhas.

## Inspecionar antes de editar

Fila escolhida em ADR, armazenamento de jobs e eventos, adaptador A2A e requisitos de concorrência do gateway.

## Trabalho de implementação

1. Implementar job/step com transições persistentes, tentativas, leases ou mecanismo equivalente e reconciliação de workers interrompidos.
2. Criar regra de ordem por lote e limites de concorrência global, por usuário e provedor; definir justiça da fila e backpressure.
3. Persistir resultado antes de publicar partial_result_ready; usar outbox ou mecanismo equivalente para consistência entre commit e evento.
4. Entregar snapshot/eventos ao chat por transporte adequado; suportar reconnect com cursor estável e deduplicação.
5. Separar deadline HTTP, de etapa, remoto e do job; aplicar retries limitados e classificados, sem repetir efeitos cegamente.
6. Implementar cancelamento solicitado/confirmado, pause para entrada/autenticação e retomada; mapear IDs locais e A2A.

## Entregáveis

Coordenador durável, workers, regras de agendamento, eventos e monitoramento básico de jobs.

## Critérios de aceite

- [ ] Reiniciar worker ou fechar navegador não perde resultado já confirmado.
- [ ] Arquivo B de um lote não entra em análise antes da publicação persistida do resultado útil de A.
- [ ] Vários usuários respeitam o limite global de chamadas ao gateway.
- [ ] Eventos repetidos/reconectados não duplicam respostas e cancelamento não é falsamente confirmado.

## Verificação obrigatória

Injetar falha antes/depois de commit e publicação, duplicar entrega de fila, reiniciar worker e reconectar navegador; medir chamadas em paralelo.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Prometer exatamente-uma-vez só por utilizar fila; deixar estado apenas em memória ou conexão SSE.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S05 de docs/sprints/S05_jobs_filas_eventos.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Demonstre a ordem dos eventos e a retomada por teste de falha. Job, conexão HTTP e tarefa A2A são unidades diferentes.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S05.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
