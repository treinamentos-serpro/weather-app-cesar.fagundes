# Weather App — Product Specification

## Overview

O Weather App é uma aplicação web responsiva para consulta rápida de condições climáticas. Seu público principal é formado por pessoas que precisam decidir sobre deslocamentos, vestuário e atividades externas sem autenticação ou navegação complexa.

A primeira versão permitirá pesquisar uma cidade, selecionar um resultado, consultar o clima atual e visualizar a previsão diária de cinco dias corridos, considerando o dia atual e os quatro dias seguintes. A interface será apresentada em português do Brasil, terá Celsius como unidade padrão e permitirá alternar para Fahrenheit.

### Objetivos

- Permitir que uma pessoa encontre uma cidade e consulte seu clima em poucos passos.
- Exibir informações atuais e uma visão comparável dos próximos cinco dias.
- Oferecer uma experiência legível, acessível e adequada principalmente a smartphones.
- Comunicar claramente carregamento, ausência de resultados e falhas recuperáveis.

### Personas principais

- **Maria, profissional urbana:** precisa consultar rapidamente o clima para decidir como se deslocar até o trabalho.
- **Carlos, estudante em viagem curta:** pesquisa cidades diferentes e alterna unidades de temperatura conforme sua preferência.
- **Ana, mãe de família:** usa a previsão de vários dias para planejar a rotina e atividades externas.

## Functional Requirements

### FR-01 — Buscar cidades

O sistema deve permitir que o usuário pesquise uma cidade por nome em um campo de busca. Após a consulta, deve apresentar no máximo cinco resultados relevantes, ordenados da maior para a menor correspondência. Cada resultado deve fornecer contexto geográfico suficiente para a seleção, como cidade, estado ou região e país quando disponível, e deve poder ser selecionado pelo usuário.

### FR-02 — Informar ausência de resultados

Quando a busca não encontrar nenhuma cidade correspondente, o sistema deve apresentar um estado vazio amigável com uma mensagem clara, como “Nenhuma cidade encontrada”, sem quebrar ou deslocar de forma incoerente o layout principal.

### FR-03 — Exibir clima atual

Depois que o usuário selecionar uma cidade, o sistema deve exibir o clima atual daquela localidade. No mínimo, devem estar visíveis a temperatura atual, a descrição da condição climática, um ícone representativo, a umidade relativa e a velocidade do vento.

### FR-04 — Exibir previsão de cinco dias

Depois que uma cidade for selecionada, o sistema deve exibir a previsão de cinco dias corridos, incluindo o dia atual e os quatro dias seguintes. Para cada dia, deve mostrar a data, uma descrição resumida da condição climática, a temperatura máxima e a temperatura mínima. A apresentação deve permitir comparar os cinco dias com clareza.

### FR-05 — Alternar unidade de temperatura

O sistema deve oferecer um controle visível para alternar entre Celsius (°C) e Fahrenheit (°F). A unidade inicial deve ser Celsius. Ao alternar, todas as temperaturas atuais e da previsão visíveis devem ser convertidas e atualizadas imediatamente, sem recarregar a página.

### FR-06 — Informar estados de consulta e falha

Durante a consulta de cidades ou dados climáticos, o sistema deve exibir um indicador de carregamento. Em caso de falha de rede, indisponibilidade da fonte de dados ou timeout, deve exibir uma mensagem clara e oferecer uma ação para tentar novamente. A interface deve permanecer utilizável e recuperável após o erro.

### FR-07 — Oferecer experiência mobile

O sistema deve funcionar em smartphones com larguras entre 320 px e 768 px, mantendo legibilidade e acesso às funções principais sem zoom manual. Os principais elementos interativos devem ter área mínima de toque de 44 px por 44 px.

## User Stories

- **US-01:** Como Maria, quero buscar uma cidade pelo nome para consultar rapidamente se o clima é adequado ao meu deslocamento.
- **US-02:** Como Carlos, quero distinguir cidades com nomes semelhantes antes de selecionar uma para evitar consultar a localidade errada.
- **US-03:** Como Maria, quero visualizar o clima atual com as principais condições meteorológicas para tomar uma decisão imediata.
- **US-04:** Como Ana, quero ver a previsão de cinco dias em uma estrutura comparável para planejar a rotina da família.
- **US-05:** Como Carlos, quero alternar entre Celsius e Fahrenheit para ler as temperaturas na unidade que prefiro.
- **US-06:** Como qualquer usuário, quero receber feedback durante carregamentos e erros para entender o que está acontecendo e conseguir continuar usando a aplicação.
- **US-07:** Como usuário de smartphone, quero consultar e operar a aplicação sem zoom ou controles difíceis de tocar para usar o produto em movimento.

