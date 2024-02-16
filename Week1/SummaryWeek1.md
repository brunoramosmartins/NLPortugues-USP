# Introdução ao Processamento de Língua Natural e ao Curso

## Vídeo 1: Introdução

Resumo da Aula de Introdução ao Processamento de Linguagem Natural

**Estudo da Linguagem:** Começou na antiguidade clássica com foco nas línguas grega, latina e sânscrita.

No século XIX, surgiu uma visão unificadora da linguagem como um fenômeno do cérebro humano.
O processamento computacional da linguagem começou no século XX.

**Elementos da Língua:**

- Acústica: estudo dos sons e da produção da voz.
- Fonologia: estudo dos ritmos da linguagem.
- Fonemas: menores unidades sonoras com significado.
- Morfologia: estudo da estrutura das palavras.
- Sintaxe: estudo da combinação de palavras em frases.
- Semântica: estudo do significado das frases.
- Pragmática: estudo do uso da linguagem na prática.

Níveis de Análise Linguística:

- Lexical: palavras e seus significados.
- Sintático: estrutura das frases.
- Semântico: significado das frases.
- Pragmático: uso da linguagem na prática.

Visões sobre Sintaxe:

- Estrutura de árvore com constituintes (Chomsky, 1957).
- Estrutura de dependências entre as palavras (século XII).

Métodos Computacionais para Processamento de Linguagem Natural:

- Modelos baseados em regras gramaticais.
- Modelos probabilísticos.
- Modelos baseados em redes neurais artificiais (abordados em módulos posteriores).

Plano do Curso:

- Módulo 1: Modelos não neurais de processamento de linguagem natural.
- Módulos 2 a 5: Modelos neurais para processamento de linguagem natural.
- Módulo 6: Redes profundas para processamento de linguagem natural.

Observações:

Este curso se concentra na linguagem escrita. O foco está em modelos e métodos para o estudo computacional da linguagem.

Estudo da Linguagem:

- Começou na antiguidade clássica.
- Visão unificadora no século XIX.
- Processamento computacional no século XX.

Elementos da Língua:
- Acústica: sons e produção da voz.
- Fonologia: ritmos da linguagem.
- Fonemas: unidades sonoras com significado.
- Morfologia: estrutura das palavras.
- Sintaxe: combinação de palavras em frases.
- Semântica: significado das frases.
- Pragmática: uso da linguagem na prática.

Níveis de Análise Linguística:

- Lexical: palavras e seus significados.
- Sintático: estrutura das frases.
- Semântico: significado das frases.
- Pragmático: uso da linguagem na prática.

### Questionário

1. Em que época se consolidou a visão atual de Linguagem? R: Século 19
2. São áreas do estudo da Linguagem Humana: Fonética, Morfologia, Sintaxe.
3. A área da Sintaxe estuda os constituintes da sentença.
4. Sobre a estrutura sintática de uma sentença, pode-se dizer que:
    - A estrutura sintagmática analisa os constituintes da sentença;
    - A estrutura de dependência correlaciona as palavras da sentença;
    - Estruturas sintáticas não são observáveis.
5. São modelos computacionais de análise de linguagem:

    - Modelos lógicos baseados em regras;
    - Modelos probabilísticos ou estocásticos;
    - Modelos conexionistas ou neuronais.

## Vídeo 2: Modelos Lógicos

Resumo da Aula sobre Processamento de Linguagem Natural baseado em Regras

- O processamento baseado em regras foi o primeiro passo em direção à linguística computacional.
- A linguagem é um fenômeno humano, o que torna seu estudo diferente de outras ciências.
- As primeiras modelagens da linguagem foram simbólicas e não numéricas.
As gramáticas formais e a lógica categórica foram usadas para modelar a sintaxe e a semântica.
- Esse tipo de modelo tem grande expressividade, mas também alta complexidade computacional.

Gramáticas e Estrutura Frasal:

- Frases são compostas por unidades básicas (palavras) com categorias morfossintáticas (classes gramaticais).
- Regras de produção definem como categorias se combinam para formar unidades maiores (sintagmas).
- As gramáticas livres de contexto definem regras que não dependem do contexto.

Exemplos:

    - S -> SN SV (sentença é composta por sintagma nominal e sintagma verbal)
    - SN -> Det N (sintagma nominal é composto por determinante e substantivo)
    - SV -> V (sintagma verbal é composto por verbo)
    - V -> VTran (verbo transitivo)
    - VTran -> beijou (verbo transitivo específico)
    - Det -> o (determinante específico)
    - N -> vilão (substantivo específico)

Derivação Sintática e Árvores de Derivação:

- As regras de produção são aplicadas para gerar uma árvore de derivação sintática.
A árvore representa a estrutura da frase.

