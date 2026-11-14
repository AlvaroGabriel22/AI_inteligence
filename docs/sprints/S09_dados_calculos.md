# S09 — Dados tabulares, filtros e cálculos verificáveis

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S07](S07_extracao_formatos.md)
- Requisitos: R08, R09, R14 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PIPELINE_DOCUMENTOS.md](PIPELINE_DOCUMENTOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Responder perguntas quantitativas usando consultas e cálculos sobre dados completos do escopo aplicável.

## Inspecionar antes de editar

Extrações XLSX/CSV/tabelas, tipos e chaves, regras de datas/decimais e mecanismos SQL/dataframe existentes.

## Trabalho de implementação

1. Normalizar datasets sem perder origem, aba, linha, coluna, unidade e valor original.
2. Implementar filtros e agregações de contagens, somas, agrupamentos, rankings e séries; tratar nulos, duplicatas e intervalos de data explicitamente.
3. Validar consultas ou planos estruturados propostos pela IA antes de executar; usar privilégios de leitura, limites e parametrização.
4. Implementar junções entre arquivos somente com chave e cardinalidade verificadas; reportar registros sem correspondência e evitar multiplicação silenciosa.
5. Gerar resultado estruturado com universo filtrado, métricas, consulta/plano e fontes para análise e gráficos.
6. Definir política para fórmulas sem valor confiável: recalcular de forma segura ou solicitar/registrar limitação.

## Entregáveis

Serviço de análise tabular, contratos de resultado, consultas validadas e testes numéricos de referência.

## Critérios de aceite

- [ ] Totais e rankings coincidem com o oráculo determinístico para o dataset completo filtrado.
- [ ] Contagem não depende dos primeiros chunks recuperados ou de amostra não declarada.
- [ ] Junção ambígua não gera métricas silenciosamente erradas.
- [ ] Consulta gerada não altera banco nem acessa tabelas/arquivos fora do escopo autorizado.

## Verificação obrigatória

Oráculos de contagem/soma com duplicatas, zeros à esquerda, intervalos inclusivos, fusos, junções 1:N e fórmulas.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Usar embeddings como motor de soma ou deixar SQL/código livre do modelo com privilégios amplos.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S09 de docs/sprints/S09_dados_calculos.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Demonstre os números por código antes de solicitar interpretação textual ao agente.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S09.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