## Acceptance Criteria

Os critérios abaixo são verificáveis e cobrem todos os requisitos funcionais `FR-01` a `FR-07`.

### AC-01 — Busca com resultados relevantes (`FR-01`, `US-01`)

- Dado que o usuário informa um nome de cidade válido e inicia a busca, quando a consulta termina, então o sistema exibe entre zero e cinco resultados.
- Quando houver resultados, então eles aparecem ordenados por relevância e cada item pode ser selecionado.
- Quando o usuário seleciona um resultado, então a cidade selecionada passa a ser a localidade usada para consultar os dados climáticos.

### AC-02 — Busca sem correspondência (`FR-02`, `US-01`)

- Dado que o usuário pesquisa um nome sem correspondência, quando a consulta termina, então o sistema exibe uma mensagem de ausência de resultados em português do Brasil.
- Enquanto o estado vazio é exibido, então o campo de busca e a estrutura principal permanecem utilizáveis e sem sobreposição de conteúdo.

### AC-03 — Clima atual (`FR-03`, `US-03`)

- Dado que o usuário seleciona uma cidade válida, quando os dados são carregados, então a tela exibe temperatura atual, descrição, ícone, umidade relativa e velocidade do vento.
- Quando o usuário seleciona outra cidade, então os dados do clima atual são substituídos pelos dados da nova cidade.

### AC-04 — Previsão diária (`FR-04`, `US-04`)

- Dado que o usuário seleciona uma cidade válida, quando os dados são carregados, então a tela exibe exatamente cinco dias corridos, começando no dia atual.
- Para cada um dos cinco dias, então são exibidos data, descrição resumida, temperatura máxima e temperatura mínima.
- A estrutura dos cinco dias permite identificar e comparar cada previsão sem depender de interação adicional ou zoom.

### AC-05 — Alternância de unidade (`FR-05`, `US-05`)

- Dado que uma previsão foi carregada, então a unidade inicial exibida é Celsius (°C).
- Quando o usuário ativa o controle de Fahrenheit, então todas as temperaturas atuais, máximas e mínimas visíveis passam a exibir °F imediatamente.
- Quando o usuário retorna para Celsius, então todas as temperaturas visíveis passam a exibir °C imediatamente.
- A troca de unidade não exige recarregar a página nem iniciar uma nova busca de cidade.

### AC-06 — Carregamento, erro e recuperação (`FR-06`, `US-06`)

- Quando uma consulta de cidade ou previsão está em andamento, então um indicador de carregamento é exibido.
- Dado que a fonte de dados falha ou excede o tempo limite, quando a aplicação detecta a falha, então exibe uma mensagem clara de erro.
- Quando o usuário aciona “Tentar novamente”, então uma nova tentativa de consulta é iniciada e um indicador de carregamento volta a ser exibido.
- Um erro de consulta não deixa a interface bloqueada nem impede novas tentativas.

### AC-07 — Uso em smartphone (`FR-07`, `US-07`)

- Em uma viewport com largura de 320 px a 768 px, então o conteúdo principal permanece legível, acessível e sem rolagem horizontal necessária para usar as funções principais.
- Os controles principais de busca, seleção, nova tentativa e unidade possuem área de toque de pelo menos 44 px por 44 px.
- As informações de clima atual e previsão permanecem acessíveis sem zoom manual.

### AC-08 — Cenário integrado de Maria (`FR-01`, `FR-03`, `FR-04`, `FR-05`, `FR-07`)

- Dado que Maria abre a aplicação em um smartphone, quando pesquisa “São Paulo” e seleciona o resultado, então vê o clima atual e a previsão de cinco dias.
- Quando Maria alterna para Fahrenheit, então todas as temperaturas exibidas são atualizadas sem recarregar a página e continuam legíveis no smartphone.

### AC-09 — Cenário integrado de Carlos (`FR-01`, `FR-03`, `FR-05`)

- Dado que Carlos pesquisa “Rio de Janeiro” e depois “Curitiba”, quando seleciona cada resultado, então os dados exibidos correspondem à cidade selecionada.
- Quando Carlos alterna a unidade em cada consulta, então a conversão é refletida imediatamente nas temperaturas apresentadas.

