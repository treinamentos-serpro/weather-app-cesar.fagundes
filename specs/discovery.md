# Discovery

## Contexto

A proposta do produto é desenvolver uma aplicação web de previsão do tempo com foco em usabilidade, rapidez e experiência mobile. O objetivo principal é permitir que o usuário consulte o clima de uma cidade de forma simples, sem necessidade de autenticação ou navegação complexa.

O brief indica que a solução deve cobrir as ações essenciais de busca, consulta do clima atual e visualização da previsão para os próximos cinco dias. Além disso, a aplicação deve oferecer conversão entre Celsius e Fahrenheit para atender diferentes preferências de usuários e garantir acessibilidade em dispositivos móveis.

A aplicação será usada por pessoas que desejam obter informações climáticas de forma imediata, em contextos cotidianos como planejamento de rotina, deslocamento e tomada de decisão rápida sobre vestuário ou atividades externas.

## Requisitos Funcionais

1. Busca de cidades
   - O usuário deve poder pesquisar uma cidade por nome por meio de campo de busca.
   - O sistema deve apresentar até 5 resultados relevantes em ordem de maior correspondência e permitir a seleção de um item da lista.
   - Quando não houver coincidência, o sistema deve exibir uma mensagem clara de ausência de resultados, como “Nenhuma cidade encontrada”.

2. Visualização do clima atual
   - Após a seleção de uma cidade, a aplicação deve exibir o clima atual correspondente.
   - A tela deve apresentar, no mínimo: temperatura atual, descrição da condição climática, ícone representativo, umidade relativa e velocidade do vento.
   - Os dados devem atualizar imediatamente após a troca de cidade ou da unidade de temperatura.

3. Previsão de 5 dias
   - A aplicação deve apresentar a previsão climática dos próximos 5 dias para a cidade selecionada.
   - Para cada dia, o sistema deve exibir a data, uma descrição resumida do clima, a temperatura máxima e a temperatura mínima.
   - A previsão deve ser apresentada em uma estrutura visual clara e comparável entre os dias.

4. Alternância entre Celsius e Fahrenheit
   - O usuário deve poder alternar a unidade de temperatura entre Celsius (°C) e Fahrenheit (°F) por meio de um controle visível na interface.
   - A conversão deve ser aplicada a todas as temperaturas exibidas na tela imediatamente, sem necessidade de recarregar a página.

5. Experiência mobile
   - A aplicação deve ser responsiva e adequada para uso em smartphones com telas de 320px a 768px de largura.
   - Os principais elementos interativos devem possuir área mínima de toque de 44x44px.
   - A interface deve manter legibilidade e acesso sem necessidade de zoom manual.

6. Tratamento de estados da aplicação
   - Durante a consulta de dados, a aplicação deve exibir um indicador de carregamento.
   - Em caso de falha de rede ou indisponibilidade da API, a interface deve apresentar uma mensagem de erro com a opção de tentar novamente.
   - Quando não houver resultados de busca, a interface deve exibir um estado vazio amigável e sem quebrar o layout.

## Requisitos Não-Funcionais

1. Usabilidade
   - A funcionalidade principal deve permitir que o usuário realize uma busca e visualize o clima em até 10 segundos em uma conexão estável.
   - O fluxo principal da aplicação deve ser simples: buscar cidade, consultar clima e alternar unidade de temperatura.

2. Responsividade
   - A interface deve funcionar corretamente em smartphones, tablets e desktops, adaptando o layout para diferentes larguras de tela.
   - A estrutura visual deve manter navegação, leitura e acessibilidade sem perda de funcionalidade.

3. Performance
   - As buscas e a renderização da previsão devem ocorrer em até 3 segundos em condições normais de rede.
   - A aplicação deve fornecer feedback visual imediato durante carregamento de dados.

4. Confiabilidade
   - O sistema deve tratar falhas de rede ou indisponibilidade de serviço sem travar a interface.
   - Em caso de erro, a aplicação deve exibir mensagem clara e manter o usuário em um estado recuperável.

5. Acessibilidade
   - A interface deve atender, no mínimo, às diretrizes WCAG 2.1 AA para contraste, foco visível e navegação por teclado.
   - Elementos interativos devem ser identificáveis e utilizáveis por usuários com tecnologias assistivas.

