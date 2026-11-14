# S01 — Fundação de domínio e persistência

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S00](S00_inventario_baseline.md)
- Requisitos: R01, R03, R04, R10, R23 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Estabelecer os contratos persistentes necessários aos módulos, com evolução incremental do banco e configuração.

## Inspecionar antes de editar

Inventário de S00, schemas/migrações existentes, configurações, storage e decisões de arquitetura; ler CONTRATOS_INTERNOS.md.

## Trabalho de implementação

1. Definir entidades mínimas e relações: usuário, conversa, mensagem, arquivo/versão, job/step/evento, artifact, conexão e definições de automação.
2. Estabelecer IDs, timestamps, ownership/ACL, versionamento de schema e referências de origem. Implementar somente entidades necessárias à fundação; adicionar detalhes nas sprints próprias.
3. Preparar migrações compatíveis e procedimento de recuperação; evitar migrações destrutivas silenciosas.
4. Separar interfaces de armazenamento, processamento, provedor IA e executor para facilitar testes e preservar a implementação existente.
5. Centralizar configurações, quotas e secrets; fornecer exemplos sem credenciais e validação no startup.
6. Decidir fila e armazenamento em ADR; documentar ambiente local reproduzível, health checks e política de logs.

## Entregáveis

Modelo de domínio inicial, migrações, configurações validadas, interfaces e ADRs de persistência/fila.

## Critérios de aceite

- [ ] Aplicação existente continua iniciando e o fluxo anterior permanece utilizável.
- [ ] Banco novo e banco com versão anterior suportada migram de forma verificada.
- [ ] Nenhuma entidade de usuário depende de um namespace global sem ownership definido.
- [ ] Erros de configuração são explícitos e não revelam tokens.

## Verificação obrigatória

Testar migração em banco descartável, recuperação conforme política e serialização dos contratos; executar regressão relevante do fluxo existente.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Implementar todo o produto de uma vez; criar microserviços sem necessidade demonstrada.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S01 de docs/sprints/S01_fundacao_dominio.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Evolua a fundação com a stack aprovada em S00; trate nomes em CONTRATOS_INTERNOS como proposta interna, não como API pública já existente.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S01.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