Exemplo: a frase "O vilão beijou a mocinha"
    
    - S
        -SN
            - Det
                - o
            - N
                - vilão
        - SV
            - VTran
                - beijou
            - SN
                - Det
                    - a
                - N
                    - mocinha

Ambiguidade Sintática:

- Uma mesma frase pode ter várias árvores de derivação e, portanto, vários significados.

* Exemplo: "Eu vi o menino com o telescópio"
    * Eu vi o menino que estava com o telescópio.
    * Eu usei o telescópio para ver o menino.

Hierarquia de Chomsky:

- As gramáticas livres de contexto podem ser usadas para modelar linguagens de programação.
- As gramáticas que lidam com contexto são complexas e, no geral, não computáveis.

Conclusão:

- O processamento baseado em regras foi um marco na história da linguística computacional.
- Apesar das suas limitações, as gramáticas formais fornecem uma base importante para o estudo da linguagem.

Anote os principais conceitos e definições.
Resuma as diferentes formas de regras gramaticais.
Descreva o processo de derivação sintática.
Explique o que é ambiguidade sintática.
Discuta as vantagens e desvantagens do processamento baseado em regras.

Gramáticas:
- Regras de produção definem como categorias se combinam.
- Gramáticas livres de contexto não dependem do contexto.
- Exemplos de regras: S -> SN SV, SN -> Det N, etc.

Derivação Sintática:

- Árvores representam a estrutura da frase.
- A partir das regras, gera-se a árvore de derivação.

Ambiguidade Sintática:

- Uma frase pode ter vários significados.
- Exemplo: "Eu vi o menino com o telescópio".

Processamento baseado em regras:

- Primeiro passo em direção à linguística computacional.
- Vantagens: expressividade, base para o estudo da linguagem.
- Desvantagens: complexidade computacional, limitações para lidar com contexto.

1. Sobre o formalismo matemático utilizado no estudo da  língua,  podemos afirmar que: A matemática da língua precisa ser inventada à medida que os estudos avançam.
2. Sobre a estrutura da frase, não é correto afirmar que: A palavra é unidade base da frase
    - A cada palavra atribui-se uma categoria morfossintática
    - O léxico é um conjunto de regras que relaciona  palavras a categorias morfossintáticas na forma de uma regra de produção.
    - Um sintagma é um trecho de uma sentença que possui significado próprio.
    - Cada tipo de palavra pode ter apenas  uma única categoria morfossintática atribuída a ela.
3. Sintagmas são sequências de palavras que formam um novo elemento na estrutura da frase.   Sobre eles podemos afirmar que: Sintagmas são estruturas autônomas que podem  ocorrer em diversos pontos de uma sentença
4. Sobre as Gramáticas Livres de Contexto, assinale todas as alternativas corretas
    - As regras de uma Gramática Livre de Contexto possuem apenas uma categoria sintática à cabeça.
    - O corpo de uma regra de  uma Gramática Livre de Contexto contémum ou mais categorias sintáticas ou morfossintática
    - Uma sentença pode ter mais de uma árvore sintática, o que constitui um caso de ambiguidade sintática

## Vídeo 3: Modelos Probabilísticos

Resumo da Transcrição da Aula sobre Modelos Probabilísticos de Processamento de Linguagem Natural

- A aula aborda modelos probabilísticos para processamento de linguagem natural (PLN).
- A probabilidade é definida como um resumo que encapsula uma configuração, geralmente a probabilidade de algo dado outras condições.
- Diferentes modelos probabilísticos escolhem diferentes tipos de parâmetros e focam em diferentes aspectos da linguagem.

Modelos Markovianos

- Modelos de transição de estados, onde a probabilidade de um estado depende apenas do estado anterior.
- Exemplo: Cadeia de Markov para modelar o mercado (alta, baixa, estagnado) com probabilidades de transição entre os estados.
- Usado em PLN para etiquetagem morfossintática (determinação da classe gramatical de cada palavra).
- Modelos de ordem 2 consideram os dois estados anteriores.
- Limitações: crescimento exponencial do número de estados com o tamanho da janela e insensibilidade ao contexto fora da janela.
- Algoritmo de Viterbi para encontrar a sequência de etiquetas mais provável.

N-gramas

- Ignoram a sequência de palavras e tratam o texto como um "saco de palavras".
- Unigramas: contagem de ocorrências de cada palavra.
- Bigramas: contagem de sequências de duas palavras.
- Trigramas: contagem de sequências de três palavras.
- N-gramas com n maior que 3 são raros.
- Exemplo: análise de sentimento com bigramas.
- Aprendizado supervisionado: treinamento com um corpus de textos com sentimento pré-classificado.

Gramáticas Probabilísticas

