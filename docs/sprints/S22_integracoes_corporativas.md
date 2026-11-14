# S22 — Homologação de fontes internas e jornadas completas

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S11](S11_analise_sequencial.md), [S15](S15_editor_exportacao_html.md), [S16](S16_catalogo_sistemas.md), [S17](S17_executor_web.md), [S18](S18_executor_desktop.md), [S20](S20_pacotes_automacao.md)
- Requisitos: R16, R17, R18, R22, R24, R14 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [Arquitetura](ARQUITETURA.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Comprovar a integração real de pelo menos uma fonte corporativa e documentar o estado individual das demais.

## Inspecionar antes de editar

Acesso autorizado ao PLM, GMQIS/GMES, ambiente de homologação, exemplos de filtros/relatórios e contrato de dados.

## Trabalho de implementação

1. Escolher consulta PLM de defeitos SW por modelo/período e definir resultado esperado com dados permitidos ou ambiente de teste.
2. Configurar acesso e implementar capacidade real sem hardcode de dados; validar paginação, filtros, exportação e timestamp.
3. Executar sistema→arquivo→pipeline→análise e sistema→dados→dashboard HTML editável; manter rastreabilidade das fontes.
4. Homologar GMQIS e GMES em suas próprias capacidades quando acessíveis; registrar explicitamente configurado/testado/pendente por sistema.
5. Testar perguntas de parâmetros, autenticação expirada, cancelamento, zero resultados, erro de download e retomada.
6. Documentar mapeamentos, limites, evidências saneadas e procedimentos de manutenção quando a interface do sistema mudar.

## Entregáveis

Conectores/capacidades reais homologados, relatório por sistema e demonstração integrada do produto.

## Critérios de aceite

- [ ] Consulta PLM comprovada retorna dados compatíveis com filtros e resultado de referência autorizado.
- [ ] Resposta/dashboards identificam fonte, período, momento da coleta e limitações.
- [ ] Nenhuma fonte pendente é apresentada como integrada só por existir no seletor.
- [ ] Pedido pontual de consulta funciona sem exigir criação/exportação de automação pelo usuário.

## Verificação obrigatória

E2E corporativo autorizado, comparação do relatório baixado com consulta de referência e testes de recuperação; não usar produção para carga destrutiva.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Inventar acesso ou resultado corporativo; marcar três fontes como homologadas porque uma funcionou.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S22 de docs/sprints/S22_integracoes_corporativas.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Caso acesso real falte, registre exatamente o que impede homologação. Não substituir esse gate por demonstração com dados falsos.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S22.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