### AC-10 — Cenário integrado de Ana (`FR-04`, `FR-07`)

- Dado que Ana acessa a previsão de sua cidade em um celular, quando os dados são carregados, então vê máximas, mínimas e descrição climática para cada um dos cinco dias.
- A previsão pode ser compreendida e comparada sem zoom manual ou interação que esconda os dados de outro dia.

### AC-11 — Validação de entrada de busca (`RR-01`)

- Dado que o usuário digita menos de 2 caracteres após remover espaços, quando tenta buscar, então a aplicação não dispara a consulta e exibe uma mensagem de validação.
- Dado que o usuário digita apenas caracteres inválidos, como símbolos ou emojis, quando tenta buscar, então o sistema informa que a cidade informada não é válida.
- Dado que o usuário informa um nome de cidade com acento ou hífen, quando a busca é iniciada, então o sistema trata corretamente a entrada e executa a consulta.

### AC-12 — Timeout, retry e falha de API (`RR-03`, `RR-04`, `FR-06`)

- Dado que uma requisição de geocodificação ou clima excede 10 segundos, quando o timeout ocorre, então a aplicação exibe uma mensagem de erro e a ação de tentar novamente.
- Dado que a API falha por indisponibilidade ou erro de rede, quando a resposta é recebida, então a tela apresenta o erro sem bloquear a interface.
- Quando o usuário seleciona “Tentar novamente”, então uma nova consulta é iniciada e um indicador de carregamento é exibido novamente.

### AC-13 — Resposta parcial e concorrência (`RR-04`, `RR-05`, `RR-06`)

- Dado que a API retorna dados incompletos para clima atual ou previsão, quando a resposta é processada, então a aplicação não renderiza dados inválidos e exibe mensagem de indisponibilidade.
- Dado que o usuário inicia uma segunda busca antes da primeira terminar, quando a segunda resposta chega, então os dados da segunda cidade prevalecem e os dados da primeira não são exibidos.
- Dado que a busca falhar após uma cidade já ter sido carregada, quando o usuário tenta novamente, então a aplicação mantém o estado anterior apenas como contexto histórico e não como dado atual válido.

### AC-14 — Contratos de dados da API (`RR-09`, `RR-10`)

- Dado que a API de geocodificação retorna um payload sem os campos mínimos exigidos, quando a resposta for validada, então a aplicação rejeita a resposta e exibe erro de dados indisponíveis.
- Dado que a API de clima retorna um payload sem os campos obrigatórios, quando a resposta for processada, então a aplicação não renderiza dados parciais e apresenta mensagem de indisponibilidade.
- Dado que a API retorna pelo menos os campos obrigatórios, quando a renderização inicia, então a interface apresenta os dados esperados sem erros de layout.

### AC-15 — Mensagens finais padronizadas (`RR-11`)

- Dado que o usuário tenta buscar com campo vazio, quando a validação acontece, então a aplicação exibe “Digite o nome de uma cidade.”
- Dado que a busca não encontra resultados, quando a resposta chega, então a aplicação exibe “Nenhuma cidade encontrada.”
- Dado que a API falha ou excede o timeout, quando o erro é capturado, então a aplicação exibe a mensagem correspondente à falha sem deixar a tela bloqueada.

## Non-Functional Requirements

### NFR-01 — Usabilidade

- O fluxo principal deve ser: buscar cidade, selecionar resultado, consultar clima e alternar unidade.
- Em conexão estável, uma pessoa deve conseguir concluir o fluxo principal e visualizar os dados em até 10 segundos.
- Textos, unidades, datas e mensagens devem ser apresentados em português do Brasil.

### NFR-02 — Performance

- Em condições normais de rede, a busca e a renderização da previsão devem ocorrer em até 3 segundos após a consulta ser iniciada.
- O sistema deve fornecer feedback visual imediato ao iniciar uma consulta.
- Uma interação de alternância de unidade deve atualizar as temperaturas sem depender de uma nova requisição de rede.

### NFR-03 — Responsividade

- A interface deve funcionar em smartphones, tablets e desktops, adaptando o layout às larguras disponíveis.
- Nenhuma função prevista deve ficar inacessível por causa da largura da tela.
- A interface mobile deve atender especialmente ao intervalo de 320 px a 768 px definido em `FR-07`.

