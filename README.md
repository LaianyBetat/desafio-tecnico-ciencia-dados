# Desafio Tecnico Cientista de Dados

Este projeto tem o objetivo de atender aos requisitos solicitados no desafio tecnico, para isso foram gerados 4 arquivos na sequencial.

Sobre os arquivos:

## 1- Pré-processamento de Dados (00_preproc_bases_metricas_pagamentoc.ipynb);

O notebook 00_preproc_bases_metricas_pagamentoc.ipynb realiza o pré-processamento inicial das bases de dados financeiras e de pagamento. Essa etapa é fundamental para garantir a qualidade e consistência dos dados que serão usados nas análises subsequentes. As ações realizadas incluem:
  
- Carregamento das bases de dados: As bases contendo métricas financeiras e de pagamento são carregadas para análise e validação.
- Verificação de tipos de dados: Conferência das colunas para garantir que os tipos de dados (como mes_ano, tpv, qtd_total, etc.) estão corretos, especialmente garantindo que datas sejam tratadas de maneira apropriada.
- Análise de valores nulos: Identificação e tratamento de dados faltantes em colunas essenciais para garantir que os cálculos e insights não sejam afetados por valores ausentes.
- Verificação de valores únicos e inconsistentes: Checagem de valores em colunas importantes, como status_finalizacao e metodo_pagamento, para garantir que todos os registros tenham dados válidos e esperados.
- Conversão de colunas para formatos adequados: Em particular, a coluna mes_ano é convertida para o tipo datetime, facilitando as análises temporais e os cálculos de médias e tendências ao longo dos meses.
- Análises gráficas e de distribuição: Foram gerados histogramas e boxplots para explorar a distribuição dos dados e identificar possíveis outliers ou padrões interessantes, como a dispersão de valores no balanço financeiro.

## 02- questao01_base_metricas_mensais.ipynb: Contém as respostas às seguintes perguntas:

- a) Quais os 5 meses com o melhor e pior fechamento de balanço?
  
Resultado: Foram extraídos os 5 meses com os maiores valores de balanço e os 5 meses com os menores valores, os quais são apresentados em gráficos. O gráfico para os 5 piores meses, por exemplo, está configurado com o uso de sns.lineplot para visualizar o comportamento negativo nesses meses.

Explicação: Os resultados mostram que os cinco melhores meses de balanço ocorreram principalmente em julho de 2019 e 2020, além de abril de 2015, com os maiores ganhos financeiros, sugerindo um bom desempenho sazonal nesses períodos. Em contraste, os cinco piores meses incluem abril de 2019 e 2021, com grandes perdas, indicando desafios recorrentes nesse mês. 

Data	Balanço Final (R$)
2015-04-01	268.988,61
2011-02-01	263.324,75
2012-02-01	209.121,28
2019-07-01	199.522,44
2020-07-01	186.999,54

 Data	Balanço Final (R$)
2022-07-01	-221.165,42
2019-12-01	-223.749,25
2015-10-01	-225.372,41
2019-04-01	-244.345,22
2021-04-01	-245.650,86

 ![Balanço Fina dos 5 melhores meses](https://github.com/user-attachments/assets/07368a5c-cec0-45aa-aced-60a19dc283c2)
 
 ![Balanço Final dos 5 piores meses ](https://github.com/user-attachments/assets/d333f0f9-9bba-4e6d-950b-45007e14e91d)


- b) Qual foi o melhor ano em termos de ganho total? E a média anual do balanço?
  
Resultado:

O ano de 2020 foi o melhor ano em termos de ganho total, com um balanço final acumulado de R$ 405.696,86,
Detalhes sobre a media e mediana;
Com base nesses resultados, não podemos afirmar que a média e a mediana se aproximam. Na maioria dos anos, a diferença entre a média  e a é bastante significativa.
Grandes diferenças: Em muitos casos, como 2010, 2011, 2012, 2019, 2023, e 2024, a diferença entre a média e a mediana é muito grande, indicando que os dados estão dispersos, com uma distribuição assimétrica.
Pequenas diferenças: Em anos como 2013, 2016, e 2017, a diferença é menor, mas ainda não suficiente para dizer que a média e a mediana se aproximam
Em resumo, a diferença entre a média e a mediana sugere que os dados têm uma distribuição que afasta essas duas medidas centrais na maioria dos anos, como mostra a imagem abaixo.
![image](https://github.com/user-attachments/assets/3fadd5c2-92ad-4b7e-b7b0-345217c94515)


- c) Qual o maior período de crescimento ininterrupto no balanço?
  
Resultado:

O maior período de crescimento ininterrupto no balanço ocorreu entre fevereiro de 2014 e setembro de 2015, com um somatório total de R$ 975.952,38. Esse intervalo de 20 meses representa uma fase de expansão contínua, sem quedas no balanço mensal. 

- d) Estimativa do balanço de outubro, novembro e dezembro de 2024.
  