6. Manutenibilidade
   - O código deve manter separação entre componentes de interface, serviços de integração com API e modelos de dados.
   - A arquitetura deve facilitar futuras evoluções, como busca por geolocalização, histórico de cidades ou novos filtros de clima.

7. Segurança
   - A aplicação deve consumir APIs externas sem expor segredos, tokens ou credenciais no cliente.
   - Nenhuma informação sensível do usuário deve ser armazenada no front-end em sua primeira versão.

## Riscos

1. Dependência de uma API externa
   - Probabilidade: Alta
   - Impacto: Alto
   - Justificativa: a funcionalidade principal depende de um provedor externo, que pode sofrer indisponibilidade, latência ou variação de qualidade dos dados.
   - Mitigação: implementar fallback visual para erro, cache de respostas recentes, tratamento de timeout e indicação clara de falha ao usuário.

2. Ambiguidade na busca por cidade
   - Probabilidade: Média
   - Impacto: Médio
   - Justificativa: cidades com nomes repetidos ou buscas pouco específicas podem gerar resultados ambíguos e afetar a confiança do usuário.
   - Mitigação: definir regras de ordenação, exibir resultados com contexto regional e permitir filtros por país/estado quando aplicável.

3. Qualidade dos dados climáticos
   - Probabilidade: Média
   - Impacto: Médio
   - Justificativa: a previsão pode variar conforme a fonte, a localização e a atualização dos dados, reduzindo a percepção de confiabilidade do serviço.
   - Mitigação: usar fonte confiável, mostrar a data de atualização quando possível e evitar promessas excessivas sobre precisão local.

4. Problemas de usabilidade no mobile
   - Probabilidade: Média
   - Impacto: Alto
   - Justificativa: se a interface não for priorizada para dispositivos pequenos, o uso pode se tornar frustrante e pouco eficiente.
   - Mitigação: adotar abordagem mobile-first, validar com testes de usabilidade em smartphones e priorizar leitura, toque e navegação simplificada.

5. Erros na conversão de temperatura
   - Probabilidade: Média
   - Impacto: Médio
   - Justificativa: a conversão entre °C e °F pode gerar inconsistência visual ou erro de regra de negócio se a implementação for inadequada.
   - Mitigação: centralizar a lógica de conversão em uma função reutilizável, testar casos de borda e validar valor em diferentes unidades.

6. Escopo incompleto
   - Probabilidade: Média
   - Impacto: Alto
   - Justificativa: sem definição clara do público, do comportamento esperado e das fronteiras do produto, a solução pode ser entregue com funcionalidade insuficiente ou com excesso de escopo.
   - Mitigação: validar o entendimento do produto com stakeholders, registrar decisões em documentação e controlar mudanças de escopo durante desenvolvimento.

## Perguntas em Aberto (Open Questions)

1. A busca deve permitir apenas cidades ou também regiões, estados e países?
2. A aplicação deve incluir geolocalização automática com base na localização do usuário?
3. A previsão deve exibir apenas a previsão diária para 5 dias ou também dados horários?
4. A interface deve seguir um idioma específico e formato de data local conforme a localização do usuário?
5. Há preferência por um design visual específico, como tema claro ou dark mode?
6. A unidade de temperatura escolhida deve ser persistida entre sessões do usuário?
7. A aplicação deve mostrar alertas climáticos severos, como tempestades, neve ou calor extremo?
8. A primeira versão precisa suportar acessibilidade e uso em redes lentas como critérios obrigatórios?

## Análise de Impacto das Perguntas em Aberto

### 1. A busca deve permitir apenas cidades ou também regiões, estados e países?
- Impacto se permanecer sem resposta:
  - O produto pode receber buscas com resultados inconsistente ou pouco úteis.
  - A UI pode ser desenhada para um comportamento errado, gerando frustração do usuário.
  - A integração com a API pode ser subdimensionada ou superdimensionada para o tipo de busca esperado.
  - O time pode gastar esforço em filtros desnecessários ou ignorar geograficamente relevantes.

### 2. A aplicação deve incluir geolocalização automática com base na localização do usuário?
- Impacto se permanecer sem resposta:
  - O produto pode perder conveniência e diferenciação em relação a concorrentes.
  - A experiência mobile pode ficar menos fluida se a localização manual for obrigatória.
  - Pode haver risco de consentimento e privacidade, caso a geolocalização seja introduzida sem definição clara.
  - A arquitetura precisa decidir se haverá permissões de navegador, fallback para cidade manual e tratamento de erro de localização.

