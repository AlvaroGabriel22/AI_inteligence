# S21 — Prompts, guias e central de conteúdo compartilhado

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S12](S12_contexto_memoria.md), [S13](S13_chat_resultados_ricos.md), [S15](S15_editor_exportacao_html.md), [S20](S20_pacotes_automacao.md)
- Requisitos: R04, R12, R21 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Oferecer orientação e reutilização acessíveis a não desenvolvedores dentro da mesma interface.

## Inspecionar antes de editar

Navegação, biblioteca, catálogo de automações, permissões e fluxos comprovados.

## Trabalho de implementação

1. Criar catálogo de prompts com título, descrição, categoria, parâmetros, versão e escopo; inserir no compositor com revisão pelo usuário.
2. Criar guias para upload, análise progressiva, dados, editor visual, fontes internas e automações; basear exemplos nas funções entregues.
3. Organizar área de automações compartilhadas com descrição, autor, versão, requisitos, acesso e ação de importar/usar conforme contexto.
4. Implementar pesquisa, filtros e favoritos quando coerente com a interface existente, sem tornar navegação complexa.
5. Definir edição/publicação de conteúdo por papéis e histórico; conteúdo compartilhado não pode ampliar permissões de quem executa.
6. Revisar terminologia e estados para esconder detalhes internos que não ajudam o usuário a decidir.

## Entregáveis

Prompts parametrizados, guias em português, central compartilhada e integração com o chat.

## Critérios de aceite

- [ ] Usuário utiliza prompt sem editar código e consegue entender quais dados fornecer.
- [ ] Guia só anuncia comportamentos implementados e informa limitações atuais.
- [ ] Automação compartilhada continua exigindo acesso do usuário ao sistema e às conexões necessárias.
- [ ] Conteúdo privado não aparece em pesquisa/favoritos de terceiros.

## Verificação obrigatória

Jornadas de primeiro uso, guia→chat, template com campos faltantes, compartilhamento/revogação e navegação por teclado.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Criar botões sem funcionalidade, catálogo fictício em produção ou prompts capazes de burlar ACL.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S21 de docs/sprints/S21_prompts_guias_central.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
A simplicidade da interface deve ser comprovada nas tarefas reais, com linguagem de usuário final.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S21.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
