

## Apresentação
O presente projeto foi originado no contexto das atividades da disciplina de graduação EA075 – Sistemas Embarcados, oferecida no primeiro semestre de 2023, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).
O desenvolvimento do projeto será feito pelos seguintes alunos:

|Nome	                         |RA	     |Curso           |
|------------------------------|--------|----------------|
|Rafael Ifanger Ribeiro        |250499  |Eng. Automação  |
|Vicente José Campitelli Real  |239834  |Eng. Computação |


## Descrição do Projeto
O presente projeto destina-se a desenvolver um sistema que analise a qualidade da água em fluxo por um conduto, permitindo sua classificação em relação às possíveis aplicações desejadas, sejam elas provenientes de quaisquer fontes, como:
•	Captação de águas pluviais;
•	Efluentes (industriais, domésticos etc.);
•	Corpos hídricos;
•	Etc.
Feita a classificação do possível uso da água será acionada uma válvula de duas vias, direcionando o fluxo para o reservatório adequado, de acordo com tal classificação.


## Utilizações possíveis
A partir do conjunto adequado de sensores e do desenvolvimento do firmware correspondente, o sistema proposto poderá ser utilizado em diversas aplicações, como, por exemplo: análise de água de aquário, destinação adequada de águas pluviais, análise de qualidade de corpos hídricos e definição do tratamento e destinação corretas de efluentes industriais em tempo real.
O projeto será desenvolvido visando o aproveitamento de águas pluviais em uma residências, devido a perspectiva de implementação prática imediata, sem envolver outros agentes externos ao desenvolvimento e a possibilidade de multiplicação da aplicação beneficiando a comunidade no entorno da Unicamp.


## Motivação
A destinação adequada dos recursos de água doce é de tamanha importância na busca de uma economia sustentável que foi escolhida para compor o capítulo 18 da Agenda 21. De modo coerente às recomendações da Agenda, em 21 de fevereiro de 1993, a Assembleia Geral da Organização das Nações Unidas, declarou o dia 22 de março como o “Dia Mundial da Água”. De acordo com a Wikipédia:
A cada ano, uma agência diferente das Nações Unidas produz um kit para imprensa sobre o DMA que é distribuído nas redes de agências contatadas. Este kit tem como objetivos, além de focar a atenção nas necessidades, entre outras, de:
- Tocar assuntos relacionados a problemas de abastecimento de água potável;
- Aumentar a consciência pública sobre a importância de conservação, preservação e proteção da água, fontes e suprimentos de água potável;
- Aumentar a consciência dos governos, de agências internacionais, organizações não governamentais e setor privado;
- Promover campanhas sobre a importância da água.
Portanto, a sociedade já tomou consciência que a água é um recurso a ser preservado e corretamente utilizado, justificando o projeto em tela.