### 3. A previsão deve exibir apenas a previsão diária para 5 dias ou também dados horários?
- Impacto se permanecer sem resposta:
  - A interface pode ficar incompleta para usuários que precisam de um plano imediato do clima ao longo do dia.
  - A estrutura da API e do componente de dados pode ser inadequada, gerando retrabalho.
  - A experiência pode ser muito genérica para casos onde o usuário precisa decidir sobre a próxima hora ou o dia inteiro.

### 4. A interface deve seguir um idioma específico e formato de data local conforme a localização do usuário?
- Impacto se permanecer sem resposta:
  - O produto pode apresentar datas e textos em formatos inconsistentes para diferentes públicos.
  - A usabilidade cai quando o usuário não entende a ordem de dias, meses ou labels da interface.
  - Testes de UI e internacionalização podem ser mal planejados, com custo de manutenção maior.

### 5. Há preferência por um design visual específico, como tema claro ou dark mode?
- Impacto se permanecer sem resposta:
  - O design pode variar entre mockups, implementação e revisão sem padronização clara.
  - Há risco de retrabalho em estilos visuais, contraste, iconografia e ergonomia.
  - A decisão de tema pode impactar a percepção de qualidade do produto e a aderência ao briefing.

### 6. A unidade de temperatura escolhida deve ser persistida entre sessões do usuário?
- Impacto se permanecer sem resposta:
  - O usuário pode precisar redefinir a unidade toda vez que voltar ao app.
  - A experiência se torna inconsistente e menos profissional.
  - O time precisa decidir se o estado deve ficar em localStorage, memória do app ou ser reaplicado ao montar a tela.

### 7. A aplicação deve mostrar alertas climáticos severos, como tempestades, neve ou calor extremo?
- Impacto se permanecer sem resposta:
  - O produto pode ser considerado incompleto para cenários de uso real e risco à segurança do usuário.
  - A API pode ser usada apenas para previsão básica, sem alertas críticos.
  - Há risco de não atender necessidades de usuários em regiões expostas a condições extremas.

### 8. A primeira versão precisa suportar acessibilidade e uso em redes lentas como critérios obrigatórios?
- Impacto se permanecer sem resposta:
  - A experiência pode deixar fora usuários com necessidades especiais ou conectividade limitada.
  - O time pode priorizar apenas a funcionalidade principal e ignorar requisitos de inclusão e performance realista.
  - O projeto pode falhar em critérios de qualidade que influenciam reputação e aceitação do produto.
  - A arquitetura e a estratégia de carregamento podem se tornar inadequadas para cenários de rede lenta.

## Conclusão da Análise

As perguntas em aberto não são apenas detalhes de conveniência; elas influenciam diretamente a arquitetura, a experiência do usuário, os testes de aceitação e o esforço de implementação. Caso permaneçam sem resposta, a equipe corre risco de construir uma solução correta para o briefing genérico, mas inadequada para o cenário real de uso. Isso resulta em retrabalho, decisões ad hoc e maior chance de insatisfação do usuário final.

## Suposições (Assumptions)

1. A aplicação será desenvolvida como uma interface web responsiva, com foco em dispositivos móveis.
2. A integração será feita com uma API pública de clima, como Open-Meteo, sem necessidade de chave de acesso.
3. A busca será manual por nome da cidade, com seleção do resultado desejado.
4. O produto cobrará clima atual e previsão para 5 dias, sem necessidade de autenticação.
5. A alternância entre Celsius e Fahrenheit será funcionalidade obrigatória da interface.
6. A aplicação deve fornecer feedback claro para estados de loading, erro e vazio.
7. A solução não exigirá login ou cadastro para a versão inicial.
8. O foco principal será na experiência de consulta rápida e informativa, não em análise meteorológica avançada.

## Decisões

### 1. Fonte de dados: Open-Meteo
- Decisão: utilizar a API Open-Meteo como fonte de dados climáticos.
- Justificativa: a solução é gratuita, não exige API key, possui cobertura relevante para geocodificação e previsão e se alinha ao objetivo do projeto de prototipagem rápida.
- O que resolve: fecha a dependência técnica da fonte de dados e elimina a necessidade de autenticação específica do provedor, reduzindo atrito de implementação e risco de configuração.

