# S02 — Autenticação, permissões e isolamento

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S01](S01_fundacao_dominio.md)
- Requisitos: R02, R04, R12, R23 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Garantir que cada usuário tenha acesso apenas às suas sessões e aos recursos explicitamente compartilhados.

## Inspecionar antes de editar

Autenticação atual, SSO corporativo disponível, armazenamento de sessão e endpoints que aceitam IDs de recursos.

## Trabalho de implementação

1. Implementar ou completar login/logout e recuperação de acesso; usar o provedor corporativo quando confirmado. Se login local for necessário, usar biblioteca consolidada e hashes adequados.
2. Definir papéis e escopos mínimos de compartilhamento; autorização no backend e nos workers, não apenas no frontend.
3. Proteger cookies/sessões, revogação, CSRF quando aplicável, tentativas de login e endpoints sensíveis.
4. Aplicar ownership/ACL a conversas, mensagens, anexos, jobs, artifacts e conexões; preparar filtro obrigatório para recuperação e memória.
5. Derivar o e-mail corporativo encaminhado ao gateway da identidade autenticada e validada.
6. Registrar eventos de acesso relevantes com logs saneados; estabelecer expiração e comportamento de sessão encerrada durante job.

## Entregáveis

Autenticação funcional, política de ACL reutilizável, testes entre usuários e telas de entrada/erro/saída.

## Critérios de aceite

- [ ] Usuários A e B não consultam recursos privados um do outro por troca de IDs, URL, API ou worker.
- [ ] Logout/revogação invalida sessão conforme política e não expõe respostas de jobs privados.
- [ ] Compartilhamento explícito e revogação são aplicados pelo backend.
- [ ] Credenciais corporativas não são devolvidas ao navegador nem registradas em logs.

## Verificação obrigatória

Testar acesso direto a IDs, usuário desativado, sessão expirada, recuperação/SSO em ambiente permitido e compartilhamento revogado.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Criar contas de produção ou conceder acesso amplo para facilitar testes.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S02 de docs/sprints/S02_autenticacao_permissoes.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Use dois usuários sintéticos e teste negações reais de acesso, incluindo os caminhos indiretos de arquivos e jobs.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S02.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
