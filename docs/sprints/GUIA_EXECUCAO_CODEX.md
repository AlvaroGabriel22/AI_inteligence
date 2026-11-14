# Guia de execução para Codex

## Perfil pretendido

O usuário pediu desenvolvimento guiado pelo Codex Astra-6, esforço extra alto. Selecionar esse perfil na interface onde ele estiver disponível. Este arquivo não muda o modelo em execução e não inventa identificadores de configuração. Se o rótulo disponível for diferente, registrar o perfil efetivamente utilizado.

## Leitura inicial

1. Ler as instruções aplicáveis do repositório (`AGENTS.md` e equivalentes), este guia, [escopo](CONTEXTO_E_ESCOPO.md), [arquitetura](ARQUITETURA.md) e [status](STATUS.md).
2. Abrir a sprint solicitada e as referências específicas. Não carregar toda a documentação no contexto a cada turno.
3. Inspecionar estado do git, arquivos existentes e trabalhos em andamento. Preservar alterações não relacionadas e componentes que já funcionam.
4. Conferir dependências da sprint e evidências anteriores. Um checkbox sem evidência não comprova conclusão.

## Ciclo de trabalho

1. Descrever brevemente a entrega concreta e os módulos a alterar.
2. Inventariar pontos necessários do código usando buscas focadas. Escolher a menor alteração que atenda a arquitetura e o escopo.
3. Executar a sprint de ponta a ponta: banco, serviço, contrato, interface, testes e documentação pertinentes.
4. Usar testes com dados sintéticos e contratos saneados; manter fixtures de simuladores separadas de evidências reais.
5. Verificar o fluxo inteiro no ambiente disponível. Validar limites, isolamento e falhas relevantes além do caminho feliz.
6. Registrar resultado em `evidencias/SXX.md`, com comandos executados, resultados observados, limitações e arquivos alterados. Atualizar `STATUS.md` e `plano.json` coerentemente.
7. Ao atingir o critério de saída, encerrar com resultado, validação e próximo passo. Executar outra sprint somente quando a instrução do usuário abranger essa continuação.

## Autonomia e bloqueios

- Decisões reversíveis de implementação dentro da sprint são responsabilidade do agente; não pedir confirmação para cada edição, teste ou correção.
- Pedir informação somente quando faltar um dado indispensável que não esteja no código, configuração segura ou documentação acessível. Continuar partes independentes enquanto isso.
- A ausência de credencial real pode bloquear a homologação externa, mas não a implementação e os testes de contrato disponíveis. Registrar claramente `AGUARDANDO_HOMOLOGACAO`.
- Não pedir tokens no chat nem gravá-los em documentação, código, logs ou fixtures. Ler de configuração segura na máquina autorizada.
- Não publicar, fazer push, migrar produção ou realizar operações de negócio reais fora da autorização da sessão. Não exigir nova autorização para ações já autorizadas.
- Não apagar dados, refazer o projeto inteiro ou trocar a stack somente por preferência. Mudanças estruturais precisam de diagnóstico, plano de migração e ADR.
- Não declarar pronto o que foi apenas simulado. Não concluir testes que não foram executados. Não substituir resultados reais por mocks no modo de produção.
- Não escolher frameworks, bibliotecas ou versões por memória: conferir a documentação oficial da versão selecionada e o lockfile.
- Evitar agentes paralelos modificando as mesmas áreas. Este plano não exige delegação nem autoriza sua utilização por si só.

## Definição de pronto comum

- Resultado demonstrável e compatível com a versão atual da aplicação.
- Requisitos da sprint rastreados, permissões verificadas no backend e configurações documentadas.
- Migrações com procedimento de recuperação quando houver alteração de dados.
- Testes significativos para a mudança; sem testes que apenas reproduzem a implementação.
- Sem dados sintéticos apresentados como produção; sem segredos; sem regressões conhecidas ocultadas.
- Jobs e artefatos possuem estado persistente e evidência verificável quando aplicável.
- Relatório de sprint com limitações reais e referência à próxima dependência.

## Estados

`PLANEJADA` → `EM_ANDAMENTO` → `IMPLEMENTADA` → `HOMOLOGADA`.

`BLOQUEADA` identifica dependência indisponível; `AGUARDANDO_HOMOLOGACAO` identifica código validado localmente cuja dependência externa ainda não foi comprovada. `IMPLEMENTADA` não equivale a pronta para produção. A trilha principal avança somente com dependências necessárias satisfeitas ou com interfaces simuladas explicitamente isoladas.

## Evidência e contexto

Manter resumos operacionais curtos nos relatórios. Não registrar raciocínio interno da IA. Guardar decisões, ações, fontes, resultados, métricas e erros relevantes. Persistência da conversa não elimina limites de contexto; o código monta o contexto necessário a cada trabalho.