Resultado:

A previsão do balanço para outubro, novembro e dezembro de 2024 mostrou-se imprecisa devido à alta irregularidade dos dados históricos, com grandes variações entre meses positivos e negativos. Essa volatilidade torna difícil prever o desempenho futuro com base nas tendências passadas, pois os balanços financeiros da empresa têm alternado abruptamente entre crescimento e queda. O modelo usado, como o ARIMA, não conseguiu capturar padrões estáveis suficientes para fornecer previsões confiáveis, indicando a necessidade de abordagens mais sofisticadas ou a inclusão de variáveis externas para melhorar a precisão.

## 03- questao02_fraudes_cpf_telefone_nomes.ipynb: 
Valida os dados de CPF e telefone e aborda variações de escrita em nomes.

- a) Validação de CPFs:
  
Resultado: Para verificar se um CPF é válido em termos estruturais, usamos um algoritmo que se baseia nos dois dígitos verificadores do CPF. Estes dígitos verificadores são calculados a partir dos nove primeiros números do CPF, utilizando um cálculo específico com somas ponderadas.

Critérios para validar um CPF:
- Formato básico: O CPF deve ter 11 dígitos numéricos.
- Primeiro dígito verificador: Deve ser calculado com base nos primeiros 9 dígitos do CPF.
- Segundo dígito verificador: Deve ser calculado com base nos 9 dígitos originais mais o primeiro dígito verificador.
- Exclusão de CPFs com todos os dígitos iguais: Como "111.111.111-11", que são considerados inválidos.
Algoritmo para validação de CPF:
Etapas:
- Remover pontuações: Retirar pontos e hífen do CPF, mantendo apenas os números.
Calcular o primeiro dígito verificador:
- Multiplicar os 9 primeiros dígitos por uma sequência de pesos decrescentes de 10 até 2.
- Somar os resultados dessas multiplicações.
- O resto da divisão dessa soma por 11 é subtraído de 11 para encontrar o primeiro dígito verificador (se o resultado for maior que 9, o dígito é 0).
Calcular o segundo dígito verificador:
- Multiplicar os 10 primeiros dígitos (os 9 originais mais o primeiro dígito verificador) por uma sequência de pesos decrescentes de 11 até 2.
- Repetir o processo de soma e resto para encontrar o segundo dígito verificador.
- 
b) Validação de números de telefone:

Resultado: 
Para verificar se um telefone celular brasileiro é válido em termos estruturais, alguns critérios podem ser utilizados:
Critérios para validar um telefone celular no Brasil:
- DDD válido: O DDD (código de área) deve ser composto por dois dígitos e corresponder a uma região válida no Brasil. Os DDDs válidos estão na faixa de 11 a 99, e "10" não é um DDD válido.
- Primeiro dígito do número: No Brasil, números de celular devem começar com o dígito 9.
- Quantidade de dígitos: O número de telefone, excluindo o DDD, deve ter 9 dígitos.
- Faixa do segundo dígito: O segundo dígito de números de celular geralmente está na faixa de 6 a 9 (mas isso pode variar regionalmente).
- Com base nesses critérios, vamos construir um algoritmo para validar telefones celulares.
- 
c) Correção de variações de nomes:

