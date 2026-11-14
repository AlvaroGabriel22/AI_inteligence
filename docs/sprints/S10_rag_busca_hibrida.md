# S10 — Chunks, embeddings e busca híbrida

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S02](S02_autenticacao_permissoes.md), [S07](S07_extracao_formatos.md), [S08](S08_ocr_qualidade.md), [S09](S09_dados_calculos.md)
- Requisitos: R09, R10, R12 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PIPELINE_DOCUMENTOS.md](PIPELINE_DOCUMENTOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Recuperar evidências relevantes por significado e palavras exatas com isolamento, qualidade e controle de custo.

## Inspecionar antes de editar

Modelos de unidades, ACL, provedor de embeddings permitido e consultas de avaliação rotuladas.

## Trabalho de implementação

1. Implementar chunks por estrutura e orçamento, com referências à versão e sem quebrar tabelas indiscriminadamente.
2. Criar índice lexical e vetorial, registrar modelo/dimensão e regras de reindexação; nunca supor que A2A fornece embeddings.
3. Aplicar autorização e filtros de escopo antes da recuperação; impedir bypass em busca, cache e download de evidências.
4. Combinar resultados lexicais/semânticos e avaliar reranking apenas se a melhora justificar custo/latência.
5. Montar contexto limitado com citações e diversidade relevante; lidar com zero evidência e documentos contraditórios.
6. Reutilizar índices por versão/configuração; revogar/remover resultados após mudanças de acesso/exclusão conforme política.

## Entregáveis

Recuperador híbrido, indexador versionado, métricas de avaliação e montagem de contexto com fontes.

## Critérios de aceite

- [ ] Códigos exatos e perguntas por sinônimos são cobertos por casos de avaliação separados.
- [ ] Chunks privados nunca entram no contexto de usuário sem acesso, inclusive via cache.
- [ ] Mudança do modelo de embeddings não mistura vetores incompatíveis.
- [ ] Pergunta sem suporte retorna insuficiência de evidência; citações apontam ao trecho utilizado.

## Verificação obrigatória

Medir recall/ranking no corpus, controles entre usuários, revogação, versões divergentes, prompt injection em documentos e consulta sem resposta.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Tratar RAG top-k como tradução/leitura integral ou instalar todas as técnicas sem avaliação.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S10 de docs/sprints/S10_rag_busca_hibrida.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Registre comparação com baseline lexical e escolha a estratégia por resultados medidos.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S10.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
