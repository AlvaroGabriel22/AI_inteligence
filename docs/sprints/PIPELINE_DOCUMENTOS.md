# Pipeline de documentos, recuperação e análise

## Entrada e preservação

Armazenar o original imutável e sua versão/hash. Validar assinatura/MIME, integridade e quota antes de processar. Upload acima de 3 MB é permitido dentro dos limites da aplicação; o teto do gateway é aplicado depois, ao construir as chamadas. Não executar macros de Office nem comandos encontrados nos documentos.

Registrar nome, tamanho, tipo, proprietário, ACL, versão, origem, status e configuração de processamento. Distinguir arquivo corrompido, protegido por senha, formato não suportado e extração vazia. Uma falha localizada não pode apagar resultados anteriores.

## Extração por conteúdo

- PDF textual: extrair texto, estrutura, tabelas e coordenadas/páginas; OCR somente onde necessário.
- PDF digitalizado, PNG/JPG: OCR com idioma e qualidade avaliados; preservar a imagem para conferência. OCR não equivale a interpretar um gráfico ou uma fotografia.
- DOCX: títulos, parágrafos, tabelas e referências de origem; registrar elementos não extraídos.
- PPTX: slides, textos, tabelas, imagens e notas quando suportadas; associar fontes ao número do slide.
- PPT legado: conversão isolada com ferramenta apropriada e validação da cobertura. Não anunciar suporte ao formato sem testar.
- XLSX: abas, cabeçalhos, células mescladas, fórmulas e valores, tipos e linhas. Preservar códigos com zeros à esquerda. Fórmulas podem ter cache desatualizado; decidir recalcular em ambiente seguro ou sinalizar indisponibilidade.
- CSV: encoding, delimitador, escape, decimal, cabeçalho e tipos inferidos com evidência. Permitir correção de inferências ambíguas.
- Markdown/TXT: texto e estrutura lógica, encoding e referências de trecho.

Leitores devem controlar expansão de arquivos compactados, quantidade de células, páginas/pixels, memória e tempo. Arquivos de mídia diferentes podem demandar interpretação visual apenas para partes relevantes e com provedor autorizado.

## Roteamento por pergunta

| Pedido | Estratégia |
| --- | --- |
| Pergunta localizada em documentos | Busca híbrida, filtros de escopo e evidências recuperadas; reranking se melhorar métricas. |
| Quantidades, ranking, tendências | Consulta estruturada sobre todos os registros aplicáveis; IA explica resultados calculados. |
| Tradução integral | Percurso completo por unidades, glossário e controle de cobertura; remontagem na ordem original. |
| Resumo integral | Cobertura do documento por blocos com sínteses intermediárias e consolidação, sem apresentar busca top-k como leitura integral. |
| Comparação entre arquivos | Normalização por arquivo, correspondência explícita de chaves, unidades e períodos; consolidação posterior. |
| Dashboard/apresentação | Dataset validado, agregações reproduzíveis, projeto visual e renderer. |

## Chunks e índices

Particionar por conteúdo e orçamento de tokens, respeitando parágrafos, títulos e tabelas. Evitar duplicação causada por overlap em contagens. Chunks guardam versão do documento e ponteiro para a fonte; nunca se tornam a única cópia dos dados.

Busca lexical prioriza termos exatos, códigos e identificadores. Embeddings capturam semelhança de significado. Aplicar ACL e filtros de origem/versão antes da recuperação, combinar rankings e medir qualidade em consultas sintéticas representativas. Reindexar quando documento ou modelo de embeddings mudar; nunca misturar dimensões ou modelos incompatíveis sem controle.

O provedor de embeddings e o de OCR/visão podem ser locais ou corporativos autorizados. Não presumir que o gateway A2A forneça endpoint de embeddings.

## Lotes e resultados progressivos

Para o mesmo lote: preparar/analisar arquivo A, validar e persistir a saída útil de A, publicar evento, então iniciar a análise de B. O usuário deve poder observar essa ordem nos eventos. O navegador não precisa estar conectado para o job continuar. A camada de armazenamento pode receber os anexos antecipadamente; isso não libera chamadas analíticas concorrentes do lote.

Resultados parciais carregam `provisional`, arquivos/unidades cobertos e dependências pendentes. Conclusões sobre o conjunto só ficam finais depois que as fontes necessárias forem cobertas. Se houver erro num arquivo, permitir retomada direcionada; resultado consolidado deve indicar incompletude enquanto faltar uma fonte obrigatória.

Controlar concorrência global, por usuário e por provedor; a sequência local não protege o gateway contra muitos usuários simultâneos. Aplicar filas justas e backpressure, sem fome de jobs pequenos.

## Eficiência e validade

Reusar extração, OCR e embeddings por hash, versão e configuração, respeitando ACL. Resultados de sistemas internos precisam de momento de coleta e política de atualização; cache antigo não deve ser apresentado como consulta atual.

Cada resposta usa fontes verificáveis. A busca sem evidência suficiente retorna limitação ou pede esclarecimento. Texto malicioso em arquivo ou página é dado, não uma instrução para mudar ferramentas, segredos ou escopo de execução.