## Regulamentação aplicável
No Brasil, a Agência Nacional de Águas (ANA), publicou os Indicadores de Qualidade das Águas (IQA) para avaliar a qualidade da água bruta (água não tratada), adotando a sistemática que vinha sendo utilizada pela CETESB (Companhia Ambiental do Estado de São Paulo) desde 1975 (criado pela National Sanitation Foundation dos Estados em 1970). A composição do IQA está listada na tabela 1:

 ![image](https://user-images.githubusercontent.com/86883576/229387705-6212b3b1-538a-4138-b65f-1a2d739d79bf.png)

Tabela 1: Indicadores de Qualidade das Águas (IQA) – fonte ANA

Conforme observado, na tabela 1, os IQA são nove parâmetros com respectivos pesos.
A publicação traz, ainda, o valor de qualidade em função da concentração de cada parâmetro, conforme figura 1:

 ![image](https://user-images.githubusercontent.com/86883576/229387739-ec50dd09-3e0c-447a-9ee0-07b0c7c74ea6.png)

Figura 1: Qualidade da Água em Cada Parâmetro do IQA – fonte ANA


A Agência reconhece as limitações de tal sistemática, posto que não são observados outros parâmetros importantes para o abastecimento, como o teor de substâncias tóxicas (pesticidas, metais pesados etc.) e agentes patogênicos entre outros.
Considerando as várias possibilidades de utilização das águas, o Conselho Nacional do Meio Ambiente-CONAMA, publicou a Resolução CONAMA nº 357, de 17 de março de 2005, que “dispõe sobre a classificação e diretrizes ambientais para o enquadramento dos corpos de água superficiais, bem como estabelece as condições e padrões de lançamento de efluentes”. Tal regulamentação classifica as águas doces, salinas e salobras em classes adequadas à diversas finalidades e amplia os parâmetros utilizados para tal classificação indicando, por exemplo, teores limites de contaminantes (orgânicos e inorgânicos) para os diversos usos.


## Descrição Funcional
A aplicação será montada para análise dos parâmetros de turbidez, pH. Serão, ainda, registradas as leituras de temperatura e vazão.
Após a determinação da qualidade da água o fluxo será direcionado adequadamente por uma válvula de duas vias.

  ![image](https://user-images.githubusercontent.com/86883576/229387759-a90bdc5c-de45-4e76-be83-720aca4c6e24.png)

 Figura 2: Fluxograma funcional do sistema – elaboração própria


## Funcionalidades
A funcionalidade básica do sistema é detectar a qualidade da água a partir de sensores e processamento dos dados por um microcontrolador.
Desse modo, o sistema recolherá ciclicamente os valores de sensores para determinar a qualidade da água.

Armazenando as entradas, o sistema (microcontrolador), a partir de limiares de qualidade estabelecidos, definirá se a água do fluxo analisado está dentro ou fora do aceitável.
Se a qualidade for aceita, com uma válvula de duas vias, o fluxo é direcionado para a aplicação estabelecida. Em caso contrário o fluxo é desviado para descarte, ou armazenado, para uma análise mais detalhada, laboratorial, e sua destinação adequada.

## Configurabilidade
Como citado, o sistema deverá ser configurado para a aplicação específica a que se destinar, que no caso em desenvolvimento, será o aproveitamento de águas pluviais. Portanto, os parâmetros de determinam a qualidade da água devem ser configurados para a aplicação.
Outras configurações do sistema são o período de leitura dos sensores, podendo diminuir ou aumentar a periodicidade entre as leituras de cada sensor, para formar o log de eventos de acordo com a demanda da aplicação.
Tais configurações serão realizadas por software.


## Eventos
Os eventos serão gerados pelo confronto entre os dados aquisitados, pelos sensores, com os parâmetros de qualidade de água. Tais comparações irão determinar o destino do fluxo de água e serão acumulados em log de eventos. Não haverá eventos externos além dos gerados pelos sensores.
Poderá ser adicionada a configuração dos limiares com um teclado em versão futura, possibilitando maior flexibilidade ao sistema. Neste caso, o evento de configuração por teclado matricial, este evento será não periódico.


## Tratamento de Eventos
Na inicialização do sistema, toda a parametrização é mostrada no display.
O evento de recepção dos dados dos sensores é realizado de forma cíclica colhendo N amostras (passível de configuração) periodicamente, conforme configuração, realizando a leitura para armazenamento e tratamento dos dados. O tratamento dos dados será feito por outra tarefa não periódica.
A qualidade da água definida pelo sistema será apresentada por um display.
Caso seja implementada, futuramente, a configuração por teclado matricial, o tratamento será interrompido.
Ocorrendo o evento de qualidade de água inferior ao padrão, a segregação da água será feita acionando a passagem adequada pela válvula, para um reservatório adequado.


## Descrição Estrutural do Sistema
O sistema é composto pelas seguintes partes:
- Microcontrolador;
- Sensores (todos intrusivos): pH, turbidez, temperatura, vazão, presença de gases inflamáveis;
- Atuador: válvula de duas vias;
- Display com informação sobre a qualidade da água;
- Fonte de alimentação.
Os sensores serão montados em um carretel que será colocado na tubulação por onde passa o fluxo de água. O sensor de gás será colocado em uma derivação adequada que impeça a perda de água.
A válvula de duas vias será montada após o carretel dos sensores de modo a desviar o fluxo que foi analisado.

A figura abaixo apresenta os componentes do sistema.


![FluxogramaSistema](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/7b7007ab-ad0e-4db5-a9b0-628887e30a05)

Figura 3: Componentes do Sistema Analisador de Qualidade de Água


## Especificações
O sistema será composto pelos seguintes subsistemas:
- Partes montadas em uma caixa à prova de tempo (IP65):
  - Processador: um módulo de desenvolvimento com microcontrolador ESP32;
  -	Placa de interface aos periféricos com conversor A/D (com comunicação I<sup>2</sup>C) ADS111, drivers de adequação de nível de tensão e conectores para ligação dos sensores e válvula atuadora;
  -	Display OLED para possibilitar a configuração do sistema e apresentar os resultados da análise, vazão e disposição da água;
-	Sensor de pH Ph4502c; 
-	Sensor de turbidez ST100; 
-	Sensor de temperatura DS18B20; 
-	Detector de gases inflamáveis MQ-2;
-	Medidor de vazão YF-S201;
-	Válvula solenóide de duas vias, que fará a segregação de água;
-	Fonte de alimentação.

O firmware do sistema foi desenvolvido em C. Tal opção é devido a necessidade de acessar os recursos de hardware do processador ESP32 e devido aos fornecedores dos componentes fornecerem, em muitos casos, funções nesta linguagem para configuração e uso de tais componentes.

O microcontrolador ESP32 foi escolhido por ser uma alternativa com boa relação custo x benefício. Segundo a Wikipédia: "ESP32 é uma série de microcontroladores de baixo custo e baixo consumo de energia. Também
 é um sistema-em-um-chip com microcontrolador integrado, Wi-Fi e Bluetooth. A série ESP32 emprega um micro processador Tensilica Xtensa LX6 com duas variações dual-core e single-core e inclui uma antena integrada RF tipo balun, amplificador de potência, receptor de baixo ruído amplificado, filtros, gerenciamento de energia dos módulos. "


O sistema poderá ser parametrizado para diversas aplicações, entretanto o desenvolvimento do protótipo será para água pluvial. No protótipo foram escolhidos aqueles que apresentam baixo custo e fácil implementação, porém, em aplicações industriais, outros sensores poderão ser utilizados.

Os demais componentes (sensores e válvula atuadora) foram selecionados por serem oferecidos no mercado nacional, com baixo custo e terem eletrônica adiocional já montada, facilitando a conclusão do projeto.

As figuras abaixo apresentam os componentes escolhidos para a montagem do protótipo:


![Esp32-PlacaDesenvolvimento](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/eadcf155-46fc-4897-8463-d98d07cf09de)

Figura 4: Módulo ESP32


![DisplayOled](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/caff3a3e-35de-4499-b9de-9bdca0eeba2a)

Figura 5: Display OLED


![SensorPh4502c](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/a342c8f2-5b71-46dc-9f99-047543fd2e90)

Figura 6: Sensor de pH Ph4502c 


![SensorTurbidez](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/a0b0fa1c-0df7-4024-a04e-d2c47f99a50d)

Figura 7: Sensor de turbidez ST100


![TermoparTipoK](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/1e0725bf-af5a-4268-a0ad-e03a1b68f9d5)

Figura 8: Sensor de Mas6675 Termopar tipo K


![SensorGasMQ2](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/53eb6e19-b2b0-4890-8812-7975882eecb2)

Figura 9: Detector de gases inflamáveis MQ-2


![MedidorVazao](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/c3d2018e-bba8-4960-82ac-9403f1d69170)

Figura 10: Medidor de vazão YF-S201


![ValvulaSolenoide2Vias](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/a3c48810-6e58-498e-bc6e-733dd7d0b89b)

Figura 11: Válvula solenóide de duas vias



A figura abaixo apresenta a caixa para abrigar os componentes eletrônicos (ESP32, fonte e eletrônica associada aos sensores e atuador).


![CaixaMontagem](https://github.com/teaching-FEEC/ea075-2023.1/assets/86883576/20b0a7ac-8d79-40d0-8487-f0d3345e754a)

Figura 12: Caixa dos componentes eletrônicos

## Glossário
**Agenda 21**Foi um dos principais resultados da conferência Eco-92 ou Rio-92, ocorrida no Rio de Janeiro, Brasil, em 1992. É um documento que estabeleceu a importância de cada país a se comprometer a refletir, global e localmente, sobre a forma pela qual governos, empresas, organizações não-governamentais e todos os setores da sociedade poderiam cooperar no estudo de soluções para os problemas socioambientais (fonte Wikipédia).


## Referências
Agência Nacional das águas (ANA): Indicadores de Qualidade das Águas (IQA), disponível em http://pnqa.ana.gov.br/indicadores-indice-aguas.aspx, consulta em 15.mar.2023
Analog: DS18B20, disponivel em https://www.analog.com/media/en/technical-documentation/data-sheets/DS18B20.pdf, consulta em 18.mai.2023
Conselho Nacional do Meio Ambiente-CONAMA: Resolução CONAMA nº 357, de 17 de março de 2005, disponível em https://www.mpf.mp.br/atuacao-tematica/ccr4/dados-da-atuacao/projetos/qualidade-da-agua/legislacao/resolucoes/resolucao-conama-no-357-de-17-de-marco-de-2005/view#:~:text=Disp%C3%B5e%20sobre%20a%20classifica%C3%A7%C3%A3o%20dos,efluentes%2C%20e%20d%C3%A1%20outras%20provid%C3%AAncias, consulta em 15.mar.2023
Espressif: microcontrolador ESP32, disponível em https://www.espressif.com/en/products/socs/esp32, consulta em 18.mai.2023
Mantech: YF-S201 - medidor de vazão de água, disponível em http://www.mantech.co.za/datasheets/products/yf-s201_sea.pdf, consulta em 18.mai.2023
Mercado Livre: Display OLED, disponível em https://produto.mercadolivre.com.br/MLB-2718237771-3-x-modulo-display-oled-096-i2c-lcd-arduino-pic-_JM?matt_tool=18956390&utm_source=google_shopping&utm_medium=organic, consulta em 20.mai.2023
_______ Sensor de temperatura: https://produto.mercadolivre.com.br/MLB-1421016384-modulo-leitor-temperatura-max6675-termopar-tipo-k-automaco-_JM#position=8&search_layout=stack&type=item&tracking_id=55b51223-dbee-43ff-bd36-b2de9fbf5e94 
______ Sensor de pH Ph4502c, disponível em https://produto.mercadolivre.com.br/MLB-2126666442-sensor-de-ph-ph4502c-com-eletrodo-sonda-bnc-arduino-_JM?matt_tool=40343894&matt_word=&matt_source=google&matt_campaign_id=14303413655&matt_ad_group_id=133855953276&matt_match_type=&matt_network=g&matt_device=c&matt_creative=584156655519&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=370933762&matt_product_id=MLB2126666442&matt_product_partition_id=1816238256222&matt_target_id=pla-1816238256222&gclid=CjwKCAjwgqejBhBAEiwAuWHioIxJDGtC9tkoYNJvX5gAWUEnbvePhUOjpSjXk7gTSZD_H4qwux0GexoCQd0QAvD_BwE, consulta em 18.mai.2023
______ Sensor de turbidez, disponível em https://produto.mercadolivre.com.br/MLB-3238478147-detecco-do-valor-de-turbidez-suspenso-do-sensor-de-turbidez-_JM?matt_tool=34055620&matt_word=&matt_source=google&matt_campaign_id=14303413817&matt_ad_group_id=125984298397&matt_match_type=&matt_network=g&matt_device=c&matt_creative=539354956989&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=696027066&matt_product_id=MLB3238478147&matt_product_partition_id=1801222606685&matt_target_id=pla-1801222606685&gclid=CjwKCAjwgqejBhBAEiwAuWHioEaGXEvfclrmQkahQmZxROTB9XhHRPCXiK-D31zPs5Ojh3sNV6-iYhoC9-UQAvD_BwE, consulta em 18.mai.2023
_______ Válvula solenoide de duas vias, disponivel em https://produto.mercadolivre.com.br/MLB-2196824192-valvula-de-entrada-de-agua-2-vias-brastemp-ative-bwl11-127v-_JM?matt_tool=59229076&matt_word=&matt_source=google&matt_campaign_id=14303413835&matt_ad_group_id=125984300317&matt_match_type=&matt_network=g&matt_device=c&matt_creative=539354957190&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=414921459&matt_product_id=MLB2196824192&matt_product_partition_id=1799522882129&matt_target_id=pla-1799522882129&gclid=CjwKCAjwgqejBhBAEiwAuWHioAAJMCfhwqpGs66CddV2ahKgM8GRz5Lc9jDMmpVG2oBrUJ9r6Sn_yBoCqicQAvD_BwE, consulta em 21.mai;2023
Polulu: sensor de gases inflamáveis MQ2, disponivel em https://www.pololu.com/file/0J309/MQ2.pdf, consulta em 20.mai.2023
Texas Instruments: ADS11, disponível em https://www.ti.com/product/ADS1113?qgpn=ads1113, consulta em 18.mai.2023
Wikipédia: Agenda 21, disponível em https://pt.wikipedia.org/wiki/Agenda_21, consulta em 15.mar.2023
_______ Dia Mundial da Água, disponível em https://pt.wikipedia.org/wiki/Dia_Mundial_da_%C3%81gua#:~:text=O%20Dia%20Mundial%20da%20%C3%81gua,com%20as%20recomenda%C3%A7%C3%B5es%20da%20Confer%C3%AAncia, consulta em 15.mar.2023
_______ ESP32, disponível em https://pt.wikipedia.org/wiki/ESP32, consulta em 19.mai.2023


