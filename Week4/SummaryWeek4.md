# Word2Vec

## Vídeo 1: O modelo word2vec Básico de Embedding

Apresentamos um método muito importante chamado `Word2vec`, que é responsável por transformar palavras em vetores de entrada. Esses vetores serão usados para diversas tarefas de processamento de texto. Vamos começar explicando o modelo básico do `Word2vec`.

O objetivo do `Word2vec` é gerar uma representação vetorial das palavras. Para isso, utilizamos uma representação _one-hot_, que é uma representação enorme que tem o tamanho do vocabulário, com apenas uma posição representando a palavra e todas as outras posições sendo zero. A ideia é gerar um vetor de tamanho arbitrário, representado aqui como "n", que pode ser 50, 100, 64, 128, ou qualquer outro número arbitrário.

O método é de aprendizado não supervisionado, onde aprendemos essa representação fornecendo uma grande quantidade de textos, ou seja, palavras de contexto. Geralmente, usamos centenas de milhões de palavras ou até bilhões em alguns casos. O modelo é baseado na co-ocorrência estatística, ou seja, palavras que ocorrem em contextos semelhantes terão representações muito parecidas.

Existem dois modelos principais do `Word2vec`: `skip-gram` e `continuous bag-of-words` (CBOW). No modelo `CBOW`, o contexto é apenas uma palavra, que é a palavra que ocorre depois da palavra foco. Por exemplo, se a palavra foco é "rei", então "primeiro" seria o contexto. A ideia é fornecer o contexto e prever a palavra foco.

O modelo utiliza duas matrizes: uma que transforma a representação _one-hot_ do contexto em uma representação vetorial intermediária, e outra que transforma essa representação intermediária na representação _one-hot_ da palavra foco. A ideia é aprender os pesos da primeira matriz, que transforma o contexto em uma representação interna.

O modelo `CBOW` é representado por uma rede neural com duas camadas: uma camada de entrada, que recebe a representação _one-hot_ do contexto, e uma camada de saída, que gera a palavra foco. O modelo `skip-gram` é semelhante, mas ao contrário: a entrada é a palavra foco e a saída é o contexto.

Para treinar o modelo, utilizamos a função softmax para transformar os vetores de números em distribuições de probabilidade. Em seguida, calculamos a entropia cruzada para minimizar a diferença entre a distribuição de probabilidade estimada e a distribuição ideal, que é 1 na posição da palavra foco e 0 nas outras.

1. Qual é o objetivo do método word2vec? R: Pré-processar palavras para transformá-las em vetores de valores para posterior uso em processamento de texto.
2. O modelo word2vec contém duas variantes, sobre quais podemos afirmar:
    - Os modelos se chamam Continuous bag of words (CBOW) e Skip-gram.
    - No modelo Skip-gram,  uma palavra prevê quatro palavras vizinhas.
    - No modelos CBOW,  quatro palavras vizinhas preveem uma palavra central.
    - Ambos os modelos  são baseados em um produto de matrizes.

3. A entrada do modelo word2vec   básico consiste de:
    - Um vetor codificado no formato 1-hot.

4. No modelo  word2vec,  cada palavra é associada a uma codificação,  sobre a qual podemos afirmar que:
    - A codificação aparece na camada oculta intermediária.

5. No modelo word2vec básico a entropia cruzada é a função de perda (loss).

## Vídeo 2: word2vec Básico Detalhado

Uma vez apresentado o modelo básico, vamos detalhar como ele pode ser treinado. No modelo CBOW do Word2vec, a entrada que representa o contexto é multiplicada por uma matriz, gerando uma camada intermediária oculta. Essa camada é então multiplicada por outra matriz, cuja saída é aplicada à função softmax e comparada com a palavra foco, que é representada como one-hot.

