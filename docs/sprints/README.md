# AI Inteligence — desenvolvimento guiado por sprints

Plano completo para evoluir o chat existente em plataforma corporativa de documentos, análise, HTML editável e automação web/desktop.

**24 sprints, S00 a S23. Todas começam como PLANEJADA. Este pacote contém documentação; não contém a aplicação implementada.**

## Instalação na pasta solicitada

O pacote foi preparado fora da máquina de Álvaro. Extraia o ZIP na raiz `/home/alvaro/Documentos/AI_Inteligence`; os arquivos entram em `docs/sprints/`. Não crie um novo projeto para substituir o existente.

Exemplo, se o ZIP estiver em Downloads:

```bash
unzip -n "$HOME/Downloads/AI_Inteligence_sprints_codex.zip" -d /home/alvaro/Documentos/AI_Inteligence
```

`-n` preserva arquivos existentes. Se já houver documentação com os mesmos nomes, compare as versões antes de substituir. O diretório informado é o destino pretendido na máquina do usuário, não uma confirmação de acesso remoto a ela.

## Como começar

1. Abra a raiz real do projeto no Codex.
2. Se disponível, selecione o perfil solicitado: Astra-6 com esforço extra alto. Os documentos não alteram essa configuração.
3. Use o [prompt inicial](PROMPT_INICIAL.md) para executar S00.
4. Execute as próximas sprints pela ordem da tabela, conferindo os gates e dependências. Cada arquivo possui seu próprio prompt, tarefas, testes e critérios de aceite.
5. Atualize [STATUS.md](STATUS.md) e [plano.json](plano.json) a partir de evidências, nunca por expectativa.

As sprints são unidades de entrega, não estimativas de uma ou duas semanas. Tamanho e duração devem ser recalibrados após o inventário. É permitido subdividir uma sprint com justificativa, preservando requisitos e rastreabilidade.

## Documentos de referência

- [Contexto e escopo](CONTEXTO_E_ESCOPO.md): requisitos R01–R24 e jornadas.
- [Guia do Codex](GUIA_EXECUCAO_CODEX.md): autonomia, critérios de pronto, bloqueios e evidências.
- [Arquitetura](ARQUITETURA.md): módulos e decisões condicionadas ao projeto existente.
- [Contrato A2A](CONTRATO_A2A.md): informado versus comprovado no gateway corporativo.
- [Pipeline de documentos](PIPELINE_DOCUMENTOS.md): grandes arquivos, OCR, busca, cálculos e fila.
- [Contratos internos](CONTRATOS_INTERNOS.md): jobs, eventos, artefatos e pacotes.
- [Plano de testes](PLANO_DE_TESTES.md): corpus sintético, falhas, desempenho e E2E.
- [Matriz de requisitos](MATRIZ_REQUISITOS.md): cobertura por sprint.
- [Fontes e decisões](FONTES_E_DECISOES.md): referências oficiais e premissas.

## Roadmap

| Sprint | Entrega | Dependências |
| --- | --- | --- |
| [S00](S00_inventario_baseline.md) | Inventário do projeto e baseline | — |
| [S01](S01_fundacao_dominio.md) | Fundação de domínio e persistência | S00 |
| [S02](S02_autenticacao_permissoes.md) | Autenticação, permissões e isolamento | S01 |
| [S03](S03_chat_sessoes_layout.md) | Chat persistente e estrutura da interface | S02 |
| [S04](S04_adaptador_a2a.md) | Adaptador A2A corporativo | S01, S02, S03 |
| [S05](S05_jobs_filas_eventos.md) | Jobs duráveis, fila e eventos de progresso | S01, S02, S04 |
| [S06](S06_biblioteca_upload.md) | Biblioteca e upload de arquivos grandes | S02, S03, S05 |
| [S07](S07_extracao_formatos.md) | Extração estruturada de formatos | S05, S06 |
| [S08](S08_ocr_qualidade.md) | OCR, layout e qualidade de extração | S07 |
| [S09](S09_dados_calculos.md) | Dados tabulares, filtros e cálculos verificáveis | S07 |
| [S10](S10_rag_busca_hibrida.md) | Chunks, embeddings e busca híbrida | S02, S07, S08, S09 |
| [S11](S11_analise_sequencial.md) | Análise sequencial e entregas por arquivo | S04, S05, S07, S08, S09, S10 |
| [S12](S12_contexto_memoria.md) | Contexto, memória e referências persistentes | S02, S03, S10, S11 |
| [S13](S13_chat_resultados_ricos.md) | Chat com resultados ricos e progresso completo | S03, S05, S11, S12 |
| [S14](S14_geracao_html.md) | Geração de dashboards e apresentações HTML | S09, S11, S13 |
| [S15](S15_editor_exportacao_html.md) | Editor visual, versões e exportação de artefatos | S14 |
| [S16](S16_catalogo_sistemas.md) | Catálogo de sistemas e seletor no chat | S02, S05, S12, S13 |
| [S17](S17_executor_web.md) | Executor de automação web | S05, S06, S16 |
| [S18](S18_executor_desktop.md) | Executor desktop e ambiente de ferramentas | S05, S06, S16, S17 |
| [S19](S19_construtor_automacoes.md) | Construção e edição de automações por conversa | S12, S16, S17, S18 |
| [S20](S20_pacotes_automacao.md) | Exportação, importação e compartilhamento de automações | S02, S04, S19 |
| [S21](S21_prompts_guias_central.md) | Prompts, guias e central de conteúdo compartilhado | S12, S13, S15, S20 |
| [S22](S22_integracoes_corporativas.md) | Homologação de fontes internas e jornadas completas | S11, S15, S16, S17, S18, S20 |
| [S23](S23_homologacao_operacao.md) | Homologação final, desempenho e operação | S21, S22 |

## Marcos de produto

- **S00–S05:** aplicação inventariada, identidade, chat, gateway e execução durável.
- **S06–S13:** biblioteca, arquivos grandes, OCR, cálculo/RAG, respostas progressivas e memória.
- **S14–S15:** apresentações e dashboards HTML editáveis e exportáveis.
- **S16–S20:** fontes internas, executores, construção e portabilidade de automações.
- **S21–S23:** experiência de apoio, integração corporativa e operação homologada.

Não encerrar o projeto após o piloto PLM: ele faz parte de uma plataforma maior. Não considerar a aplicação pronta para produção apenas por completar o frontend ou os testes com simulador.
