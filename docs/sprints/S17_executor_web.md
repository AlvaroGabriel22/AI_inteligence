# S17 — Executor de automação web

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S05](S05_jobs_filas_eventos.md), [S06](S06_biblioteca_upload.md), [S16](S16_catalogo_sistemas.md)
- Requisitos: R17, R19, R24 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Executar consultas web autorizadas com observação, validação, download e retomada.

## Inspecionar antes de editar

Rede corporativa, runtime do navegador, sessões permitidas, aplicação de teste e política de downloads.

## Trabalho de implementação

1. Implementar executor com ciclo observar→agir→verificar, preferindo DOM/acessibilidade e seletores estáveis; visão entra onde comprovadamente necessária.
2. Isolar contextos de navegador por usuário/conexão e gerenciar expiração, autenticação/SSO e handoff para MFA/CAPTCHA quando exigido.
3. Implementar navegação, preenchimento, filtros, paginação e downloads com timeout, checkpoints e validação do estado esperado.
4. Confirmar conclusão e integridade do download, classificar origem/filtros e encaminhar ao pipeline comum da biblioteca.
5. Expor eventos e perguntas ao chat; restringir sites, ações e downloads ao escopo autorizado.
6. Criar aplicação web sintética representativa e avaliar adaptadores/base de agent framework sem assumir dependência de Sai/Hermes.

## Entregáveis

Executor web, ambiente sintético, coleta de arquivos e trilha de execução integrada ao chat.

## Critérios de aceite

- [ ] Consulta com paginação retorna todos os registros aplicáveis e distingue zero resultado de falha.
- [ ] Sessão expirada pede autenticação e retoma sem perder filtros/estado.
- [ ] Mudança de seletor gera recuperação validada ou erro claro, sem clicar cegamente em alvo parecido.
- [ ] Downloads só entram na análise após validação e preservam ACL e origem.

## Verificação obrigatória

Sessão expirada, elemento ausente, download incompleto, pop-up, timeout após ação, página com instruções maliciosas e dois usuários simultâneos.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Compartilhar perfil autenticado entre usuários, contornar MFA ou declarar todas as páginas compatíveis.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S17 de docs/sprints/S17_executor_web.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Priorize a consulta e obtenção de dados. A evidência deve mostrar resultado correto, não apenas uma sequência de cliques.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S17.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