### NFR-04 — Acessibilidade

- A aplicação deve atender, no mínimo, às diretrizes WCAG 2.1 nível AA para contraste, foco visível e navegação por teclado.
- Campos, controles, resultados, mensagens de estado e ações de erro devem possuir nomes e papéis identificáveis por tecnologias assistivas.
- A ordem de foco deve acompanhar a ordem lógica do fluxo de busca e consulta.

### NFR-05 — Confiabilidade e recuperação

- Falhas da fonte externa, timeout e respostas sem dados devem ser tratados sem travar a interface.
- Após uma falha, o usuário deve conseguir iniciar uma nova tentativa sem recarregar a aplicação.
- Quando possível, respostas recentes podem ser usadas como fallback visual, sem apresentar dados antigos como se fossem atuais.

### NFR-06 — Segurança e privacidade

- A aplicação não deve expor segredos, tokens ou credenciais no cliente.
- A primeira versão não deve exigir login, cadastro ou armazenar informações sensíveis do usuário.
- Nenhum dado de localização do usuário deve ser coletado automaticamente nesta versão.

### NFR-07 — Manutenibilidade

- A solução deve manter separação clara entre interface, integração com fonte de dados e modelos de dados.
- As regras de conversão e apresentação devem ser passíveis de validação isolada.
- A estrutura deve permitir futuras evoluções sem exigir alteração do fluxo principal, como geolocalização, histórico ou filtros climáticos.

## Edge Cases

- Busca vazia, composta apenas por espaços ou com caracteres inesperados: não deve disparar uma consulta inválida; deve orientar o usuário a informar uma cidade.
- Nome muito curto ou pouco específico: pode retornar várias localidades; os resultados devem manter contexto geográfico para apoiar a escolha.
- Cidades homônimas em países ou regiões diferentes: devem aparecer como itens distintos quando a fonte de dados fornecer essa diferenciação.
- Mais de cinco correspondências: somente os cinco resultados mais relevantes devem ser apresentados.
- Nenhuma correspondência: exibir o estado vazio definido em `FR-02`.
- Usuário seleciona um resultado enquanto outra consulta está carregando: a interface deve evitar misturar dados de cidades diferentes.
- Falha de rede, indisponibilidade da API ou timeout: exibir erro recuperável e permitir nova tentativa.
- API responde com dados incompletos, inválidos ou incompatíveis: não exibir campos incorretos como válidos; informar que os dados não estão disponíveis ou solicitar nova tentativa.
- API retorna menos de cinco dias: não preencher dias ausentes com dados inventados; comunicar a indisponibilidade da previsão completa.
- Temperaturas negativas, zero, decimais ou valores extremos: exibir corretamente em ambas as unidades, sem quebrar o layout.
- Alternância repetida entre unidades: não deve acumular erro de conversão; cada mudança deve representar a conversão do valor original.
- Falha ao carregar uma nova cidade após uma consulta bem-sucedida: preservar, quando apropriado, o contexto anterior sem apresentá-lo como resultado da nova cidade e indicar o erro da nova consulta.
- Viewport estreita de 320 px: não permitir que textos, controles ou cartões causem sobreposição ou rolagem horizontal para as tarefas principais.
- Navegação por teclado ou tecnologia assistiva: resultados, controle de unidade, mensagens e ação de nova tentativa devem permanecer alcançáveis e compreensíveis.

## Requisitos complementares para reduzir ambiguidade e facilitar validação

### RR-01 — Validação da busca

- A busca deve considerar como entrada inválida qualquer valor que, após remover espaços em branco, tenha menos de 2 caracteres.
- A aplicação deve aceitar letras, letras com acento, espaços e hífen, mas rejeitar entradas compostas apenas por pontuação, símbolos ou emojis.
- Se a entrada for inválida, o sistema não deve disparar a requisição de geocodificação e deve mostrar uma mensagem de orientação em português do Brasil, como “Digite o nome de uma cidade”.

### RR-02 — Relevância e ordenação dos resultados

- A ordenação dos resultados deve priorizar correspondências exatas por nome da cidade, seguida por cidades com maior proximidade geográfica e maior contexto regional (estado/país).
- Quando houver mais de cinco resultados relevantes, a interface deve mostrar no máximo cinco itens, mantendo a ordem de maior relevância para menor.
- Cidades com nomes iguais em diferentes regiões devem permanecer distintas quando a fonte de dados fornecer contexto suficiente, como estado, região ou país.

