# Backlog do Produto

## Visão geral

Este backlog transforma as histórias de usuário em itens priorizados para o desenvolvimento do Weather App. A priorização considera impacto na experiência principal, esforço de implementação e relevância para usuários móveis.

## Prioridade 1 - Core do produto

### US-01: Busca de cidade
- História: Como Maria, profissional urbana, quero pesquisar a cidade onde trabalho para consultar rapidamente o clima atual e decidir como me deslocar.
- Priorização: Alta
- Critérios de aceitação:
  - O usuário pode digitar o nome de uma cidade em um campo de busca.
  - O sistema apresenta até 5 resultados relevantes em ordem de correspondência.
  - O usuário consegue selecionar uma cidade da lista.
  - Quando não há resultado, o sistema exibe a mensagem “Nenhuma cidade encontrada”.
  - A busca funciona em telas mobile e desktop.
- Tarefas técnicas:
  - Criar componente de campo de busca com label acessível.
  - Implementar lógica de filtro e ordenação dos resultados da API de geocodificação.
  - Criar estado de loading, erro e vazio para as buscas.
  - Integrar a API Open-Meteo de geocodificação.
  - Validar acessibilidade do campo com foco visível e teclado.

### US-02: Clima atual
- História: Como Maria, profissional urbana, quero visualizar a temperatura, a umidade e a velocidade do vento para planejar minha rotina sem precisar abrir outros apps.
- Priorização: Alta
- Critérios de aceitação:
  - Após selecionar uma cidade, a aplicação exibe o clima atual.
  - A tela apresenta temperatura, descrição do clima, ícone, umidade e velocidade do vento.
  - Os dados são atualizados imediatamente ao trocar a cidade.
  - O layout mantém legibilidade em mobile.
- Tarefas técnicas:
  - Criar componente de card de clima atual.
  - Integrar endpoint de clima atual da API Open-Meteo.
  - Mapear dados da API para modelos internos.
  - Definir estado de carregamento e erros de rede.
  - Garantir responsividade do layout em telas pequenas.

### US-03: Previsão de 5 dias
- História: Como Ana, mãe de família, quero ver a previsão dos próximos 5 dias para planejar roupas, passeios e atividades externas com o restante da família.
- Priorização: Alta
- Critérios de aceitação:
  - A aplicação mostra previsão para os próximos 5 dias.
  - Cada dia exibe data, descrição do clima, temperatura máxima e mínima.
  - A tela é clara e comparável entre os dias.
  - A informação permanece legível em celulares.
- Tarefas técnicas:
  - Implementar componente de previsão diária.
  - Integrar API de previsão de 5 dias.
  - Criar estrutura visual com cards ou lista comparável.
  - Tratar dias com dados ausentes ou falhas em requisição.
  - Validar contraste e leitura em mobile.

### US-04: Alternância de unidade
- História: Como Carlos, estudante em viagem curta, quero alternar a unidade de temperatura entre Celsius e Fahrenheit para entender as condições climáticas de acordo com minha preferência.
- Priorização: Alta
- Critérios de aceitação:
  - O usuário consegue alternar entre °C e °F por meio de controle visível.
  - Todas as temperaturas exibidas são convertidas imediatamente.
  - A troca não recarrega a página.
  - A unidade escolhida é aplicada a todas as seções da interface.
- Tarefas técnicas:
  - Centralizar conversão de temperatura em função reutilizável.
  - Implementar toggle de unidade na interface.
  - Atualizar os valores exibidos em clima atual e previsão.
  - Validar conversões com casos de borda.
  - Garantir que o componente tenha área mínima de toque de 44x44px.

### US-05: Tratamento de estados da aplicação
- História: Como Ana, mãe de família, quero receber mensagens de erro e carregamento adequadas para saber se a aplicação está funcionando e tentar novamente quando necessário.
- Priorização: Alta
- Critérios de aceitação:
  - Enquanto os dados são carregados, o usuário vê indicador visual de progresso.
  - Em falha de rede, a interface exibe mensagem de erro com ação de tentar novamente.
  - Quando não houver resultado, a interface mostra estado vazio amigável.
  - A aplicação não quebra o layout em nenhum desses estados.
- Tarefas técnicas:
  - Criar estados de loading, erro e vazio reutilizáveis.
  - Implementar tratamento de erro na camada de serviço.
  - Exibir mensagem com botão de retry.
  - Garantir que a UI continue estável quando a API falha.
  - Testar cenários sem internet e sem resultado.

## Prioridade 2 - Experiência e conveniência

### US-06: Comparação rápida entre cidades
- História: Como Carlos, estudante em viagem curta, quero buscar cidades diferentes para comparar o clima de cada destino antes de sair de casa.
- Priorização: Média
- Critérios de aceitação:
  - O usuário pode pesquisar mais de uma cidade em sequência.
  - O sistema mostra os dados da cidade atualmente selecionada sem perda de contexto.
  - A interface facilita comparação visual de clima atual e previsão.
- Tarefas técnicas:
  - Reutilizar o fluxo de busca e seleção para múltiplas cidades.
  - Ajustar componente de resultado para manter contexto da cidade atual.
  - Garantir que a troca de cidade atualize toda a tela corretamente.

