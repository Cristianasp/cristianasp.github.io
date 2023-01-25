## CIDADES BRASILEIRAS
UM CONJUNTO DE DADOS

#DATASETS #BRAZILIAN-CITIES #DADOSGOVBR

![[img/brazilcities.png]]

Tudo começou com um projeto de expansão na empresa que eu trabalhava. Precisávamos identificar novas cidades e regiões para expandir a operação. Eu já tinha feito um projeto similiar em outra empresa que trabalhei, mas naquela época usamos poucas informações econômicas e sociais das cidades, e tomamos decisões com os dados internos e das empresas concorrentes.

Então fui procurar fontes de informações sobre as cidades brasileiras. Não encontrei nada pronto e disponível gratuitamente. Já tinha até recebido ofertas de bases de dados com informações para tomada de decisão, e os valores eram sempre salgados.

Decidi então me divertir montando uma base útil com os dados disponíveis na Internet.

Comecei com as informações do projeto de dados abertos do governo brasileiro. Há muita informação disponível e com um grande nível de detalhe disponível para toda a população nos diversos sites governamentais. Fiz algumas pesquisas nos sites do IBGE, Tesouro Nacional, Banco Central, Anatel, Embratur, Denatran.

Então adicionei informações sobre a presença de algumas empresas no município, para trazer um tempero diferente a esta coleção de dados. Para tal, rodei scrappers nos sites dessas empresas.  
   