### RR-03 — Timeout e retry

- O timeout de cada requisição de geocodificação ou previsão deve ser de 10 segundos.
- Quando a requisição exceder o tempo limite, a aplicação deve mostrar uma mensagem de erro específica e permitir uma nova tentativa via ação explícita.
- A primeira tentativa falha não deve bloquear a interface; o usuário pode executar uma nova busca ou repetir a consulta imediatamente.

### RR-04 — Validação de resposta da API

- A aplicação deve validar todos os campos críticos antes de renderizar qualquer dado climático.
- Se a API retornar campos obrigatórios ausentes, nulos ou em formato inválido, a aplicação deve exibir um estado de erro em vez de apresentar dados incompletos como válidos.
- A interface deve mostrar “Dados climáticos indisponíveis” quando a resposta não contiver os valores necessários para clima atual ou previsão.

### RR-05 — Concorrência e sincronização de consultas

- Quando o usuário inicia uma nova busca enquanto uma anterior ainda está carregando, a requisição mais recente deve ter prioridade sobre a anterior.
- Dados de consultas antigas não devem substituir os dados da cidade atual em execução.
- A interface deve evitar que dados de busca concorrente sejam misturados em um único estado visual.

### RR-06 — Fallback e dados antigos

- A aplicação não deve exibir dados de uma consulta anterior como se fossem atuais após uma falha ou mudança de cidade.
- Quando houver dados recentes em cache e a busca falhar, o sistema pode mostrar um aviso de indisponibilidade sem apresentar os dados como válidos.
- O status visual deve indicar claramente se os dados são atuais ou não.

### RR-07 — Conversão de temperatura

- A conversão entre Celsius e Fahrenheit deve seguir a fórmula: $F = (C \times 9/5) + 32$.
- Os valores exibidos na interface devem ser arredondados para o inteiro mais próximo.
- A alternância de unidade deve alterar todas as temperaturas visíveis imediatamente, sem recarregar a página ou iniciar uma nova requisição.

### RR-08 — Mensagens e estados visuais

- Todos os estados de erro, vazio e carregamento devem apresentar texto em português do Brasil.
- Mensagens de erro e ausência de resultados devem ser acessíveis por leitores de tela e permanecer visíveis sem ocultar o conteúdo principal.
- A ação de retry deve ser identificável por nome acessível e deve permanecer funcional mesmo em telas pequenas.

### RR-09 — Contrato de dados da API de geocodificação

- A aplicação deve consumir a API de geocodificação do Open-Meteo para buscar cidades por nome.
- Para cada resultado válido, o sistema deve exigir pelo menos os campos `name`, `country`, e `latitude` e `longitude`.
- Quando o resultado vier com `state`, `admin1` ou `region`, o sistema deve usar esse dado para enriquecer a label visual da cidade.
- A interface deve exibir cada cidade como um item de seleção com: nome da cidade, contexto regional e país, quando disponíveis.
- A resposta abaixo do mínimo de campos obrigatórios deve ser tratada como resposta inválida.

### RR-10 — Contrato de dados da API de clima

- A aplicação deve consumir os dados de clima atual e previsão do Open-Meteo.
- A consulta de clima atual deve exigir pelo menos: `current.temperature_2m`, `current.relative_humidity_2m`, `current.wind_speed_10m`, `current.weather_code` e `current.time`.
- A previsão de cinco dias deve exigir pelo menos: `daily.time`, `daily.temperature_2m_max`, `daily.temperature_2m_min`, `daily.weather_code`.
- Se algum campo obrigatório estiver ausente, a aplicação deve tratar os dados como incompletos e apresentar erro.
- Quando a previsão for incompleta, o sistema deve mostrar mensagem de “Previsão indisponível” e evitar renderizar dias vazios ou inventados.

### RR-11 — Mensagens finais padronizadas

- Cidade inexistente: “Nenhuma cidade encontrada.”
- Input vazio: “Digite o nome de uma cidade.”
- Entrada inválida por caracteres: “Informe uma cidade válida.”
- Falha de rede/servidor: “Não foi possível carregar os dados no momento. Tente novamente.”
- Timeout: “A busca demorou mais do que o esperado. Tente novamente.”
- Dados incompletos: “Dados climáticos indisponíveis.”
- Previsão incompleta: “Previsão indisponível para esta cidade.”

## Assumptions