### 2. "5 dias" = hoje + 4 dias
- Decisão: a previsão será exibida para 5 dias corridos, entendendo o dia atual mais quatro dias seguintes.
- Justificativa: o intervalo é simples de explicar ao usuário, coerente com o briefing e consistente com a maioria das experiências de clima em apps de uso cotidiano.
- O que resolve: elimina ambiguidade sobre o escopo da previsão e define com clareza o que significa “próximos 5 dias”.

### 3. Unidade padrão: Celsius
- Decisão: a unidade padrão da interface será Celsius (°C), com opção de alternar para Fahrenheit (°F).
- Justificativa: Celsius é a unidade mais comum em mercados lusófonos e facilita a adoção inicial da aplicação. A alternância mantém flexibilidade para usuários com preferência diferente.
- O que resolve: define a experiência padrão e fecha a questão sobre persistência ou preferência de temperatura no primeiro momento, sem bloquear a conversão manual.

### 4. Sem autenticação e sem persistência de servidor
- Decisão: a versão inicial não terá login, cadastro nem armazenamento de dados no servidor.
- Justificativa: reduz complexidade de desenvolvimento, acelera a entrega e está alinhado com a proposta de produto focada em consulta rápida e local, sem dados sensíveis ou usuários autenticados.
- O que resolve: responde diretamente às dúvidas sobre identidade do usuário, histórico persistente e infraestrutura de backend.

### 5. Idioma da UI: pt-BR
- Decisão: a interface será apresentada em português do Brasil e os rótulos, mensagens e datas seguirão esse idioma como padrão.
- Justificativa: o projeto e o público-alvo do treinamento são lusófonos, e isso melhora clareza de uso e aderência ao contexto do produto.
- O que resolve: elimina ambiguidade sobre o idioma da aplicação e reduz risco de inconsistência visual e textual no produto final.

## Personas

### 1. Maria, profissional urbana
- Perfil: 32 anos, trabalha em escritório e precisa decidir se vai de metrô, carro ou caminhar para o trabalho.
- Objetivo principal: consultar rapidamente o clima da cidade e planejar o dia sem perder tempo.
- Necessidades: busca simples, visualização clara do clima atual e previsão curta para tomar decisões imediatas.

### 2. Carlos, estudante em viagem curta
- Perfil: 21 anos, viaja de cidade em cidade para estudo ou visita a familiares, frequentemente em deslocamentos curtos.
- Objetivo principal: verificar clima de outras localidades e escolher a melhor roupa e planejamento do dia.
- Necessidades: busca por diferentes cidades, comparação rápida entre temperaturas e conversão entre unidades.

### 3. Ana, mãe de família
- Perfil: 38 anos, organiza rotina doméstica e atividades externas com o restante da família.
- Objetivo principal: entender a previsão dos próximos dias para planejar roupas, deslocamentos e atividades ao ar livre.
- Necessidades: previsão de 5 dias, leitura fácil em mobile e entendimento rápido da tendência climática.

## Cenários de Aceite

### Cenário de aceite - Maria
- Dado que Maria abre a aplicação em seu smartphone
- Quando ela busca por “São Paulo”
- Então o sistema deve mostrar o clima atual, a previsão dos próximos 5 dias e permitir a troca entre °C e °F sem recarregar a página
- E a informação deve ser legível em uma tela mobile sem zoom manual.

### Cenário de aceite - Carlos
- Dado que Carlos quer comparar clima entre “Rio de Janeiro” e “Curitiba”
- Quando ele pesquisa cada cidade e alterna as unidades de temperatura
- Então o sistema deve exibir resultados corretos em ambas as cidades
- E a conversão deve refletir instantaneamente nas temperaturas apresentadas.

### Cenário de aceite - Ana
- Dado que Ana deseja planejar a semana da família
- Quando ela acessa a previsão dos próximos 5 dias de sua cidade
- Então o sistema deve mostrar a temperatura máxima e mínima por dia, a descrição do clima e uma visão clara da tendência do período
- E a previsão deve estar compreensível em poucos segundos em um celular.
