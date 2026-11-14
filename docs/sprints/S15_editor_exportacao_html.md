# S15 — Editor visual, versões e exportação de artefatos

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S14](S14_geracao_html.md)
- Requisitos: R04, R14, R15 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [CONTRATOS_INTERNOS.md](CONTRATOS_INTERNOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Permitir editar por conversa e controles visuais, restaurar versões e exportar artefatos utilizáveis.

## Inspecionar antes de editar

Schema e renderer de S14, versionamento, armazenamento de datasets e requisitos de export offline.

## Trabalho de implementação

1. Implementar controles de texto, tema, cor, ordem, layout, tipo/configuração de gráfico e slides dentro do schema suportado.
2. Aplicar edições pelo chat como patches validados; proteger contra atualização sobre revisão antiga sem resolver conflito.
3. Adicionar salvar, desfazer/refazer quando suportado, histórico e restauração, preservando vínculos com dados.
4. Gerar HTML exportável e pacote de projeto editável com assets/dependências necessárias e manifest de compatibilidade.
5. Separar exportação estática de atualização ao vivo; indicar quando o artefato contém snapshot dos dados e quando depende de conexão.
6. Expor download/compartilhamento autorizado e conferir abertura em ambiente limpo.

## Entregáveis

Editor funcional, revisões, patches pelo chat, export HTML e pacote editável.

## Critérios de aceite

- [ ] Mudar cor/posição de card mantém os números e as fontes sem recalcular ou inventar dados.
- [ ] Alterar filtro/dataset refaz cálculo por código e registra nova revisão.
- [ ] Versão anterior pode ser restaurada; edição concorrente não apaga silenciosamente outra revisão.
- [ ] HTML exportado abre conforme contrato documentado e projeto importado mantém capacidade de edição.

## Verificação obrigatória

E2E criar→editar visualmente→editar pelo chat→restaurar→exportar→abrir/importar; validar assets e tamanho.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Prometer editor irrestrito de qualquer aplicação web; incluir credenciais no HTML ou pacote.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S15 de docs/sprints/S15_editor_exportacao_html.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Teste editabilidade do projeto e portabilidade do HTML separadamente; são entregáveis distintos.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S15.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