- A fonte de dados será a API pública Open-Meteo, incluindo seus serviços de geocodificação e previsão, sem necessidade de chave de acesso.
- A busca inicial será manual por nome de cidade; geolocalização automática não faz parte da primeira versão.
- “Cinco dias” significa hoje mais os quatro dias corridos seguintes.
- Celsius (°C) será a unidade inicial.
- A unidade escolhida não será persistida entre sessões na primeira versão; a preferência será válida durante a sessão atual da aplicação.
- A interface e as mensagens serão apresentadas em português do Brasil.
- A primeira versão não terá autenticação, cadastro, persistência em servidor ou histórico de cidades.
- A aplicação será usada para consulta rápida e informativa, não para análise meteorológica avançada ou garantia de precisão local.
- A implementação terá acesso a uma conexão de rede para consultar a fonte externa; a indisponibilidade será tratada como estado recuperável.

## Risks

| Risco | Probabilidade | Impacto | Mitigação |
| --- | --- | --- | --- |
| Indisponibilidade, latência ou mudança de comportamento da API externa | Alta | Alto | Tratar timeout e erro, oferecer nova tentativa, fornecer feedback claro e considerar cache de respostas recentes sem mascarar sua atualidade. |
| Ambiguidade entre cidades com o mesmo nome | Média | Médio | Exibir contexto regional e país, ordenar resultados por relevância e limitar a lista aos cinco resultados mais relevantes. |
| Dados climáticos incompletos ou de qualidade variável | Média | Médio | Validar campos recebidos, comunicar indisponibilidade e indicar a atualização dos dados quando essa informação estiver disponível. |
| Interface difícil de usar em telas pequenas | Média | Alto | Adotar validação mobile-first, respeitar áreas de toque, testar viewport de 320 px e verificar ausência de sobreposição ou rolagem horizontal. |
| Erros de conversão ou arredondamento de temperatura | Média | Médio | Centralizar a regra de conversão, converter sempre a partir do valor original e validar temperaturas negativas, zero e decimais. |
| Requisitos ainda indefinidos gerarem retrabalho | Média | Alto | Registrar as questões abertas, validar decisões antes da implementação e controlar alterações de escopo. |
| Falha em requisitos de acessibilidade | Média | Alto | Validar contraste, foco, teclado, nomes acessíveis e uso com tecnologias assistivas durante testes de aceitação. |

## Out of Scope

- Autenticação, cadastro, perfis ou contas de usuário.
- Persistência de cidades, unidade de temperatura ou histórico entre sessões.
- Geolocalização automática e solicitação de permissão de localização.
- Previsão horária, dados intradiários ou visualizações meteorológicas avançadas.
- Alertas climáticos severos, notificações push ou avisos personalizados.
- Comparação simultânea de várias cidades na mesma tela.
- Mapas, radar meteorológico, imagens de satélite ou camadas geográficas.
- Favoritos, compartilhamento social e integração com calendário.
- Administração de conteúdo ou painel operacional.
- Armazenamento de dados sensíveis ou persistência de dados pessoais no front-end.
- Garantia de precisão meteorológica além dos dados fornecidos pela fonte externa.

## Open Questions

As questões abaixo permanecem abertas porque podem alterar o produto, a experiência ou o esforço de implementação. Elas não bloqueiam a especificação da primeira versão enquanto as decisões registradas em `Assumptions` forem mantidas.

1. A busca deverá aceitar somente cidades ou também regiões, estados e países como termos explícitos?
2. A previsão diária deverá exibir apenas os cinco dias definidos ou haverá necessidade futura de dados horários?
3. O idioma pt-BR será o único idioma suportado ou deverá existir internacionalização desde a primeira versão?
4. O formato de data deverá seguir sempre o padrão brasileiro ou acompanhar a localidade selecionada?
5. Será necessário oferecer tema claro, dark mode ou preferência de tema do sistema?
6. A unidade de temperatura deverá ser persistida entre sessões em uma versão posterior?
7. Alertas climáticos severos serão necessários em uma versão futura e qual será a fonte desses alertas?
8. O requisito de funcionamento em redes lentas deverá ter metas específicas de tempo, tamanho de resposta e comportamento offline?
9. O cache de respostas recentes será obrigatório para a primeira versão ou apenas uma opção de mitigação de indisponibilidade?
10. Qual política de atualização ou indicação de idade dos dados climáticos deve ser apresentada ao usuário?
