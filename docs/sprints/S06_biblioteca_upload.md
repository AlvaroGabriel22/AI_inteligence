# S06 — Biblioteca e upload de arquivos grandes

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S02](S02_autenticacao_permissoes.md), [S03](S03_chat_sessoes_layout.md), [S05](S05_jobs_filas_eventos.md)
- Requisitos: R04, R05, R06, R23 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PIPELINE_DOCUMENTOS.md](PIPELINE_DOCUMENTOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Aceitar, armazenar e organizar arquivos maiores que o limite do gateway sem enviar o original indiscriminadamente à IA.

## Inspecionar antes de editar

Storage existente, limites de proxy/API/frontend, quotas, ACL e formato de metadados de arquivos.

## Trabalho de implementação

1. Implementar upload em streaming ou mecanismo resumível adequado, com quota por usuário e teto configurado por arquivo/lote.
2. Validar assinatura, MIME, integridade e tamanho real; guardar original, hash, versão, proprietário e origem.
3. Exibir biblioteca com status de processamento, pesquisa de metadados, versões, download autorizado e vínculos com conversas.
4. Tratar arquivos duplicados sem misturar ACL; definir reuso seguro de bytes/derivados e sem vazamento de existência de arquivos privados.
5. Gerar jobs para processamento sequencial dos anexos; suportar interrupção de upload, limpeza de temporários e idempotência.
6. Implementar compartilhamento/revogação básico e política de exclusão consistente para originais e referências.

## Entregáveis

Upload grande funcional, biblioteca persistente, download autorizado, metadados e criação de jobs.

## Critérios de aceite

- [ ] Arquivo de conteúdo realista acima de 3 MB é aceito dentro do limite configurado da aplicação.
- [ ] Arquivo acima do limite da aplicação é rejeitado antes de processamento caro, com mensagem útil.
- [ ] Upload/download não exige carregar todo arquivo em memória quando a estratégia escolhida prevê streaming.
- [ ] Revogar acesso bloqueia links e endpoints de download conforme política.

## Verificação obrigatória

Testar fronteiras, upload interrompido, duplicado, MIME falso, quota, usuários distintos e arquivos protegidos/corrompidos.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Mandar anexos grandes diretamente ao gateway; supor upload ilimitado ou usar nomes difíceis como controle de acesso.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S06 de docs/sprints/S06_biblioteca_upload.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Separe explicitamente limite de upload, tamanho descompactado e limite final de requisição A2A.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S06.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
