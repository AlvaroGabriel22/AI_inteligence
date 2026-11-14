# S04 — Adaptador A2A corporativo

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S01](S01_fundacao_dominio.md), [S02](S02_autenticacao_permissoes.md), [S03](S03_chat_sessoes_layout.md)
- Requisitos: R22, R10, R11 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [CONTRATO_A2A.md](CONTRATO_A2A.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Concentrar a integração existente em um adaptador testado, compatível com o contrato real do gateway.

## Inspecionar antes de editar

CONTRATO_A2A.md, implementação atual, AgentCard e exemplos saneados disponíveis; confirmar métodos e headers sem adivinhar.

## Trabalho de implementação

1. Inventariar o contrato real e preencher matriz de compatibilidade, incluindo versões de SDK/protocolo e métodos expostos.
2. Implementar autenticação proprietária, identidade validada, envelope JSON-RPC e tratamento uniforme de erros HTTP/JSON-RPC.
3. Suportar resposta imediata, tarefa assíncrona, GetTask, continuidade com taskId/contextId e CancelTask conforme o contrato.
4. Adicionar SSE somente quando comprovado, mantendo polling exigido pelo gateway; tratar reconexão sem duplicar submissão.
5. Validar parts/artifacts, tipos e base64; estabelecer medição de payload e limites de timeout/chamadas.
6. Criar simulador determinístico e fixtures saneadas de contrato; executar homologação real quando a rede e os dados necessários estiverem disponíveis.

## Entregáveis

Adaptador isolado, simulador, testes de contrato, matriz de capacidades e documentação de configuração segura.

## Critérios de aceite

- [ ] Pergunta adicional é respondida no mesmo taskId/contextId quando aplicável.
- [ ] Erros JSON-RPC em HTTP 200 são reconhecidos; artefato inválido não é apresentado como sucesso.
- [ ] Timeout não causa reenvio cego de operação já aceita.
- [ ] Compatibilidade simulada e real estão documentadas separadamente.

## Verificação obrigatória

Cobrir todos os cenários de falha em CONTRATO_A2A.md e uma jornada real permitida quando disponível; confirmar cancelamento/reconciliação.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Inventar endpoint de embeddings, headers, enum ou métodos não expostos; trocar o gateway por provedor público.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S04 de docs/sprints/S04_adaptador_a2a.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Se o gateway estiver indisponível, conclua adaptador e testes locais possíveis, registrando homologação externa pendente sem declarar integração comprovada.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S04.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
