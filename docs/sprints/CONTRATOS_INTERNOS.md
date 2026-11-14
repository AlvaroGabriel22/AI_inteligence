# Contratos internos propostos

Estes contratos são do produto. Não são schemas oficiais do A2A e não devem ser enviados diretamente ao gateway. S01/S04 convertem esta proposta em modelos compatíveis com a aplicação real.

## Entidades mínimas

| Entidade | Campos/responsabilidades essenciais |
| --- | --- |
| User/Session | Identidade, permissões, sessões autenticadas e revogação. |
| Conversation/Message | Dono/ACL, mensagens, anexos, referências a jobs e artefatos; histórico persistente. |
| File/DocumentVersion | Hash, original, MIME, tamanho, versão, origem, política de acesso e retenção. |
| ExtractedUnit/Dataset | Conteúdo estruturado, página/slide/aba/célula, tipos, cobertura e qualidade. |
| Chunk/Embedding | Documento e versão, intervalo de origem, modelo/dimensão, ACL e status de indexação. |
| Job/Step | Solicitante, plano, estado, orçamento, checkpoints, tentativas e vínculos A2A. |
| Event | Sequência por job, tipo, timestamp, payload saneado e versão de schema. |
| Artifact/ArtifactVersion | Tipo, versão, conteúdo/projeto, fontes, validações e permissão de compartilhamento. |
| Memory | Escopo, origem, validade, versão, confiança e exclusão/revogação. |
| SystemConnection | Sistema, ambiente, acesso autorizado e referência de segredo. |
| AutomationDefinition/Version | Parâmetros, etapas, condições, loops, pré-condições e requisitos do executor. |
| AutomationRun/Checkpoint | Versão executada, dados da instância, efeitos confirmados e recuperação. |

## Job durável

Estados internos sugeridos: `queued`, `running`, `waiting_input`, `waiting_auth`, `cancel_requested`, `canceled`, `failed`, `completed`. São independentes dos enums do gateway. Persistir transições com concorrência controlada; erro de um step não pode causar conclusão falsa do job.

Cada evento tem ID/ordem estável. Exemplo conceitual:

```json
{
  "schema_version": "1",
  "job_id": "job_exemplo",
  "sequence": 12,
  "type": "partial_result_ready",
  "file_position": 1,
  "file_total": 3,
  "artifact_id": "art_exemplo",
  "provisional": true,
  "coverage": {"files_completed": 1, "files_total": 3}
}
```

O exemplo não representa uma execução real. Eventos não carregam segredos nem raciocínio interno. Reabrir o chat deve recuperar o snapshot e eventos posteriores sem duplicar mensagens.

## Projeto visual editável

Salvar um modelo estruturado com versão de schema, tema, páginas/slides, componentes, configurações e vínculos com datasets/consultas. Componentes permitidos incluem texto, card, tabela e gráficos especificados. Valores e séries precisam apontar a dados validados; textos explicativos têm fontes quando aplicável.

Mudanças pelo chat são patches validados e revisionados. Edição visual preserva o modelo e os vínculos de dados. HTML exportado é uma saída; o projeto editável mantém a estrutura necessária para futuras edições. Pacote offline deve incluir dependências necessárias ou informar claramente suas dependências externas.

## Pacote de automação

Formato inicial proposto: ZIP validado, com `manifest.json`, definição estruturada do fluxo, código necessário, dependências declaradas e documentação de uso. O nome/extensão comercial pode ser definido depois. Não é um formato universal já existente.

O manifest declara versão do schema e da automação, entradas/saídas, sistema alvo, SO/runtime compatíveis, permissões e referências de conexão. Loops são lógica parametrizada, não milhares de cliques expandidos. Credenciais, cookies, tokens, históricos e dados de execuções anteriores ficam fora do pacote por padrão.

Importar deve validar paths, tamanho, versão e dependências; não executar automaticamente. Na mesma plataforma, compartilhar uma definição não exige baixar/reimportar. Em outro sistema, o executor/API compatível precisa existir uma vez antes da experiência de executar com um clique.

## Validação comum

Schemas versionados; alterações incompatíveis exigem migração. IDs fornecidos pelo cliente sempre passam por autorização. Referências de arquivos, datasets, artefatos, memórias e conexões devem pertencer ao escopo do solicitante. Tamanho/payload não deve ser validado apenas na interface.
