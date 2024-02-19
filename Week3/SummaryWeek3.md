# Processamento Neural de Língua e Representação de Palavras

## Vídeo 1:

Neste módulo, estudaremos como representar palavras de forma adequada para o processamento de textos em redes neurais. Para isso, é crucial transformar as sentenças em sequências de palavras que possam ser processadas eficientemente. O primeiro passo é a tokenização, que consiste em quebrar as sentenças em palavras ou tokens. Essa etapa é automatizada em frameworks como o `TensorFlow`, facilitando a extração dos tokens de uma sentença e a padronização do texto, como transformar todas as letras em minúsculas e remover a pontuação.

Uma vez tokenizadas, as palavras são transformadas em números para que as redes neurais possam processá-las. As redes neurais não entendem letras, apenas números, então é essencial essa conversão. No entanto, os códigos ASCII ou UTF-8, embora sejam padrões, não carregam informações sobre as palavras ou frases. Por isso, precisamos de representações mais ricas em informações.

Uma abordagem comum é o `One Hot Encoding`, que transforma cada palavra em um vetor onde apenas uma posição é 1 e as outras são 0. Por exemplo, para as palavras "eu", "gosto", "de" e "batata", teríamos vetores como [1, 0, 0, 0], [0, 1, 0, 0], [0, 0, 1, 0] e [0, 0, 0, 1]. Essa representação é limitada, pois o número de vetores diferentes é igual ao tamanho do vocabulário, o que pode ser muito grande em línguas como o português, com mais de 150 mil palavras. Isso resultaria em vetores muito esparsos e inadequados para o processamento eficiente de textos.

Nas próximas aulas, veremos outras formas mais eficientes de representar os vetores de palavras, evitando a explosão do número de vetores e tornando o processamento de texto mais eficaz.

## Vídeo 2: 

Nesta aula, exploramos diferentes maneiras de representar palavras para processamento de texto, buscando alternativas mais eficientes ao One Hot Encoding, que se mostrou ineficiente devido ao seu alto consumo de memória e à falta de consideração pela ordem das palavras.

A primeira abordagem alternativa é o "Bag of Words" (saco de palavras), onde cada sentença é representada como um vetor que indica a presença ou ausência de cada palavra do vocabulário, ignorando a ordem das palavras. Embora mais compacta, essa representação não captura a ordem das palavras na sentença.

Para enriquecer essa representação, podemos usar o `Count Vectorizer` para anotar a frequência com que as palavras ocorrem em uma sentença. Assim, cada palavra é representada pela sua frequência na sentença, embora a ordem das palavras ainda não seja considerada.

Além disso, podemos usar `N-grams` para representar trechos de sentenças, como bigramas (duas palavras consecutivas) e trigramas (três palavras consecutivas). Isso permite uma representação mais rica, capturando um pouco da ordem das palavras na sentença.

Outra abordagem é o uso de `TF-IDF` (Term Frequency-Inverse Document Frequency), que mede a importância de uma palavra em relação a um conjunto de documentos. O `TF-IDF` leva em conta não apenas a frequência da palavra em um documento, mas também a frequência da palavra em relação a todos os documentos, atribuindo um valor que indica a importância relativa da palavra no contexto dos documentos.

Essas representações alternativas são mais eficientes que o `One Hot Encoding` em termos de uso de memória e capturam mais informações sobre as palavras e suas relações nos textos. No entanto, ainda não capturam a similaridade entre palavras, que é um aspecto importante no processamento de texto e será abordado nas próximas aulas.

## Vídeo 3: Semântica Vetorial

Nesta parte do curso, exploramos a semântica vetorial de palavras, que é uma abordagem para representar o significado das palavras usando vetores em um espaço n-dimensional. Antes de entrar nos detalhes da semântica vetorial, é importante entender o conceito de semântica e como ela se relaciona com a sintaxe.

A semântica refere-se ao significado das palavras e das sentenças. Na linguística formal, a semântica é frequentemente definida em termos de composicionalidade, ou seja, o significado de uma sentença é uma composição dos significados de suas partes. Por exemplo, na frase "Marcelo está com fome", o significado da sentença é uma combinação dos significados de "Marcelo", "está", "com" e "fome".

A abordagem tradicional para a semântica formal envolve o uso de gramáticas formais e lógicas complexas para atribuir significado às sentenças. No entanto, esse tipo de abordagem é computacionalmente intensivo e muitas vezes difícil de aplicar em larga escala.

Em contraste, a semântica vetorial de palavras baseia-se na ideia de que palavras com significados semelhantes ocorrem em contextos semelhantes. Em vez de atribuir um significado específico a cada palavra, a semântica vetorial representa o significado de uma palavra por um vetor em um espaço n-dimensional, onde n é o número de dimensões do espaço vetorial.

Nesse espaço vetorial, palavras com significados semelhantes têm representações vetoriais próximas umas das outras. Por exemplo, as palavras "gato" e "gatinho" teriam representações vetoriais próximas, pois têm significados semelhantes. Da mesma forma, palavras que não têm relação semântica, como "gato" e "rocambole", teriam representações vetoriais distantes uma da outra.

Essa abordagem explora as propriedades dos espaços vetoriais no processamento de linguagem natural e é computacionalmente mais eficiente do que as abordagens tradicionais de semântica formal. Além disso, a semântica vetorial permite capturar nuances sutis de significado que não são facilmente expressas em termos de lógica formal.

Em resumo, a semântica vetorial de palavras é uma abordagem poderosa para representar o significado das palavras usando vetores em um espaço n-dimensional. Essa abordagem é simples, mas eficaz, e tem sido amplamente utilizada em diversas aplicações de processamento de linguagem natural.

## Vídeo 4: Embeddings

Nesta parte do curso, vamos discutir como representar palavras usando semântica vetorial e gerar essas representações por meio de embeddings. A ideia central é representar palavras como vetores em um espaço n-dimensional, onde palavras semelhantes têm vetores próximos.

Os embeddings são inserções de representações em um espaço de dimensão "n", onde cada palavra é representada por um ponto nesse espaço vetorial. A dimensão desse espaço é muito menor que o tamanho do vocabulário, por exemplo, 50, 100, ou até 1024. Esses valores são geralmente escolhidos de forma arbitrária, mas é preferível escolher valores que sejam múltiplos de dois ou de dez.

A distância entre dois vetores pode ser medida de várias maneiras, como a distância euclidiana, que é a mesma utilizada no teorema de Pitágoras. Outra medida comum é a similaridade de cosseno, que considera o ângulo entre os vetores. Se os vetores estão próximos, o cosseno é máximo, enquanto se são opostos, o cosseno é mínimo.

Para gerar embeddings, podemos usar uma tabela de pesquisa de embeddings, onde cada palavra do vocabulário está associada a um vetor. Também podemos usar redes neurais multicamadas para gerar embeddings com base em um conjunto de textos. Nesse caso, cada palavra é representada por um vetor gerado pela rede neural.

Além disso, é importante lidar com sentenças de comprimento variável ao processar texto. Para isso, utilizamos um token especial chamado de "PAD" para preencher as sentenças mais curtas e deixá-las com o mesmo comprimento das mais longas.

Por fim, quando nos deparamos com palavras que estão fora do nosso vocabulário, utilizamos o token "OOV" (Out of Vocabulary) para representá-las. Podemos criar diferentes classes de OOVs, dependendo da aplicação.

No próximo módulo, vamos explorar uma técnica muito poderosa chamada Word2Vec, que é amplamente utilizada para gerar embeddings de palavras.
