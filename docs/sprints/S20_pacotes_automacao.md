# S20 — Exportação, importação e compartilhamento de automações

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S02](S02_autenticacao_permissoes.md), [S04](S04_adaptador_a2a.md), [S19](S19_construtor_automacoes.md)
- Requisitos: R04, R20, R24 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [CONTRATOS_INTERNOS.md](CONTRATOS_INTERNOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Transportar definições de automação entre ambientes compatíveis e permitir uso pelo chat principal.

## Inspecionar antes de editar

CONTRATOS_INTERNOS.md, schemas/versionamento de S19, ACL e política de dependências.

## Trabalho de implementação

1. Definir manifest/versionamento, schemas de inputs/outputs, runtime/SO, permissões, dependências e referências de conexão do pacote.
2. Exportar definição e código necessário sem tokens, cookies, sessões, dados de execuções ou credenciais; verificar pacote antes de disponibilizar.
3. Importar com validação de integridade, tamanho, paths e compatibilidade, sem executar automaticamente; negociar conexões locais após importação.
4. Publicar no catálogo interno e compartilhar com escopo explícito/revogável; habilitar chamada pelo chat sem download/reimportação na mesma plataforma.
5. Criar integração documentada para sistema externo: importar/registrar, executar com parâmetros, acompanhar, responder entrada pendente e obter artifacts.
6. Quando a integração externa usar A2A, implementar fachada/contrato explícito e validar separadamente; o gateway corporativo de análise não é presumido como host do executor.

## Entregáveis

Pacote exportável, importador validado, galeria compartilhada, catálogo e contrato de integração externa.

## Critérios de aceite

- [ ] Exportar→importar em ambiente limpo compatível→configurar conexão→executar nova entrada funciona sem conversa original.
- [ ] Pacote não contém segredos ou dados de execução excluídos por padrão.
- [ ] Versão incompatível/dependência ausente/path traversal é rejeitada com diagnóstico útil.
- [ ] Revogação retira acesso futuro no catálogo; documentar que cópias já baixadas não podem ser recolhidas automaticamente.
- [ ] Após configuração, executar pelo chat ou ação de um clique usa a versão selecionada.

## Verificação obrigatória

Portabilidade em ambiente limpo, manifesto malicioso, tamanho excessivo, revisão antiga, usuário sem acesso e pacote adulterado.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Anunciar arquivo universal que roda em qualquer sistema sem executor; instalar e executar pacote no ato do upload.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S20 de docs/sprints/S20_pacotes_automacao.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
O critério principal é executar em outro ambiente compatível, com novos dados, sem senhas embutidas e sem histórico original.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S20.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
