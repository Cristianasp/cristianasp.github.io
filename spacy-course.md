[BACK TO INDEX](https://cristianasp.github.io)

---

# NLP WITH SPACY

📅 Março, 2022

## Curso processamento avançado de Linguagem Natural com a biblioteca spaCy.

`#PLN` `#NLP` `#SPACY_IO`

A [spaCy](http://www.spacy.io) é uma biblioteca gratuita e de código aberto, criada para o desenvolvimento de aplicações para entendimento de linguagem natural. Entrega funcionalidades de marcação de classes gramaticais, termos sintáticos e identificação de entidades. Através de sua robusta API, é possível acessar seus métodos, propriedades e seus modelos estatísticos treinados em grandes bases de dados de diversos idiomas. É escrita em Python e Cython. O projeto existe desde 2015 e é liderado por Matthew Honnibal @honnibal e Ines Montani @_inesmontani. 

Em 2018 eu comecei a estudar PLN (Processamento de Linguagem Natural), ou NLP (em inglês). Nesta época, pouco se falava no assunto, pois todas as atenções estavam voltadas para Visão Computacional.

Fiz contato com a Ines e acabei me voluntariando para ajudar no projeto, especialmente no que tange à tradução dos materiais disponíveis para o Português. 

PLN é um campo de pesquisa que deve evoluir muito nos próximos anos. A cada semana surgem novos projetos, artigos são divulgados, novos algoritmos, novas aplicações, novas estratégias transferidas de outros campos de estudo de machine learning. Muita coisa interessante acontecendo.

Neste cenário de inovação semanal, a oferta de material em língua portuguesa é bastante restrita. Por isso entendo que disponibilizar um curso em português para estudantes ou profissionais que desejem se aprofundar no tema amplia as possibilidades do desenvolvimento de novas aplicações no Brasil.

O Curso está disponível [aqui](https://course.spacy.io/pt). 

Adicionalmente, gostaria de comentar sobre alguns desafios de traduzir textos técnicos para a língua portuguesa. Encontrar a palavra que melhor represente o significado em outra língua requer dedicação e um pouco de pesquisa. Não sou uma especialista em traduções. Vale observar que existem novos termos que são adotados diretamente do inglês para o português, ou que são abrasileirados, então sempre temos que decidir se vamos manter a palavra em inglês ou traduzir. Tampouco sou uma especialista em PLN, mas me interesso muito pelo assunto e já estudei e fiz alguns cursos e projetos.


Esses são alguns comentários dos desafios desta tradução de conteúdo técnico do inglês para o português.

"Segue o fio" ;-)

![](img/fofoca.png)
##### foto de unsplash.com/@benwhitephotography


#### Token  
Essa é dificil de traduzir. O sentido no texto é de uma unidade que foi particionada, ou extraída, de algo maior. Neste caso, estamos falando de palavras ou pontuações que foram extraídas de um texto. A tradução literal é símbolo, sinal ou ficha, mas definitivamente, nenhuma dessas palavras traduz o sentido de "text tokens". Sendo assim, decidi por manter token na versão em português, até porque token é muito usado aqui. Token tem seus filhos: root token, que traduzi como token raiz e head token, que traduzi como cabeçalho.

#### String  
Outra palavra difícil de traduzir. Corda, fio ou barbante de um texto ? É outra palavra que foi adotada para o português, pelo menos no que se refere à programação. Mantive string.

#### Span  
A tradução de span é o vão, alcance, período, espaço, extensão. No contexto de PLN, refere-se à um intervalo, ou um pedaço de um texto que é extraído. Depois de muita pesquisa, achei que "text span" poderia ser compreendido como "partição de texto". Na biblioteca spaCy, existe um objeto chamado Span, que define uma classe no spaCy, e então no texto inclui tanto a tradução como o original. Você encontrará: o objeto partição (span) do texto. 

#### Hash Code  
O termo hash é conhecido na computação. Hash code é o resultado da transformação de uma informação em outra, utilizando uma função. Normalmente códigos hash são usados para indexar ou mapear informações. No contexto do curso, o dicionário de palavras é mapeado em códigos hash, e esses são usados com o objetivo de melhorar o desempenho do processamento.

#### Label  
Esse é outro termo frequente em machine learning, onde dados que serão utilizados para treinamento de um modelo são rotulados, identificados ou classificados de alguma maneira. O "label" normalmente é traduzido como rótulo. No contexto do curso, as palavras, ou tokens, ou partições ou quaisquer outros objetos podem receber vários "labels", de acordo com o tipo de classificação desejada. Neste sentido, label está mais relacionado a um atributo do que um rótulo ou resumo. Sendo assim, optei pelo termo marcador (considerei a possibilidade de etiqueta também), que parece ter um sentido mais adequado do que rótulo.

#### Match  
Esse é um substantivo de tradução difícil. Muitas vezes utilizamos o termo em inglês : "deu match", já ouviram isso? O sentido da palavra match no curso é de ter correspondência, que me pareceu bastante adequado. Nunca usei, mas passarei a usar "correspondeu" ao invés de "deu match".

#### Matcher  
Depois de resolver "match", apareceu o "matcher", aquele que faz correspondências... o correspondedor? Acho que não. O sentido aqui é que o "matcher" é uma função que compara dois valores e verifica se eles são semelhantes. Então matcher ficou como comparador. Mas é um termo tão usado em português que na tradução mantive o termo em inglês também.

#### Lookup table  
O Comparador (Matcher) faz pesquisas em uma "lookup table" para realizar as comparações (match) e identificar as correspondências (matches). A tradução literal de lookup é olhar para cima. No contexto do curso, trata-se de uma lookup table, ou seja, uma tabela de consulta /pesquisa.

#### Pattern  
A tradução mais comum para pattern é padrão. No curso, cria-se um "pattern" para fazer correspondências em um texto. O ponto é que em português, padrão também é a tradução de "default" (valor padrão que deve ser adotado quando este não for definido) e achei que poderia confundir o aluno. Por isso, preferi usar o termo expressão ao invés de padrão. Afinal, uma expressão é a representação de uma idéia ou objetivo, que é o caso aqui.

#### Tagger  
O tagueador, aquele que adiciona marcações a um token. Mantive o original e o "abrasileirado".

#### Parser  
O analisador, que no contexto do curso é o analisador sintático (dependency parser). Mantive ambos pois o termo em inglês também é utilizado no dia a dia.

#### Tokenizer  
O toquenizador, aquele que pega um texto e extrai seus tokens. Mantive os dois também.

#### Part-of-speech tags  
São os marcadores de classe gramatical (substantivo, verbo, adjetivo, etc.) O termo em inglês não tem muita relação com o português.

#### Dependency labels  
São os termos sintáticos(sujeito, predicado, predicativo, etc.) A definição dos termos sintáticos é o resultado da análise de dependências ou análise sintatica.

#### Pipelines  
Tubos ou linha de canos? Ruim! Em computação normalmente a palavra pipeline é mantida em português, talvez porque pareça bem mais sério dizer: vamos processar o pipeline do que vamos processar o tubo! Mesmo assim, fiz algumas pesquisas com o objetivo de tentar traduzir pipeline para algo que representasse em português seu real significado: acabei usando "fluxos de processamento", mas mantive pipeline ao lado.

#### Streams  
Mais à frente no curso, aparece o conceito de Streams, que são fluxos otimizados que tem um melhor desempenho no processamento de grande volume de dados. Usei "fluxos".

#### Function or callable  
As traduções de callable que encontrei foram: exigível, resgatável. No contexto do curso, um objeto callable é aquele que pode ser chamado em um programa de computador. A tradução ficaria tão esquisita que preferi alterar ligeiramente o texto original e manter apenas o termo "objeto".

#### Keyword arguments  
Esses são parâmetros (ou argumentos) de uma função, que necessitam de uma keyword, ou palavra-chave, para distinguí-los. É bastante específico para a computação, e o melhor termo que encontrei foi parâmetros nomeados.

  
#### Getter and setter functions  
São também tão específicos de computação que foram mantidos no original.

#### Raise an error  
A tradução mais comum é gerar um erro. Ela não reflete exatamente o signficado de "raise", já que em um programa, quando um erro é "raise", ele é enviado para outros níveis do encadeamento de chamadas das funções, módulos ou programas, que estão acima deste em execução. Mas como este é o termo geralmente empregado, mantive-o.

#### Loop  
Particularmente, sempre achei esquisito "executar um laço do código", que é a tradução usual de loop. Eu prefiro loop. Mantive ambos.

#### Overfitting and Underfitting  
O processo de treinamento de um  modelo estatístico pode levá-lo a overfitting ou underfitting. O primeiro ocorre quando o treinamento é feito por demasiado, então o modelo se ajusta muito aos dados de treinamento e perde a capacidade de generalização com novos dados. O segundo é o contrário, quando o treinamento é pouco, e o modelo ainda não aprendeu os aspectos que permitem fazer previsões a partir dos dados. Encontrei a tradução de sobreajuste e subajuste. Entendo que são bons termos para se usar.

---

[BACK TO INDEX](https://cristianasp.github.io)

---

