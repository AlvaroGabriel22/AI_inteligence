# Prompt inicial para o Codex

Abra a pasta `/home/alvaro/Documentos/AI_Inteligence` no Codex. Selecione na interface o modelo/perfil Astra-6 com esforço extra alto, caso disponível. Depois envie:

```text
Vamos desenvolver a plataforma AI Inteligence usando o planejamento em docs/sprints.
O projeto já possui um chat integrado ao gateway corporativo A2A. Preserve o que existe e inspecione antes de decidir mudanças de stack ou arquitetura.

Leia as instruções aplicáveis do repositório e estes documentos:
- docs/sprints/README.md
- docs/sprints/GUIA_EXECUCAO_CODEX.md
- docs/sprints/CONTEXTO_E_ESCOPO.md
- docs/sprints/ARQUITETURA.md
- docs/sprints/STATUS.md
- docs/sprints/S00_inventario_baseline.md

Execute a S00 de ponta a ponta. Verifique o código real, o fluxo de análise atual, a persistência, a interface, as integrações e os testes. Registre o que deve ser mantido, adaptado e acrescentado para atender ao escopo completo.
Não invente contratos do gateway ou acesso aos sistemas internos. Nunca exponha segredos. Não crie uma aplicação nova por falta de inspeção da existente.
Faça escolhas reversíveis autonomamente e continue nas partes independentes quando faltar informação. Pergunte somente pelo que for indispensável e não puder ser obtido do projeto.
Produza evidencias/S00.md, atualize STATUS.md e plano.json e indique a próxima sprint elegível, diferenciando testes executados de homologações pendentes.
```

## Continuar uma sprint por vez

```text
Execute a próxima sprint elegível de docs/sprints conforme STATUS.md, plano.json e evidências existentes. Leia o arquivo completo da sprint, implemente seu escopo de ponta a ponta, valide critérios e registre o resultado. Preserve o código e alterações não relacionadas. Não declare concluído o que não foi testado.
```

## Retomar após interrupção

```text
Retome o trabalho a partir de docs/sprints/STATUS.md e do último relatório em docs/sprints/evidencias. Confira o estado real do código e dos testes antes de atualizar o plano. Continue a sprint em andamento sem repetir operações externas já confirmadas.
```