- Atribuem probabilidades a regras gramaticais para resolver ambiguidades sintáticas.
- A soma das probabilidades das regras com a mesma cabeça é 1.
- Probabilidade da árvore de derivação sintática: produto das probabilidades das regras utilizadas.
- Escolha da árvore com maior probabilidade.
- Limitações: suposição de independência entre regras e incapacidade de capturar interdependências de longo alcance no contexto.

Modelos Probabilísticos Avançados

- Usados em tradução automática antes das redes neurais.
- Alinhamento de textos paralelos (original e tradução) para calcular probabilidades de tradução entre palavras.
- Treinamento supervisionado com grandes quantidades de dados.

Modelos probabilísticos são ferramentas importantes para PLN, mas possuem limitações.
Redes neurais com arquitetura Encoder-Decoder serão abordadas em aulas futuras.

Modelos probabilísticos:
- Encapsulam configurações e fornecem probabilidades de eventos.
- Diferentes tipos de modelos focam em diferentes aspectos da linguagem.

Cadeias de Markov:
- Modelos de transição de estados.
- Úteis para etiquetagem morfossintática.
- Limitados pelo tamanho da janela de contexto.

N-gramas:
- Modelam o texto como um "saco de palavras".
- Úteis para análise de sentimento.
- N-gramas com n maior que 3 são raros.

Gramáticas probabilísticas:
- Atribuem probabilidades a regras gramaticais para resolver ambiguidades.
- Limitadas pela suposição de independência entre regras.
- Lembre-se de adaptar as anotações ao seu estilo de estudo e às suas necessidades.

1. Sobre as probabilidades podemos afirmar que: Concentram expressivamente em um único número toda uma configuração linguística.
2. Sobre as cadeias de makov, marque todas as alternativas que estiverem corretas:
    - São modelos probabilísticos cujos parâmetros são transições probabilísticas entre estados aleatórios.
    - No processamento de linguagem natural, as cadeias de markov permitem computar a sequência mais provável de palavras.
    - Aplicações de cadeias de markov incluem a etiquetagem morfossintática
3. Sobre os modelos probabilísticos de n-gramas, marque todas as alternativas corretas.
    - A análise de sentimento calcula a probabilidade de algum sentimento (positivo/negativo/neutro) a partir das probabilidades dos n-gramas.
    - O aprendizado supervisionado de modelos de n-gramas ocorre por meio de contagem e cálculo de elementos de interesse em sentenças previamente classificadas.

## Vídeo 4: Problemas I

Conceitos Fundamentais: Antes de abordar os problemas de processamento de linguagem natural (PLN), é importante definir o conceito de "palavra". Existem dois tipos de conceitos relacionados às palavras: ocorrências de palavras e tipos de palavras. Ocorrências são cada uma das palavras que aparecem escritas nos textos, enquanto tipos são as palavras independentemente de sua ocorrência nos textos. Por exemplo, no texto "o menino viu o vizinho", há quatro ocorrências de palavras (ou "tokens"): "o", "menino", "viu" e "vizinho", mas apenas quatro tipos de palavras, uma vez que "o" ocorre duas vezes.

Corpus: "Corpus" é uma coleção de textos ou outras mídias, como áudios e vídeos. Existem vários tipos de corpus, como o de texto puro (sem anotações) e o anotado, que pode conter marcações gramaticais, sentimentos, entre outros. Os corpus também podem ser paralelos, indicando relações entre textos, como traduções.

Pré-processamento de Texto: Antes de aplicar modelos matemáticos no PLN, é necessário realizar o pré-processamento dos dados. Isso inclui a tokenização (extração das palavras), filtragem (remoção de elementos indesejados, como etiquetas), identificação de pontos finais (para separar sentenças) e expansão de abreviações (transformar abreviações em suas formas completas).

Problemas comuns no Pré-processamento:

Tokenização: Extrair as palavras de um texto.
Filtragem: Remover elementos indesejados, como etiquetas.
Identificação de Pontos Finais: Determinar quais pontos indicam o final de um período.
Expansão de Abreviações: Transformar abreviações em suas formas completas.
Separação de Sentenças: Identificar o final de uma sentença, mesmo com pontuação incorreta.
Extração de Stop-words: Remoção de palavras comuns que não agregam significado ao texto.
Importância do Pré-processamento: Apesar de muitas vezes ser considerado simples, o pré-processamento é uma etapa fundamental e consome a maior parte do tempo no processamento de linguagem natural, pois é crucial para preparar os dados de forma adequada para os modelos matemáticos.

Considerações Finais: A escolha dos métodos de pré-processamento depende da aplicação e do modelo matemático utilizado. Em modelos probabilísticos, a extração de stop-words era comum, mas em redes neurais, essa prática é menos utilizada.

Esses são os principais pontos abordados na aula sobre processamento de linguagem natural.