Esse é o resultado do trabalho: uma base com os 5565 municípios brasileiros, com 79 atributos, disponível para download no [Kaggle](https://www.kaggle.com/crisparada/brazilian-cities).

https://www.kaggle.com/crisparada/brazilian-cities

Confira abaixo o detalhamento de cada campo:

##### Localização dos municípios  

Pensando na possibilidade de poder desenhar mapas com a localização dos municípios, encontrei esta [base do IBGE de 2010](ftp://geoftp.ibge.gov.br/organizacao_do_territorio/estrutura_territorial/localidades) com a latitude, longitude e elevação dos 5565 municípios brasileiros em 2010.

Neste caso os dados não devem mudar muito ao longo do tempo, né?

  
##### Área dos municípios  

Em relação à área do município, encontrei a informação nesta [base do IBGE](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/estrutura-territorial/15761-areas-dos-municipios.html?t=acesso-ao-produto&c=1), em km2.

  
##### População Residente  

Comecei com a População Residente, por nacionalidade, disponível na [tabela 1497](https://sidra.ibge.gov.br/tabela/1497) do Instituto Brasileiro de Geografia e Estatística - IBGE, censo de 2010 e lá descobri a população total, população brasileira e população estrangeira.

##### Estimativa da População por Municípios  

Buscando dados mais atuais da população, uma vez que o último censo foi feito em 2010, identifiquei que o IBGE realiza anualmente a [Estimativa da População por Município](https://www.ibge.gov.br/estatisticas/sociais/populacao/9103-estimativas-de-populacao.html?=&t=o-que-e). Utilizei a estimativa de 1 de Julho de 2018.


##### Unidades domésticas rurais e urbanas  

Encontrei no IBGE as unidades domésticas residentes em domicílios particulares, por tipo de família, segundo a situação do domicílio: [tabela 3495](https://sidra.ibge.gov.br/tabela/3495) do censo de 2010 .

Ela apresenta a quantidade de unidades domésticas rurais e urbanas. 


##### Moradores por faixa etária  

A [tabela 3365](https://sidra.ibge.gov.br/tabela/3365) do censo de 2010 apresenta "moradores em domicílios particulares permanentes, em áreas com ordenamento urbano regular, por grupos de idade e existência e características do entorno".

É possível saber a quantidade de moradores por faixa etária: até 1 ano, de 1 a 4 anos, de 4 a 9 anos, de 10 a 14 anos, de 15 a 59 anos, acima de 60 anos.


##### Produção agrícola  

Em seguida procurei por dados econômicos e achei indicadores da agricultura, com dados de 2017. A [tabela 5457](https://sidra.ibge.gov.br/tabela/5457)  apresenta a "área plantada ou destinada à colheita, área colhida, quantidade produzida, rendimento médio e valor da produção das lavouras temporárias e permanentes".

Esta tabela tem informações detalhadas muito interessantes para o agro-negócio. E note que todas essas informações estão abertas por município, o que é extramamente útil para análises detalhadas e regionalizadas.

Selecionei as variáveis: área plantada ou destinada à colheita em hectares (1 hectare = 10,000 metros quadrados) e valor da produção (em Mil Reais).


##### Produto Interno Bruto dos Municípios  

No cenário econômico, o IBGE publica o [Produto Interno Bruto dos Municípios](https://www.ibge.gov.br/estatisticas/economicas/contas-nacionais/9088-produto-interno-bruto-dos-municipios.html?t=downloads).

Neste estudo "são apresentados, a preços correntes, os valores adicionados brutos dos três grandes setores de atividade econômica – Agropecuária, Indústria e Serviços – bem como os impostos, líquidos de subsídios, o PIB e o PIB per capita.

Destaca-se o valor adicionado bruto da Administração, saúde e educação públicas e seguridade social, devido à relevância deste segmento na economia municipal. A análise dos resultados, ilustrada por meio de tabelas, quadros, gráficos e cartogramas, enfoca aspectos econômicos de abrangência nacional, regional e municipal". Dados de 2016.


Os campos são:  
  
-   Valor adicionado bruto da Agropecuária, a preços correntes (R$ 1.000)    
-   Valor adicionado bruto da Indústria, a preços correntes (R$ 1.000)    
-   Valor adicionado bruto dos Serviços, a preços correntes - exclusive Administração, defesa, educação e saúde públicas e seguridade social (R$ 1.000)    
-   Valor adicionado bruto da Administração, defesa, educação e saúde públicas e seguridade social (R$ 1.000)    
-   Valor adicionado bruto total, a preços correntes (R$ 1.000)    
-   Impostos, líquidos de subsídios, sobre produtos, a preços correntes (R$ 1.000)    
-   Produto Interno Bruto, a preços correntes (R$ 1.000)    
-   População (Nº de habitantes)    
-   Produto Interno Bruto per capita (R$ 1,00)    
-   Atividade com maior valor adicionado bruto

##### Despesas dos Municípios  

No site do [Tesouro Nacional Transparente](https://www.tesourotransparente.gov.br), há muitas informações fiscais, contábeis, societárias e financeiras da União. Além disso, há relatórios e análises disponíveis sobre os Estados e Municípios. Encontrei o [[Balanço Patrimonial e Demonstrativo de Despesas dos Municípios - DCA](http://www.tesourotransparente.gov.br/ckan/dataset/dcam), dados de 2016.

No arquivo com a Declaração das Contas Anuais dos Municípios, selecionei a informação **Total de Despesas (exceto intraorçamentárias)**.

Ela totaliza as despesas classificadas nas contas: Legislativa, Judiciária, Administração, Defesa Nacional, Segurança Pública, Relações Exteriores, Assistência Social, Previdência Social, Saúde, Trabalho, Educação, Cultura, Direitos da Cidadania, Urbanismo, Habitação, Saneamento, Gestão Ambiental, Comércio e Serviços, Comunicações, Transporte, Desporto e Lazer, Encargos Especiais.

Atualização: após reestruturação do site do Tesouro Transparente, acesse [esse link](http://apidatalake.tesouro.gov.br/docs/siconfi/) para orientações sobre o acesso às informações via API.

##### Cadastro de Empresas por ramo de atividade  

O sistema SIDRA do IBGE possui o Cadastro Central de Empresas: [Tabela 993 - Empresas e outras organizações, por seção da classificação de atividades (CNAE 2.0), faixas de pessoal ocupado total e ano de fundação](https://sidra.ibge.gov.br/tabela/993).

  
Totalizei a quantidade de empresas por classificação das atividades: 

-   A Agricultura, pecuária, produção florestal, pesca e apicultura 
-   B Indústrias extrativas
-   C Indústrias de transformação 
-   D Eletricidade e gás 
-   E Água, esgoto, atividades de gestão de resíduos e descontaminação 
-   F Construção 
-   G Comércio; reparação de veículos automotores e motocicletas 
-   H Transporte, armazenagem e correio 
-   I Alojamento e alimentação 
-   J Informação e comunicação 
-   K Atividades financeiras, de seguros e serviços relacionados 
-   L Atividades imobiliárias 
-   M Atividades profissionais, científicas e técnicas N Atividades administrativas e serviços complementares 
-   O Administração pública, defesa e seguridade social 
-   P Educação 
-   Q Saúde humana e serviços sociais 
-   R Artes, cultura, esporte e recreação 
-   S Outras atividades de serviços 
-   T Serviços domésticos 
-   U Organismos internacionais e outras instituições extraterritoriais

  
##### Regiões Turísticas  

Em relação ao turismo, o Ministério do Turismo recortou o território brasileiro em [Regiões Turísticas](http://dados.turismo.gov.br/mapa-do-turismo-brasileiro), catalogando 2694 municípios agrupados em 333 regiões com potencial turístico.

As regiões turísticas estão divididas seguindo o seguinte critério: "a categoria A, que representa os municípios com maior fluxo turístico e maior número de empregos e estabelecimentos no setor de hospedagem, tem 51 municípios, incluindo as 27 capitais brasileiras. Este agrupamento concentra destinos turísticos tradicionais de nove estados brasileiros como Porto Seguro (BA), Ipojuca (Porto de Galinhas/PE), Armação de Búzios (RJ), Campos do Jordão (SP), Guarapari (ES), Balneário Camboriú (SC), Foz do Iguaçu (PR), Gramado (RS) e Caldas Novas (GO). O grupo responde por 47% da estimativa de fluxo turístico doméstico do Brasil e 82% do internacional.O grupo B tem 167 municípios, o equivalente a 5% das cidades categorizadas pelo Ministério do Turismo. São destinos turísticos de 20 estados, com participação expressiva de localidades das regiões Sudeste, Nordeste e Sul. Juntos os grupos A e B, representados por 218 municípios, respondem por 68% do fluxo doméstico brasileiro e 97% do internacional. Já o grupo C, com 504 municípios, representa 15% do total avaliado. O maior número de cidades do Mapa do Turismo, 2.623, ou 78% do conjunto avaliado concentram-se nos grupos D e E, que reúne municípios de menor fluxo de turistas e empregos formais no setor. A ideia é que, conhecidas as características de cada grupo de municípios, torna-se mais fácil proporcionar apoios adequados a cada um deles".


##### Hotéis  

Ainda no tema turismo, a Embratur mantém o [CADASTUR](http://dados.turismo.gov.br/cadastur): trata-se do "Cadastro de Pessoas Físicas e Jurídicas que atuam no setor de turismo. O Cadastro é obrigatório para os acampamentos turísticos,  agências de turismo, guias de turismo, parques temáticos, organizadoras de eventos, meios de hospedagem e  transportadoras turísticas e opcional para os restaurantes, cafeterias, bares e similares,  parques aquáticos e empreendimentos de lazer, locadoras de veículos para turistas, prestadoras especializadas em segmentos turísticos, casas de espetáculos, empreendimentos de apoio ao turismo náutico ou à pesca desportiva, prestadores de infraestrutura para eventos e centros de convenções".

Selecionei o cadastro de hotéis (meios de hospedagem) desde 2016 até o primeiro trimestre de 2019, e contabilizei o total de hotéis e quantidade de leitos, por município.

  
##### Agências Bancárias  

O Banco Central do Brasil mantém o [ESTBAN - Estatística Bancária Mensal por município](https://www.bcb.gov.br/estatisticas/estatisticabancariamunicipios), que é "gerado mensalmente com a informação da Estatística Bancária Mensal, contemplando a posição mensal dos saldos das principais rubricas de balancetes dos bancos comerciais e dos bancos múltiplos com carteira comercial, por município."

Os dados são de Fevereiro de 2019 e foram organizados da seguinte maneira: total de bancos, total de agências e total de ativos, por município, separando os indicadores para bancos públicos e bancos privados.
 
##### Assinantes de TV por assinatura e telefonia  

Um indicador muito interessante que incorpora população, tecnologia e renda, na minha opinião, é a quantidade de assinantes de TV por assinatura e telefonia.

No site da Agência Nacional de Telecomunicações ANATEL encontrei a [base com assinantes de TV por assinatura](https://cloud.anatel.gov.br/index.php/s/TpaFAwSw7RPfBa8?path=%2FTV_por_Assinatura%2FPor_Municipio) e a [base com assinantes de telefonia fixa](https://cloud.anatel.gov.br/index.php/s/TpaFAwSw7RPfBa8?path=%2FTelefonia_Fixa%2FPor_Municipio), por município, dados de Março de 2019. A base de telefonia móvel não estava aberta por municipio, na época.

##### Frota de veículos  

O Denatran, órgão do Ministério da Infraestrutura,  possui a estatística da [Frota de veículos por Município da Federação, por tipo e com placa](https://www.denatran.gov.br/estatistica/639-frota-2019) de Janeiro 2019.

Os veículos são classificados nas categorias: automóvel, bonde, caminhão, caminhão trator, caminhonete, camioneta, chassi plataf, ciclomotor, micro-ônibus, motocicleta, motoneta, ônibus, quadriciclo, reboque, semi-roboque, side-car, outros, trator esteira, trator rodas, triciclo, utilitário.

Adicionei à base: o total de automóveis, total de motocicletas, motonetas e ciclomotores e o total de tratores com rodas.


##### Índice de desenvolvimento humano  

E é claro, precisava incluir o Índice de Desenvolvimento Humano, um indicador bem popular baseado em três dimensões básicas do desenvolvimento humano: renda, educação e saúde/longevidade. No site das Nações Unidas no Brasil, há o [Ranking IDMH dos municípios brasileiros 2010](http://www.br.undp.org/content/brazil/pt/home/idh0/rankings/idhm-municipios-2010.html), que inclui o ranking geral e tambem o ranking considerando cada uma das três dimensões.
 

##### UBER  

Após pesquisa no site do [Uber](https://www.uber.com/en-BR/cities/), em Maio de 2019, adicionei um campo indicando se o Uber está presente ou não em cada um dos 5565 municípios.

##### Lojas Mac Donalds  

Após pesquisa no site do [MacDonalds](https://www.mcdonalds.com.br/enderecos) em Novembro de 2018, adicionei um campo indicando a quantidade de lojas do MacDonalds nos municípios.

##### Lojas Wallmart  

Após pesquisa no site do [Walmart Brasil](https://tabloide.walmartbrasil.com.br/) em Dezembro de 2018, adicionei um campo com a quantidade de lojas Wallmart nos municípios.

Atualização: em Agosto de 2019 a marca Walmart deixou o Brasil.

##### Agência dos Correios  

  
Rodei um scrapper (ou "raspador" - confesso que acho essa tradução muito estranha...) no site dos [Correios](http://www2.correios.com.br/sistemas/agencias/) para extrair a quantidade de agências em cada município. 

O scrapper utilizado está disponível [no meu repositório do Github](https://github.com/Cristianasp/scrappers).


## UMA PITADA DE PYTHON

Tanto os scrappers para os sites como o processamento das bases de dados do governto foram criados usando Python em Jupyter Notebook da distribuição Anaconda.

E já que são tabelas para filtrar, combinar e totalizar, nada melhor que contar com a ajuda da biblioteca Pandas, minha preferida.

Essas são algumas dicas e alguns fragmentos de código:


##### Tratamento de campos vazios, ou que deveriam ser vazios  

Cuidados especiais com campos vazios, NaN ou preenchidos com valores que representam vazio.

Importante definir um valor padrão para esses campos e garantir que todas as tabelas usam o mesmo valor.

Neste projeto, todos os campos vazios foram preenchidos com zero.

``` python
mask = df["IBGE_CROP_PRODUCTION_$"].isna()
df.loc[mask, "IBGE_CROP_PRODUCTION_$"] = 0

mask = df["IBGE_CROP_PRODUCTION_$"]== "..."
df.loc[mask, "IBGE_CROP_PRODUCTION_$"] = 0

mask = dg["IBGE_PLANTED_AREA"] == "-"
dg.loc[mask,"IBGE_PLANTED_AREA"] = 0
```

##### Tratamento dos campos usados para unificar as tabelas  

Os campos cidade e estado foram usados para unificar as tabelas.

É importante remover espaços em branco (strip), padronizar maísculas e minúsculas (title).

Neste projeto, precisei criar uma tabela adicional do tipo "de-para" para padronizar o nome de alguns municípios, pois aparecem escritos de maneira diferente em algumas bases de dados.

``` python
dg["CITY"] = dg["CITY"].str.strip()
dg["CITY"] = dg["CITY"].str.title()
dg["STATE"] = dg["STATE"].str.strip()
```

##### Mesclar tabelas  

A cada tabela adicionada era necessário fazer um "merge" com a base principal. 

A biblioteca pandas tem a função [merge](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.merge.html), que funciona de maneira similiar ao join do SQL.

``` python
df = df.merge(dg, on=["STATE","CITY"], how="outer")
```

##### A tabela dinâmica do pandas  

Pra quem usou muito tabela dinâmica do excel, a função [pivot_table](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.pivot_table.html) tem comportamento similar.

``` python
dg = dg.pivot_table(index=["CITY","STATE"], values="FIXED_PHONES",aggfunc="sum")

temp = dg.pivot_table(index=["STATE","CITY"], columns="PUBLIC_BANK", aggfunc={"BANK": "count", "AGENCIES":"sum", "TOTAL_ASSETS":"sum"}, fill_value=0)
```


Curtiu essa história? Deixe seu feedback ou entre em contato ;-)
