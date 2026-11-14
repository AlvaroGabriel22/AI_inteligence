# ADR-001 — Preservação do projeto e ponto de partida

- Estado: proposta; depende da confirmação do código existente.
- Data: 13/11/2026 (America/Manaus).
- Sprint: S00.

## Contexto e evidências

A inspeção de `/home/alvaro/Documentos/AI_Inteligence` encontrou 40 arquivos,
todos no pacote `docs/sprints`, sem código de aplicação, manifest, lockfile,
configuração executável ou testes. O diretório existe e está acessível.
O repositório Git descoberto pertence ao diretório pai
`/home/alvaro/Documentos`; contém trabalhos de outros projetos que não fazem
parte desta entrega. Não inicializar, limpar, restaurar ou publicar esse
repositório como se fosse exclusivo de AI Inteligence.

O planejamento pressupõe um chat A2A já existente, mas declara que não houve
inspeção durante sua elaboração. O usuário solicitou iniciar o desenvolvimento
e informou que a API oficial ainda não será disponibilizada. Isso permite
trabalhar com simuladores identificados, sem escolher ou chamar um provedor
externo substituto.

## Alternativas consideradas

1. Localizar o código existente a partir de um caminho fornecido pelo usuário:
   preserva R01 e permite decidir a stack a partir de evidências reais.
2. Iniciar uma aplicação nesta pasta após corrigir a premissa com o usuário:
   mantém o planejamento como referência, mas exige registrar stack, persistência
   e limites da primeira entrega em outra decisão.

Criar uma aplicação concorrente antes de esclarecer a premissa pode duplicar
trabalho e romper a compatibilidade que o plano exige.

## Decisão proposta

Preservar o planejamento, registrar o baseline e esclarecer se o chat está em
outro caminho ou se a implementação deve começar aqui do zero. Nenhum dado
corporativo ou credencial é necessário para essa confirmação.

A ausência da API oficial será tratada separadamente: contrato interno de
provedor e simulador determinístico explicitamente identificado; nenhuma
simulação será apresentada como análise real ou homologação corporativa.
Não inventar endpoints, headers ou schemas do gateway.

## Consequências e recuperação

As mudanças de baseline são apenas documentação dentro do projeto. Não há
migração de dados nem alteração em código anterior. S01 terá ponto de partida
concreto após resolver a localização/premissa; então a decisão poderá ser aceita
ou substituída com referência à confirmação do usuário. Publicação e contratação
de infraestrutura não fazem parte deste início local.