O código apresentado visa normalizar e comparar nomes, permitindo que variações comuns e erros de digitação não afetem a avaliação de similaridade entre eles. A função normalizar_nome remove acentos e palavras comuns (como "da" e "dos"), convertendo os nomes para minúsculas, o que garante que comparações sejam feitas de forma uniforme. Em seguida, a função comparar_nomes calcula a similaridade entre os nomes normalizados usando o SequenceMatcher, retornando True se a similaridade for igual ou superior a 0.8. Isso permite que pares como "Fernando dos Santos" e "Fernando Santos" sejam considerados equivalentes, facilitando a análise de dados em contextos onde erros de preenchimento de nomes são frequentes.

## 04- questao03_metricas_processamento_parceiros.ipynb: Análise das métricas de processamento para parceiros da fintech.

a) Parceiro com maior TPV por mês:

Resultado:

Os resultados mostram que, nos meses de julho, agosto e setembro de 2024, os parceiros com maior volume de processamento de vendas em termos de TPV variam significativamente. Em julho de 2024, o parceiro com o maior processamento foi o user_id 4057, com um TPV de R$ 51.822.500,00, enquanto nos meses de agosto e setembro, o parceiro user_id 652 liderou com valores menores, porém ainda expressivos, de R$ 12.256.841,77 e R$ 8.982.559,97, respectivamente. Esses resultados apontam para uma possível concentração de grandes vendas em certos parceiros em momentos específicos do ano.

![image](https://github.com/user-attachments/assets/469868d3-33de-4c06-b2d8-71aa1f5a492b)

b) Pico de processamento de cartão de crédito:

Resultado: 
O pico de processamento de cartão de crédito ocorreu em julho de 2024, com um TPV de R$ 192.642.173,86. 

c) Identificação dos parceiros supremos:
Resultado: 
A análise mostra que existem 118 parceiros supremos na base de dados, definidos como aqueles que apresentam uma média de processamento total superior a R$ 300.000,00 ao longo de um período de três meses.

d) Oscilação no número de parceiros entre agosto e setembro:
Resultado: 
A análise da estabilidade do processamento dos parceiros revelou uma oscillação absoluta de -1.040 parceiros e uma oscillação percentual de -13,11% entre os meses de agosto e setembro. Isso indica uma diminuição significativa no número de parceiros que geraram um processamento maior que zero nesse período. Essa redução sugere que a fintech pode estar enfrentando desafios que afetam a performance de seus parceiros, como mudanças nas condições de mercado ou problemas operacionais.

Outras Análises

 Análise da quantidade total de transações e a quantidade de transações finalizadas, bem como suas taxas de conversoes:
 
Resultado: A taxa de conversão de 47,67% indica que quase metade das transações realizadas pelos parceiros foram finalizadas com sucesso no status "integrado". Embora isso sugira um desempenho razoável, também revela que mais de 52% das transações não foram integradas, apontando para possíveis problemas operacionais ou técnicos. Melhorar essa taxa é um pilar importante, pois uma conversão mais alta pode resultar em maior receita e fortalecer a confiança na plataforma, além de aumentar as relações com os parceiros.

Análise de Número de Transações por Mês

Resultado: Os dados mostram que o número de transações por mês em julho, agosto e setembro de 2024 foi de 1.637.565, 1.598.021 e 1.289.503, respectivamente. Embora julho tenha registrado o maior volume, houve uma queda de aproximadamente 19,3% em setembro em relação a agosto, indicando uma possível sazonalidade ou fatores que impactaram a demanda.
![image](https://github.com/user-attachments/assets/42b24b4b-60e5-470e-ac1f-4be87cbe643a)

Análises sobre o tempo entre transacoes

Resultado: Os resultados revelam o tempo médio entre transações para diferentes user_ids, variando de 4,43 a 7,75 dias. Esses dados são importantes para entender o comportamento dos parceiros, pois intervalos menores podem indicar maior engajamento com a plataforma. Essa análise pode ajudar a fintech a segmentar usuários, desenvolver estratégias de marketing direcionadas e identificar oportunidades para incentivar transações mais frequentes, especialmente entre aqueles com intervalos maiores.


   
