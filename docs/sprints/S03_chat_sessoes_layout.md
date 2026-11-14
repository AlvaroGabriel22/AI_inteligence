# S03 — Chat persistente e estrutura da interface

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S02](S02_autenticacao_permissoes.md)
- Requisitos: R03, R11, R13, R21 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Entregar o núcleo visual do produto e conversas persistentes sobre o chat existente.

## Inspecionar antes de editar

Componentes atuais de chat, design system, roteamento, histórico, responsividade e acessibilidade.

## Trabalho de implementação

1. Criar ou melhorar estrutura com navegação para Chat, Biblioteca, Automações e Prompts/Guias; módulos ainda indisponíveis devem ter estado honesto ou ficar ocultos.
2. Implementar criação, listagem, busca e retomada de conversas conforme permissões; preservar mensagens existentes.
3. Organizar compositor, anexos, área de mensagens, ações de copiar e estado de envio; preparar área de etapas e resultados.
4. Adicionar estados vazios, erro e rede indisponível, comportamento de rolagem que respeite leitura do usuário, foco e teclado.
5. Definir padrões de spacing, tipografia, cores e componentes sem textos técnicos desnecessários na interface.
6. Persistir mensagens e correlacionar resposta/solicitação; impedir duplicação por duplo envio ou reconexão.

## Entregáveis

Chat navegável com histórico, layout responsivo, estados de interação e componentes reutilizáveis.

## Critérios de aceite

- [ ] Recarregar ou abrir novamente a sessão restaura a conversa correta do usuário.
- [ ] Mensagens não se duplicam por reenvio da interface.
- [ ] Usuário consegue ler mensagens antigas sem a rolagem ser forçada continuamente.
- [ ] Fluxo básico funciona por teclado e em larguras representativas de desktop e mobile.

## Verificação obrigatória

E2E de criar/reabrir conversas, refresh, isolamento entre usuários, anexos e estados de erro; inspeção visual com conteúdo longo.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Construir editor visual completo, fluxos de automação ou anunciar funcionalidades ainda ausentes.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S03 de docs/sprints/S03_chat_sessoes_layout.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Priorize o chat como área principal. Demonstre persistência e boa interação usando o fluxo atual de análise.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S03.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
