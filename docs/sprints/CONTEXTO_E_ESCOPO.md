# AI Inteligence — contexto e escopo do produto

Versão do planejamento: 1.0. Data: 13/11/2026, America/Manaus.

## Origem e estado real

Este planejamento consolida os requisitos informados por Álvaro. A aplicação já possui um chat que envia anexos a um agente por um gateway corporativo A2A e recebe análises e traduções. O código, a infraestrutura, o gateway e os sistemas internos NÃO foram inspecionados durante a elaboração destes documentos. Nenhuma sprint foi implementada ou homologada por este pacote.

Destino solicitado na máquina do usuário: `/home/alvaro/Documentos/AI_Inteligence/docs`. O ambiente que elaborou o pacote não possui esse diretório montado. O ZIP entrega `docs/sprints/` para instalação na raiz real do projeto, sem substituir arquivos da aplicação. S00 deve confirmar o caminho e a estrutura reais.

## Visão

Uma plataforma corporativa com chat como interface principal, contas e sessões individuais, biblioteca persistente, memória controlável, análise de arquivos, criação de apresentações e dashboards HTML editáveis e automação de sistemas web e desktop. A plataforma busca dados quando o usuário não dispõe do arquivo e aproveita o mesmo pipeline para anexos manuais e arquivos coletados.

O código executa o máximo do trabalho verificável: extração, OCR, estruturação, indexação, filtros, cálculos, consultas, fila, execução de ações e validações. A IA interpreta solicitações, planeja ações permitidas, interpreta evidências e redige ou organiza conteúdos. O resultado precisa indicar fontes, cobertura e limitações observadas.

## Requisitos rastreáveis

| ID | Requisito aceito |
| --- | --- |
| R01 | Preservar e evoluir o chat existente; inventariar antes de substituir qualquer componente. |
| R02 | Login, logout, recuperação de acesso ou SSO conforme ambiente; isolamento efetivo por usuário e permissões. |
| R03 | Sessões persistentes, histórico, busca de conversas, cancelamento e recuperação do andamento. |
| R04 | Biblioteca de originais, arquivos derivados, projetos visuais, resultados e automações, com versões e compartilhamento explícito. |
| R05 | Upload acima de 3 MB dentro dos limites configurados da plataforma; nunca transmitir payload incompatível com o gateway. |
| R06 | XLSX, DOCX, PDF, CSV, PPT/PPTX, Markdown, TXT, PNG e JPG/JPEG; OCR e identificação de formatos problemáticos. |
| R07 | Analisar arquivos de um lote sequencialmente; entregar o resultado útil do arquivo atual antes de iniciar a análise do próximo. |
| R08 | Trabalho pesado por código; cálculos sobre o universo de dados aplicável e sem depender da aritmética do LLM. |
| R09 | RAG, chunks, embeddings e busca lexical/semântica conforme a tarefa; referências a páginas, slides, seções e células. |
| R10 | Orçamento de contexto, requisições e recursos; filas duráveis, retomada, limites de concorrência e tratamento de timeout. |
| R11 | Mostrar etapas reais e entregas parciais identificadas; consolidar somente após cobrir as dependências necessárias. |
| R12 | Memória de preferências e conhecimentos reutilizáveis, com escopo, origem, validade e possibilidade de apagar. |
| R13 | Chat com tabelas, listas, Markdown, fluxogramas, código copiável, gráficos e prévias de artefatos. |
| R14 | Criar apresentações e dashboards HTML com dados rastreáveis, cards, gráficos, temas e layouts. |
| R15 | Editar artefatos pelo chat e por controles visuais, salvar versões e exportar projeto editável e HTML. |
| R16 | Seletor de PLM, GMQIS e GMES no compositor; no máximo um sistema selecionado por solicitação. |
| R17 | Executor web com autenticação autorizada, filtros, navegação, downloads e retomada. |
| R18 | Executor desktop no ambiente compatível; apps nativos, documentos e terminal quando necessário e permitido. |
| R19 | Construção e edição de automações por conversa, com perguntas, loops, condições, parâmetros e validação. |
| R20 | Exportar/importar automações versionadas e compartilhar pacotes sem transportar credenciais. |
| R21 | Catálogo de prompts prontos, guias e central de automações compartilhadas. |
| R22 | Compatibilidade com o gateway A2A corporativo descrito; continuidade, polling, cancelamento e artifacts. |
| R23 | Rastreabilidade, métricas, testes de carga, backup/restauração e operação corporativa. |
| R24 | Busca pontual em sistemas internos sem obrigar o usuário a criar ou salvar uma automação. |

## Jornadas de referência

1. Usuário envia três arquivos grandes; recebe a análise do primeiro, depois do segundo, depois do terceiro e a consolidação pertinente.
2. Usuário pede tradução integral de PDF longo: todas as páginas aplicáveis são cobertas; páginas ilegíveis ficam explicitamente identificadas.
3. Usuário envia planilhas e pede cards e gráfico de barras em azul: código calcula, IA organiza, usuário edita e exporta.
4. Usuário seleciona PLM e pede defeitos SW de modelo/período: executor consulta, valida, coleta e alimenta o chat.
5. Usuário ensina um processo por conversa; agente pergunta o que falta, testa, salva e exporta um fluxo reutilizável.
6. Planilha contém códigos para criação de OS: cada linha tem progresso; criação concluída seguida de falha na escrita do Excel não provoca OS duplicada na retomada.

## Limites do compromisso

- O sistema terá limites de tamanho, páginas, registros, pixels, tempo e armazenamento dimensionados; aceitar acima de 3 MB não significa volume ilimitado.
- Não prometer operação universal em qualquer aplicação desconhecida. Cada capacidade deve ter ambiente, pré-condições e validações explícitas.
- A2A é o contrato de comunicação com agentes. O backend e os executores implementam coordenação, persistência e ações locais.
- O serviço A2A não foi comprovado como provedor de embeddings, visão ou tool calling. Essas capacidades precisam de contrato testado ou componente separado aprovado.
- Dados corporativos devem permanecer em infraestrutura e provedores autorizados. A escolha de cloud pública não foi autorizada como requisito deste projeto.
- As sprints cobrem o produto completo. PLM é uma integração de referência, não uma redução do escopo.