### US-07: Planejamento do dia com base na previsão
- História: Como Maria, profissional urbana, quero consultar a previsão dos próximos 5 dias para saber se preciso levar guarda-chuva ou roupa adequada ao trabalho.
- Priorização: Média
- Critérios de aceitação:
  - A previsão deve descrever de forma clara as condições do clima para cada dia.
  - O usuário entende a tendência geral do período com facilidade.
  - Os dados permanecem acessíveis em poucos segundos.
- Tarefas técnicas:
  - Criar resumo visual da previsão por dia.
  - Definir labels amigáveis para a descrição do clima.
  - Melhorar legibilidade em mobile com espaçamento e hierarquia visual.

### US-08: Leitura fácil em celular
- História: Como Ana, mãe de família, quero acessar a previsão em um celular com interface simples e legível para consultar o clima rapidamente enquanto cuida da rotina.
- Priorização: Média
- Critérios de aceitação:
  - A interface se adapta a telas de 320px a 768px.
  - Os elementos interativos possuem área mínima de toque adequada.
  - Não é necessário zoom manual para leitura.
- Tarefas técnicas:
  - Adotar abordagem mobile-first no layout.
  - Ajustar espaçamento, fontes e breakpoints.
  - Validar área mínima do toque nos principais botões.
  - Testar em diferentes larguras de tela.

### US-09: Suporte a diferentes preferências de temperatura
- História: Como Maria, profissional urbana, quero alternar entre °C e °F para entender o clima da forma que me for mais confortável.
- Priorização: Média
- Critérios de aceitação:
  - A interface expõe a conversão de forma clara e visível.
  - O usuário troca a unidade sem esforço.
  - O valor convertido é consistente em todas as seções.
- Tarefas técnicas:
  - Criar toggle com estados visualmente distintos.
  - Aplicar a conversão de forma global.
  - Validar consistência entre clima atual e previsão.

### US-10: Mensagens amigáveis de busca vazia
- História: Como Carlos, estudante em viagem curta, quero receber uma mensagem clara quando não houver resultados na busca para continuar a pesquisa sem perder tempo.
- Priorização: Média
- Critérios de aceitação:
  - A mensagem aparece quando o resultado não existe.
  - O texto é claro e orienta a ação seguinte.
  - O layout não fica quebrado com o estado vazio.
- Tarefas técnicas:
  - Definir mensagem padronizada de ausência de resultados.
  - Implementar componente de estado vazio.
  - Validar comportamento em diferentes tipos de busca.

## Prioridade 3 - Refinamento e qualidade

### US-11: Acessibilidade
- História: Como Maria, profissional urbana, quero acessar a previsão em meu celular com leitura fácil para tomar decisões rápidas no caminho entre casa e o escritório.
- Priorização: Baixa
- Critérios de aceitação:
  - Elementos interativos possuem foco visível.
  - A aplicação é navegável por teclado.
  - O contraste atende aos critérios mínimos de acessibilidade.
- Tarefas técnicas:
  - Revisar contraste em componentes e textos.
  - Garantir labels semânticas em inputs e botões.
  - Validar navegação por teclado.
  - Executar testes de acessibilidade básicos.

### US-12: Recuperação de erro
- História: Como Carlos, estudante em viagem curta, quero usar a aplicação em meu smartphone com layout responsivo para consultar o clima rapidamente em qualquer lugar.
- Priorização: Baixa
- Critérios de aceitação:
  - Falha de rede ou indisponibilidade da API é tratada sem travar a interface.
  - O usuário consegue tentar novamente.
  - O estado em erro é claro e não quebra a navegação.
- Tarefas técnicas:
  - Melhorar tratamento de exceções na integração.
  - Exibir feedback de recuperação com botão de retry.
  - Validar comportamento em conexões lentas ou indisponíveis.

### US-13: Experiência consistente em mobile
- História: Como Ana, mãe de família, quero receber mensagens de erro e carregamento adequadas para saber se a aplicação está funcionando e tentar novamente quando necessário.
- Priorização: Baixa
- Critérios de aceitação:
  - A experiência do usuário é consistente em diferentes dispositivos.
  - Os principais elementos interativos possuem boa ergonomia no toque.
  - A interface evita elementos pequenos ou difíceis de pressionar.
- Tarefas técnicas:
  - Ajustar tamanho de botões e espaçamento.
  - Revisar componentes críticos em mobile.
  - Validar com testes de usabilidade em smartphones.

## Sequenciamento sugerido

1. US-01: Busca de cidade
2. US-02: Clima atual
3. US-03: Previsão de 5 dias
4. US-04: Alternância de unidade
5. US-05: Tratamento de estados
6. US-06: Comparação rápida entre cidades
7. US-07: Planejamento do dia
8. US-08: Leitura fácil em celular
9. US-09: Suporte a diferentes preferências de temperatura
10. US-10: Mensagens amigáveis de busca vazia
11. US-11: Acessibilidade
12. US-12: Recuperação de erro
13. US-13: Experiência consistente em mobile

## Observações técnicas para o projeto

- Separar componentes da interface em `src/components/`.
- Isolar acessos à API em `src/services/`.
- Centralizar tipos em `src/types/`.
- Usar funções puras para conversão de temperatura e mapeamento de dados.
- Priorizar desenvolvimento mobile-first, com foco em leitura e toque.
- Garantir cobertura de testes para busca, clima atual, previsão e conversão de unidades.