A camada intermediária é calculada como a soma dos produtos dos pesos pelos parâmetros de entrada. Em seguida, essa camada intermediária é multiplicada pela matriz W linha, gerando o vetor de saída u. Esse vetor u é então aplicado à função softmax para gerar uma distribuição de probabilidade para cada palavra do vocabulário, dada a palavra de entrada como contexto.

A loss é calculada usando a entropia cruzada, que compara a distribuição de probabilidade estimada com a distribuição ideal, que é 1 na posição da palavra foco e 0 nas outras. A loss é minimizada através da retropropagação.

No modelo CBOW simplificado, como a entrada e a saída são vetores one-hot, a camada intermediária é simplesmente uma cópia do vetor de entrada. A loss também é simplificada, resultando em uma fórmula mais direta para o cálculo da atualização dos pesos.

Para atualizar os pesos, primeiro atualizamos os pesos da matriz W linha, subtraindo a taxa de aprendizado multiplicada pelo erro entre a saída do softmax e o vetor one-hot da palavra de saída. Em seguida, atualizamos os pesos da matriz W, multiplicando a matriz W linha atualizada pela matriz D e subtraindo o resultado da matriz W original.

Esse é o processo de treinamento do modelo CBOW do Word2vec, onde palavras que ocorrem em contextos semelhantes terão vetores de representação muito parecidos.

1. Sobre o detalhamento do modelo word2vec,

    - A camada intermediária é a codificação  da palavra  cuja  versão 1-hot  é apresentada na entrada.
    - A soma dos elementos da  transformação softmax (y)  sempre vale 1.
    - Apenas uma dimensão do vetor de saída é levado em consideração para o cálculo da entropia cruzada.
    - Atualização dos pesos no processo de  treinamento pode ser reduzido a um conjunto de operações matriciais.
    - A distância cosseno mede a similaridade de duas representações  vetoriais,  ou seja,  quanto maior esse valor mais similar são as palavras.

## Vídeo 3: O modelo CBO Completo

O modelo _Continuous Bag of Words_ (`CBOW`) completo é uma extensão do modelo básico que visa prever a palavra alvo com base em um contexto de palavras ao redor dela. Enquanto o modelo básico considera apenas uma única palavra de contexto, o modelo completo permite um contexto de tamanho arbitrário, representado por `c` palavras antes e depois da palavra alvo.

No modelo CBOW completo, o contexto é tratado como um "saco de palavras" (_bag of words_), onde a ordem das palavras não importa, apenas a ocorrência delas no contexto. Essa representação é obtida somando os vetores `one-hot` das palavras do contexto. Esse vetor soma é então dividido pelo tamanho do contexto, o que resulta em um vetor intermediário que é multiplicado pela matriz de pesos `W` para gerar a saída final. A saída é então comparada com o vetor `one-hot` da palavra alvo para calcular a perda (_loss_).

Uma das dificuldades do modelo completo é o cálculo da função `softmax`, especialmente em vocabulários grandes, onde o custo computacional pode ser elevado. Para contornar esse problema, técnicas como softmax hierárquico ou amostragem negativa são utilizadas. Essas técnicas simplificam o cálculo da função `softmax`, tornando o treinamento do modelo mais eficiente em termos computacionais.

Em resumo, o modelo CBOW completo é uma extensão do modelo básico que permite um contexto de tamanho variável e utiliza técnicas para tornar o cálculo da função softmax mais eficiente em vocabulários grandes.

## Vídeo 4: Eficiência no word2vec

O modelo Continuous Bag of Words (CBOW) do Word2vec pode ser otimizado para melhorar sua eficiência computacional. No treinamento do modelo normal, para cada conjunto de contexto/palavra, todas as colunas da matriz de pesos "W" são atualizadas. Isso pode ser ineficiente, pois muitas dessas atualizações são pequenas e poderiam ser aproximadas para zero. Para contornar isso, é possível atualizar apenas algumas colunas de "W" para cada par contexto/palavra, em vez de todas.

