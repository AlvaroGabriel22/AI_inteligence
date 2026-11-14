# S14 — Geração de dashboards e apresentações HTML

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S09](S09_dados_calculos.md), [S11](S11_analise_sequencial.md), [S13](S13_chat_resultados_ricos.md)
- Requisitos: R08, R13, R14, R15 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [CONTRATOS_INTERNOS.md](CONTRATOS_INTERNOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Criar artefatos visuais a partir de dados verificados e apresentar uma prévia isolada e persistente.

## Inspecionar antes de editar

CONTRATOS_INTERNOS.md, resultados tabulares, renderer disponível e padrões de componentes visuais.

## Trabalho de implementação

1. Definir schema versionado de projeto com páginas/slides, componentes, tema e vínculos com datasets.
2. Implementar componentes de cards, barras, tabelas, textos e navegação adequados ao pedido; separar modo dashboard e apresentação.
3. Converter instrução natural em proposta estruturada validada, reutilizando cálculos e evidências do backend.
4. Gerar conteúdo somente a partir dos dados disponíveis; quando faltar métrica/unidade necessária, pedir detalhe ou indicar lacuna.
5. Renderizar prévia isolada da sessão principal, com recursos/dependências controlados e tratamento de erros de renderização.
6. Salvar projeto, versão, fontes e resultado da validação; permitir entrega progressiva de seções coerentes.

## Entregáveis

Schema de projeto, componentes de renderer, fluxo chat→dados→artefato e prévia funcional.

## Critérios de aceite

- [ ] Pedido de cards e barras azuis a partir de anexos produz projeto com números iguais aos cálculos de referência.
- [ ] Gráficos preservam títulos, unidades, filtros e origem; dados ausentes não viram valores fictícios.
- [ ] Prévia não acessa cookies/tokens da plataforma nem executa rede fora da política.
- [ ] Artefato reaparece corretamente ao reabrir conversa/biblioteca.

## Verificação obrigatória

Validar schema, números/series dos gráficos, estados sem dados, conteúdo malicioso, responsividade e renderização de apresentação.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Gerar HTML livre e inserir diretamente na árvore da aplicação autenticada; tratar screenshot como projeto editável.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S14 de docs/sprints/S14_geracao_html.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Faça a IA propor a organização e o código validar dados, estrutura e renderização antes de marcar o artefato como concluído.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S14.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
