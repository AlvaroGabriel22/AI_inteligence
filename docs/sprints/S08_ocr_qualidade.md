# S08 — OCR, layout e qualidade de extração

Estado inicial: **PLANEJADA**. Unidade de entrega, sem duração de calendário presumida.

- Dependências: [S07](S07_extracao_formatos.md)
- Requisitos: R06, R08, R09, R11 — ver [escopo](CONTEXTO_E_ESCOPO.md).
- Contratos específicos: [PIPELINE_DOCUMENTOS.md](PIPELINE_DOCUMENTOS.md)
- Execução: [guia do Codex](GUIA_EXECUCAO_CODEX.md).

## Resultado esperado

Ler digitalizações e imagens mantendo qualidade mensurável, localização e limites de processamento.

## Inspecionar antes de editar

Páginas sinalizadas em S07, imagens PNG/JPG, idiomas do corpus e recursos locais/corporativos disponíveis.

## Trabalho de implementação

1. Selecionar mecanismo de OCR autorizado e configurar idioma, resolução, timeout e orçamento de pixels/páginas.
2. Processar PDFs mistos por página/região; evitar duplicar a camada de texto já extraída.
3. Preservar coordenadas, página, texto reconhecido e indicadores de confiança quando disponíveis; não transformar confiança numérica em garantia de correção.
4. Sinalizar baixa legibilidade, tabelas com estrutura incerta e elementos visuais que exigem visão além de OCR.
5. Exibir progresso real de páginas e erros parciais; permitir repetir apenas unidades falhas ou substituídas.
6. Separar provedor OCR de eventual interpretação visual pela IA; confirmar autorização/capacidade antes de encaminhar imagens.

## Entregáveis

Pipeline OCR integrado, indicadores de qualidade, recuperação de unidades e referências visuais.

## Critérios de aceite

- [ ] PDF misto preserva texto e OCR sem duplicação indevida.
- [ ] Documento pouco legível é identificado e não sustenta conclusões sem ressalva de cobertura.
- [ ] Interrupção retoma unidades pendentes sem repetir o documento inteiro desnecessariamente.
- [ ] Tempo e memória permanecem dentro dos limites configurados no corpus testado.

## Verificação obrigatória

Fixtures com rotações, texto português/inglês, baixa resolução, páginas em branco, tabela digitalizada e excesso de pixels.

Aplicar também a [definição de pronto](GUIA_EXECUCAO_CODEX.md) e os cenários pertinentes do [plano de testes](PLANO_DE_TESTES.md). Evidência real e teste de simulador são categorias distintas.

## Fora desta entrega

Prometer OCR perfeito; enviar todo o documento a modelo visual sem necessidade ou autorização.

## Prompt para execução no Codex

```text
No repositório /home/alvaro/Documentos/AI_Inteligence, execute a sprint S08 de docs/sprints/S08_ocr_qualidade.md.
Leia as instruções aplicáveis do repositório, docs/sprints/GUIA_EXECUCAO_CODEX.md, CONTEXTO_E_ESCOPO.md, STATUS.md e as dependências necessárias.
Meça qualidade e cobertura. Para figuras sem texto suficiente, informe a necessidade de interpretação visual em vez de inventar conteúdo.
Implemente de ponta a ponta o escopo desta sprint, preserve trabalho existente e valide os critérios de aceite com evidências.
Continue autonomamente nas decisões reversíveis. Se faltar dado indispensável, faça uma pergunta específica e avance nas partes independentes.
Registre o resultado em docs/sprints/evidencias/S08.md e atualize STATUS.md e plano.json sem declarar testes ou integrações que não foram executados.
Encerre informando o resultado, verificações, limitações reais e a próxima sprint elegível.
```

## Saída e retomada

Usar o [template de relatório](templates/RELATORIO_SPRINT.md). Estado final deve refletir implementação e homologação reais. Se bloquear, registrar o passo de retomada e a dependência exata; não apagar trabalho independente concluído.