A ideia básica é reduzir a largura do modelo, que possui 150 mil palavras, para que o cálculo da camada intermediária, da camada escondida H e da camada final seja mais eficiente. Isso é importante, pois o cálculo da função softmax na camada final é computacionalmente custoso. Para isso, é utilizada a técnica de amostragem negativa.

Na amostragem negativa, para cada par contexto/palavra, algumas palavras são escolhidas aleatoriamente entre as que não ocorrem no contexto para serem atualizadas. Isso é feito com base em uma distribuição de probabilidade proporcional ao número de vezes que cada palavra ocorre no corpus. Essa técnica reduz drasticamente o número de atualizações necessárias, tornando o treinamento do modelo mais eficiente.

Assim, ao invés de atualizar as 150 mil colunas de "W" para cada par contexto/palavra, apenas algumas colunas são atualizadas, o que melhora significativamente a eficiência do método. Isso torna o aprendizado mais econômico, focando nas palavras relevantes e nas amostradas negativamente a cada iteração. Essa abordagem permite que o Word2vec seja treinado de forma eficiente, resultando em representações vetoriais semelhantes para palavras que aparecem em contextos semelhantes.

1. Sobre o modelo word2vec completo,
    - O modelo CBOW  completo leva em consideração quatro palavras de contexto.
    - Os vetores das palavras de contexto  são  somados na entrada.   
    - O valor da camada escondida é dividido pelo número de vetores de contexto utilizados.  
    - Como no caso  básico, a soma dos elementos da  transformação softmax (y)  sempre vale 1.  
    - Se seguirmos o cálculo da  função de perda do caso básico, haverá uma grande  perda de eficiência.  
    - A amostragem negativa é um  método de compensar essa perda de eficiência. 
    - O modelo word2vec é muito mais largo que profundo.

## Avaliação do word2vec

O Word2vec é um modelo poderoso para criar representações vetoriais de palavras, mas sua qualidade precisa ser avaliada para garantir que as representações capturam efetivamente as relações semânticas entre as palavras. Existem duas principais formas de avaliar o Word2vec: a avaliação intrínseca e a avaliação extrínseca.

A avaliação intrínseca envolve operações diretas nos vetores de palavras para verificar se as relações semânticas são capturadas corretamente. Por exemplo, se o vetor da palavra "França" menos o vetor da palavra "Paris" é similar ao vetor da palavra "Japão", isso indica que o modelo capturou a relação de capitalidade entre países. Da mesma forma, se o vetor da palavra "mulher" menos o vetor da palavra "homem" é similar ao vetor da palavra "rainha", isso indica que o modelo capturou a relação de gênero entre palavras.

No entanto, a avaliação intrínseca pode revelar problemas no modelo, como viéses e estereótipos presentes nos dados de treinamento. Por exemplo, se aplicarmos a mesma operação de vetorização para palavras como "feio" e "branco", esperaríamos que a palavra "negra" fosse o resultado, mas o modelo pode produzir resultados indesejados devido a tendências raciais ou sexistas nos dados.

A avaliação extrínseca envolve usar as representações vetoriais do Word2vec em tarefas reais, como reconhecimento de entidades mencionadas (Named Entity Recognition), para ver se o modelo melhora o desempenho dessas tarefas. Isso permite uma avaliação mais prática da utilidade do Word2vec em aplicações reais.

Além disso, existem outros tipos de embeddings pré-treinados, como o GloVe, que são baseados em probabilidades de coocorrência das palavras no texto. Esses embeddings são mais simples do que o Word2vec, não envolvendo redes neurais ou multiplicação de matrizes, e podem ser uma opção útil em determinados contextos.

Em resumo, a avaliação do Word2vec envolve testar se as representações vetoriais capturam efetivamente as relações semânticas entre as palavras, ao mesmo tempo em que se considera possíveis viéses e estereótipos nos dados de treinamento. A avaliação intrínseca e extrínseca são ferramentas importantes para garantir a qualidade e a utilidade do modelo.