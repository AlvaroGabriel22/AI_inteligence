# Plano de testes e evidências

## Estratégia

Usar testes proporcionais ao risco e às mudanças. Testes unitários para regras e transformações, testes de contrato para A2A, integração para estado/armazenamento e E2E para jornadas reais. Não criar mocks que comprovem apenas a própria implementação. Sucesso em simulador não prova acesso a PLM ou compatibilidade com o gateway corporativo.

## Corpus sintético reproduzível

Criar geradores com seed e um manifest de resultados esperados em área de testes do repositório, definida por S00. Incluir:

| Fixture | Verificação |
| --- | --- |
| PDF textual longo | Texto, páginas e seções preservados; pergunta localizada e tradução integral. |
| PDF digitalizado/misto | OCR nas páginas necessárias; baixa qualidade sinalizada; sem repetir texto já extraído. |
| XLSX multiaba | Códigos com zeros, cabeçalhos mesclados, tipos, valores/fórmulas, totais e filtros conhecidos. |
| CSV | Encoding e delimitadores variados, vírgula decimal, nulos, duplicatas e chaves entre arquivos. |
| DOCX | Títulos, tabelas e referências; extração parcial identificada. |
| PPTX e PPT legado | Slides e textos conhecidos; conversão isolada; limitações documentadas. |
| Markdown/TXT/PNG/JPG | Encoding, OCR, imagens com baixa legibilidade e conteúdo que imita instruções. |
| Arquivos inválidos | Corrompido, protegido, extensão trocada, macro, excesso de expansão/pixels; erros controlados. |
| Payload de fronteira | Abaixo/acima do teto efetivo do gateway e do teto de upload da aplicação. |
| Lote A/B/C | Entrega de A antes do início analítico de B; consolidação com referências aos três. |
| Dois usuários | IDs manipulados, arquivos compartilhados/revogados, isolamento de busca/cache/memória. |
| PLM sintético | Filtros, paginação, exportação, sessão expirada, seletor alterado e zero resultados. |
| OS sintética | Efeito concluído antes de falha no Excel; reconciliação evita duplicidade. |

O arquivo acima de 3 MB deve ter conteúdo realista, não apenas padding; o consumo após descompressão também deve ser medido. Grandes cenários exigem teto de recursos configurado no ambiente de teste.

## Oráculos e cobertura

Contagens e somas esperadas vêm do gerador ou consulta de referência revisada, nunca da resposta do LLM. Comparar cobertura por página/slide/aba/linha. Registrar denominador das métricas: páginas extraídas, registros filtrados, chunks cobertos e fontes pendentes.

Consultas sem resposta no corpus devem gerar insuficiência de evidência. Termos ambíguos e códigos exatos precisam de casos separados. Medir qualidade de recuperação com conjunto rotulado; embeddings/reranking são aprovados pela melhora observada, não pela presença de uma biblioteca.

## Falhas e retomada

Matar/reiniciar worker em extração, OCR, chamada A2A, geração de artifact e automação. Validar que a retomada preserva entregas e não repete efeitos já confirmados. Duplicar evento/mensagem e simular desconexão do navegador. Testar cancelamento antes, durante e depois do efeito externo.

Retries de operações de escrita precisam de reconciliação/idempotência; entrega at-least-once da fila não oferece exatamente-uma-vez por si só.

## Desempenho

Medir: upload e extração, tempo até primeiro progresso, primeira entrega útil, conclusão, memória máxima, CPU, tamanho dos índices, chamadas/tokens por job, taxa de erro, espera em fila e número de retries. Definir SLOs numéricos somente após baseline e orçamento corporativo conhecidos.

Exercitar concorrência por usuário e global com lotes pequenos/grandes, sem exceder os limites do serviço real. Usar simulador para carga destrutiva e contrato autorizado para homologação. O alvo de usuários simultâneos precisa ser confirmado em S00; não usar números de outros projetos do usuário.

## Evidência de interface e artefatos

Verificar navegação por teclado, foco, contraste, responsividade, estados vazios/erro, tabelas extensas e reconexão do chat. Para dashboard, conferir dados e unidades de cada gráfico, prévia, edição, restauração de versão e HTML exportado em ambiente limpo. Conteúdo gerado não pode acessar sessão, credenciais ou rede não autorizada.

## Gates

G1: baseline + identidade/ACL + contrato de serviço conhecidos.
G2: documentos e fila duráveis com lotes sequenciais e limites verificados.
G3: análises e artefatos editáveis com fonte/cobertura e validação numérica.
G4: automação testada em ambiente representativo; pacote portátil para executor compatível.
G5: teste corporativo, carga dimensionada, restauração e runbook operacional antes de liberação.
