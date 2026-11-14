# S13 — Chat com resultados ricos e progresso completo

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S03](S03_chat_sessoes_layout.md), [S05](S05_jobs_filas_eventos.md), [S11](S11_analise_sequencial.md), [S12](S12_contexto_memoria.md)
- Requisitos: R03, R11, R13 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Apresentar respostas e etapas com clareza, incluindo formatos ricos e interação durante trabalhos longos.

## Inspecionar antes de editar

Design system, streaming/eventos existentes, suporte a Markdown e componentes de resultados.

## Trabalho de implementação

1. Implementar renderização segura de Markdown, listas, tabelas extensas, código copiável com linguagem e fluxogramas por sintaxe suportada.
2. Renderizar resultados estruturados como gráficos/tabelas quando o contrato permitir, com origem e download.
3. Mostrar etapa, arquivo atual, progresso mensurável, resultado parcial e pendências, sem inventar percentual ou status.
4. Integrar perguntas do agente, autenticação pendente, cancelamento, reprocessamento e recuperação de conexão na conversa.
5. Atualizar entregas com IDs estáveis e revisões; marcar quando uma conclusão foi substituída pela consolidação.
6. Testar acessibilidade, comportamento de seleção/cópia, rolagem, anexos, estados vazios e layouts em telas pequenas.

## Entregáveis

Renderers ricos, timeline de trabalho, componentes de perguntas/retomada e testes de interface.

## Critérios de aceite

- [ ] Tabela, lista, fluxograma, Markdown, código e gráfico são demonstrados com dados sintéticos válidos.
- [ ] Código exibido não executa automaticamente; conteúdo não injeta scripts na sessão.
- [ ] Progresso corresponde aos eventos persistidos e continua correto após reload.
- [ ] Resultados parciais e finais têm identificação acessível e não se duplicam.

## Verificação obrigatória

E2E com mensagem longa, bloco malformado, HTML/script no texto, tabela grande, pergunta pendente e reconnect em evento parcial.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Exibir raciocínio interno do modelo ou animações que afirmem etapas não ocorridas.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S13 de docs/sprints/S13_chat_resultados_ricos.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Valide a experiência real do usuário acompanhando um lote lento, não apenas screenshots de estado vazio.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S13.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
