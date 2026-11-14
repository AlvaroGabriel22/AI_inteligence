# S18 — Executor desktop e ambiente de ferramentas

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S05](S05_jobs_filas_eventos.md), [S06](S06_biblioteca_upload.md), [S16](S16_catalogo_sistemas.md), [S17](S17_executor_web.md)
- Requisitos: R18, R19, R24 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Operar aplicativos nativos em máquina compatível e integrar arquivos/terminal ao mesmo contrato de execução.

## Inspecionar antes de editar

SO real dos aplicativos, disponibilidade de sessão gráfica, rede, permissões, acessibilidade e ferramentas corporativas autorizadas.

## Trabalho de implementação

1. Criar executor local/servidor com registro de capacidades, vínculo à identidade e comunicação autenticada com o coordenador.
2. Implementar observação e ações usando acessibilidade nativa quando disponível, com visão/coordenadas verificadas como fallback controlado.
3. Tratar janelas, foco, diálogos, arquivos, estados de bloqueio da máquina e acesso exclusivo quando dois jobs disputarem o mesmo desktop.
4. Oferecer ferramentas de filesystem e terminal limitadas ao workspace/escopo, com timeout, captura saneada de resultado e dependências controladas.
5. Instalar bibliotecas necessárias em ambiente isolado e reproduzível quando autorizado; registrar versões e evitar alterações globais silenciosas.
6. Validar tarefa com aplicativo real representativo do SO alvo e cenário sintético de planilha/documento; separar homologação de SAP ou outro app proprietário.

## Entregáveis

Runner desktop compatível, capacidades declaradas, ferramentas de arquivos/terminal e integração com eventos/checkpoints.

## Critérios de aceite

- [ ] Job é executado somente em runner com SO/aplicativos/sessão compatíveis.
- [ ] Foco incorreto ou tela bloqueada não dispara digitação em janela aleatória.
- [ ] Dois jobs não controlam simultaneamente a mesma sessão de desktop.
- [ ] Falha de ferramenta ou instalação preserva estado e é mostrada com resultado real.

## Verificação obrigatória

Teste em SO alvo, diálogos, perda de foco, bloqueio de sessão, arquivo inexistente, conflito entre jobs e limites de processo.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Afirmar que simulação Linux prova automação Windows/SAP; executar comandos de páginas/documentos como instruções confiáveis.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S18 de docs/sprints/S18_executor_desktop.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Se o SO ou aplicativo alvo não estiver disponível, implemente o contrato e testes possíveis, deixando a validação desktop real explicitamente pendente.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S18.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
