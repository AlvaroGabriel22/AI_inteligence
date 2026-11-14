# Contrato corporativo A2A: confirmar antes de integrar

## Informações fornecidas pelo usuário

| Item | Informação e grau de certeza |
| --- | --- |
| Protocolo | A2A 1.0, JSON-RPC; gateway expõe quatro métodos. Nomes e schemas exatos ainda precisam de documentação/AgentCard. |
| Versão | Header de versão 1.0 obrigatório; confirmar grafia em exemplo saneado. |
| Autenticação | Dois tokens proprietários; rótulos informados aproximadamente como `x-generative-ai-client` e `x-openapi-token` com Bearer. Confirmar nomes e formato exatos. Não é OAuth. |
| Identidade | Header de e-mail corporativo foi citado com grafia imprecisa; confirmar. Derivar identidade do usuário autenticado, nunca confiar em e-mail livre enviado pelo cliente. |
| Rede | Acesso pela rede corporativa obrigatório. |
| Continuidade | Quando pede entrada, continuar no mesmo taskId e contextId; histórico mantido pelo serviço. |
| Acompanhamento | GetTask/polling no ciclo assíncrono; SSE citado; sem push notifications. |
| Cancelamento | CancelTask disponível; schema e semântica a validar. |
| Arquivos de entrada | Base64 em parts, até cinco arquivos, até 3 MB cada; formatos corporativos precisam ser confirmados. |
| Saída | Inline nos artifacts; não inferir que o teto de entrada também é o de saída. |
| Timeout | Configurável por request até máximo do ambiente, exemplo 3600 s. Confirmar valor real em documentação/AgentCard quando publicado. |
| SDK | SDK oficial ainda não testado nesse gateway. Testar compatibilidade e possibilidade de headers/transporte customizados. |

Não transformar os exemplos aproximados do usuário em código de produção. O adaptador deve receber nomes de headers, métodos e limites confirmados por configuração segura ou contrato versionado. Não confundir versão do pacote SDK com versão do protocolo.

## Evidências mínimas a coletar

Endpoint/base URL, AgentCard se disponível, exemplos saneados de envio simples, resposta imediata, tarefa assíncrona, continuação, erro, cancelamento, entrada de arquivo e artifact. Registrar limites de payload total, bytes antes/depois de base64, tempo, taxa e concorrência. Se um limite não for publicado, negociar teste seguro e registrar o valor provisório conservador.

Verificar suporte real a imagens/visão, saída estruturada, uso de ferramentas e embeddings separadamente. A existência do protocolo A2A não confirma nenhuma dessas capacidades de IA.

## Adaptador isolado

Interface interna sugerida: enviar mensagem/tarefa, consultar tarefa, continuar tarefa aguardando entrada, solicitar cancelamento e consumir eventos quando suportado. São operações internas, não nomes presumidos do JSON-RPC do gateway.

Centralizar construção de envelopes, validação, secrets, timeout e saneamento de erros. Nunca adicionar headers proprietários em todos os módulos. Usar SDK oficial se o contrato comprovado for atendido; divergências exigem adaptador explícito e testes, sem fork precipitado do SDK.

## Regras de continuidade e orçamento

- `input-required` e rótulos equivalentes dependem do schema real: mapear para estado interno; não adivinhar casing/enum.
- Manter taskId/contextId da tarefa que espera resposta. Não reutilizar uma tarefa terminal para novo trabalho; criar uma tarefa relacionada conforme o contrato.
- Cada arquivo ou etapa pode ter sua própria tarefa. A continuidade do produto é mantida no job local e não depende de acumular todos os arquivos em um contexto remoto ilimitado.
- Reservar orçamento para instruções, dados recuperados, memória, histórico e resposta. Reduzir contexto somente com rastreabilidade da cobertura.
- Medir bytes do payload final e tokens estimados. Base64 aumenta tamanho em aproximadamente um terço, além do JSON; validar o limite efetivamente contratado.
- Polling com intervalo configurável, teto de chamadas, backoff e jitter quando adequado. Não usar push notifications nem métodos ausentes do gateway.
- Reconexão SSE não pode duplicar eventos nem recomeçar a tarefa. GetTask reconcilia o estado quando necessário.
- Timeout de uma chamada, prazo da tarefa remota e prazo do job são limites diferentes. Ao perder uma resposta, consultar/reconciliar antes de reenviar uma operação com possível efeito.
- Cancelamento solicitado não é cancelamento confirmado. Persistir a intenção, consultar o estado e reportar se uma operação já ocorreu.

## Falhas a testar

401/403, credencial expirada, rede indisponível, 429, 5xx transitório, JSON-RPC error em HTTP 200, schema inesperado, artifact base64 inválido, limite de bytes, resposta truncada, desconexão SSE, tarefa não encontrada, cancelamento não aceito e timeout após aceitação remota.

Simulador serve para engenharia; homologação exige resposta real no ambiente corporativo. Nunca registrar tokens ou conteúdo confidencial como evidência pública.
