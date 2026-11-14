# S00 — Inventário do projeto e baseline

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: Nenhuma: ponto de entrada do plano.
- Requisitos: R01, R22, R23 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Conhecer a aplicação existente e produzir um plano de evolução compatível com ela, sem reescrita especulativa.

## Inspecionar antes de editar

Raiz real do projeto, AGENTS.md, estado do git, manifests/lockfiles, rotas de chat, client A2A, persistência, testes, configuração saneada e forma atual de iniciar.

## Trabalho de implementação

1. Confirmar o diretório de trabalho e ler as instruções do repositório; não criar uma cópia vazia se o caminho real estiver inacessível.
2. Mapear frontend, backend, banco, arquivos e serviços externos; identificar o que já atende aos requisitos deste plano.
3. Executar os comandos de desenvolvimento e verificações existentes quando disponíveis; registrar falhas anteriores à sprint.
4. Desenhar o fluxo atual do anexo até a resposta e localizar autenticação, limites, timeout, estado de sessão e tratamento de erro.
5. Identificar dados faltantes do gateway sem expor secrets; preparar checklist saneado e confirmar infraestrutura/OS, concorrência desejada, SSO e política de dados.
6. Criar inventário de módulos e matriz manter/adaptar/adicionar, mapa de riscos observados e ADR inicial de evolução; ajustar o planejamento com evidência.

## Entregáveis

Relatório de baseline, inventário, lacunas por requisito, comandos reais de execução/teste e ADR da abordagem.

## Critérios de aceite

- [ ] A estrutura real e o fluxo atual estão descritos com referências de arquivos existentes.
- [ ] Testes executados são separados de indisponíveis; nenhum estado antigo é atribuído à nova implementação.
- [ ] Componentes reaproveitáveis e dependências externas não comprovadas estão identificados.
- [ ] Próxima sprint possui ponto de partida concreto e nenhum segredo foi copiado.

## Verificação obrigatória

Repetir uma jornada atual com arquivo sintético, se ambiente/configuração estiverem disponíveis; validar configuração de exemplo sem chamar produção desnecessariamente.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Reescrever a aplicação; escolher cloud/stack sem evidência; instalar uma base nova no lugar do sistema atual.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S00 de docs/sprints/S00_inventario_baseline.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Comece pelo inventário. Preserve o código existente e registre bloqueios reais. Não implemente as outras sprints nesta execução.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S00.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
