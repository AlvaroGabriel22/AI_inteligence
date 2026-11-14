# S19 — Construção e edição de automações por conversa

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S12](S12_contexto_memoria.md), [S16](S16_catalogo_sistemas.md), [S17](S17_executor_web.md), [S18](S18_executor_desktop.md)
- Requisitos: R19, R24, R11 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [CONTRATOS_INTERNOS.md](CONTRATOS_INTERNOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Transformar solicitações e execuções assistidas em fluxos parametrizados que podem ser editados e testados.

## Inspecionar antes de editar

Contratos de executores, jobs, perguntas ao usuário e modelo proposto de definição/run/checkpoint.

## Trabalho de implementação

1. Criar representação de fluxo com etapas, inputs/outputs, variáveis, condições, loops, subfluxos, pré-condições e validações.
2. Implementar ciclo de planejamento, execução assistida, perguntas e revisão; persistir a definição em construção a cada mudança significativa.
3. Extrair lógica reutilizável das observações e instruções; não converter uma lista de coordenadas em única fonte da automação.
4. Parametrizar datas, modelos, caminhos e tabelas; registrar dependências de ambiente e referências de conexão.
5. Permitir teste com nova entrada, edição pelo chat e versionamento; reparo de fluxo cria revisão auditável e não altera silenciosamente uma versão em uso.
6. Implementar reconciliação por item em loops de escrita: se OS foi criada e gravação em Excel falhou, recuperar número existente antes de criar outra.

## Entregáveis

Construtor conversacional, modelo de fluxo editável, versões testadas e execução com parâmetros.

## Critérios de aceite

- [ ] Usuário consegue ensinar processo, responder pergunta e continuar sem perder etapas construídas.
- [ ] Loop usa novos registros de entrada e condições, não apenas a sequência da demonstração original.
- [ ] Fluxo salvo executa em sessão nova sem depender de todo o histórico do chat.
- [ ] Cenário OS sintético não duplica operações após falha entre criação e escrita na coluna D.
- [ ] Busca pontual também funciona sem forçar publicação de automação.

## Verificação obrigatória

Criar→executar→perguntar→retomar→editar→testar nova entrada; loops vazios/mistos, falha de validação e reconciliação de efeitos.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Prometer criação universal sem instruções ou acesso; executar testes de escrita em produção fora do escopo autorizado.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S19 de docs/sprints/S19_construtor_automacoes.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Demonstre separadamente definição reutilizável e estado de uma execução. Valide a generalização com dados diferentes dos usados na construção.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S19.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
