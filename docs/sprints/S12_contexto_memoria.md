# S12 — Contexto, memória e referências persistentes

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S02](S02_autenticacao_permissoes.md), [S03](S03_chat_sessoes_layout.md), [S10](S10_rag_busca_hibrida.md), [S11](S11_analise_sequencial.md)
- Requisitos: R03, R09, R10, R12 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Dar continuidade útil às conversas sem carregar todo histórico ou misturar informações entre usuários.

## Inspecionar antes de editar

Persistência de conversas, contexto mantido pelo serviço A2A, políticas de memória e recuperação.

## Trabalho de implementação

1. Separar histórico, estado de trabalho, biblioteca e memória; definir tipos e escopos pessoal/projeto/compartilhado.
2. Implementar memória com origem, validade, revisão, correção e exclusão; inferências frágeis não devem virar fatos permanentes silenciosamente.
3. Montar contexto com objetivo atual, estado confirmado, fontes e preferências relevantes, respeitando orçamento do modelo.
4. Resumir histórico antigo de forma versionada e conservar referências aos originais; abrir contexto remoto novo quando necessário sem perder estado local.
5. Expor controles simples para consultar, corrigir e apagar memórias e definir retenção.
6. Incluir referências clicáveis a documentos, páginas, células e versões nas respostas e projetos visuais.

## Entregáveis

Gerenciador de contexto, memória controlável, referências persistentes e interface de gestão.

## Critérios de aceite

- [ ] Conversa longa permanece dentro do orçamento configurado sem reenviar histórico inteiro.
- [ ] Usuário consegue corrigir/apagar uma memória e a alteração afeta respostas futuras.
- [ ] Memória privada não é recuperada por outro usuário nem por projeto sem acesso.
- [ ] Referência aponta à versão usada, inclusive quando o original recebe atualização.

## Verificação obrigatória

Conversas longas, resumo de histórico, revogação, memória conflitante, mudança de usuário e retomada após nova tarefa/contexto A2A.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Guardar toda mensagem como memória permanente ou usar resumo como substituto do original auditável.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S12 de docs/sprints/S12_contexto_memoria.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
O histórico mantido pelo gateway não dispensa persistência local e orçamento; valide ambos os níveis.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S12.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
