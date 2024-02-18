# Introdução as Redes Neurais

## Vídeo 1: Modelos Neurais - Percéptons

1. Aprendizado Supervisionado: É mencionado que o aprendizado supervisionado é usado, onde fornecemos dados de entrada e saída para que o modelo aprenda uma função que melhor se adeque aos dados. Os dados de entrada podem ser multi-dimensionais, como palavras em textos, e os de saída podem ser valores contínuos ou classes categóricas.

2. Tipos de Aprendizado: Existem dois tipos básicos de aprendizado supervisionado: regressão, quando a saída é um valor contínuo, e classificação, quando a saída é uma classe dentre várias.

3. Exemplos de Métodos de Aprendizado: São mencionados métodos como o KNN e árvores de decisão, mas o curso focará em redes neurais.

4. Perceptron: O perceptron é apresentado como um classificador linear que tenta separar os dados com um hiperplano. Ele utiliza a função sinal para determinar o lado do hiperplano em que os dados estão.

5. Limitações do Perceptron Clássico: O perceptron clássico tem dificuldade em lidar com dados não linearmente separáveis, pode gerar hiperplanos com margens pequenas, levando a uma baixa generalização, e não fornece medidas de confiança sobre o aprendizado.

O vídeo enfatiza a importância do aprendizado supervisionado e suas aplicações em problemas do mundo real, como processamento de linguagem natural. Destaca as limitações do perceptron clássico, preparando o espectador para entender a necessidade de métodos mais avançados, como o perceptron probabilístico.

### Percéptons

Exemplo de Perceptron Funcionando:
Vamos criar um conjunto de dados linearmente separável e usar um perceptron para classificá-lo. Este é um exemplo onde o perceptron funciona bem.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_blobs, make_circles
from sklearn.model_selection import train_test_split
from sklearn.linear_model import Perceptron
from sklearn.metrics import accuracy_score

# Criar conjunto de dados linearmente separável
X, y = make_blobs(n_samples=100, centers=2, random_state=42)

# Dividir o conjunto de dados em treino e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=42)

# Criar e treinar o perceptron
perceptron = Perceptron()
perceptron.fit(X_train, y_train)

# Fazer previsões
y_pred = perceptron.predict(X_test)

# Calcular acurácia
accuracy = accuracy_score(y_test, y_pred)
print("Acurácia:", accuracy)

# Plotar o conjunto de dados e a linha de decisão do perceptron
plt.figure(figsize=(8, 6))
plt.scatter(X[:, 0], X[:, 1], c=y, cmap=plt.cm.Paired)
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')

# Plotar a linha de decisão
x_values = np.array([X[:, 0].min(), X[:, 0].max()])
y_values = -(perceptron.coef_[0][0] * x_values + perceptron.intercept_) / perceptron.coef_[0][1]
plt.plot(x_values, y_values, '--', color='red')
plt.title('Perceptron para dados linearmente separáveis')
plt.show()

```

Exemplo de Perceptron Ineficiente:
Vamos criar um conjunto de dados não linearmente separável e tentar usar um perceptron para classificá-lo. Neste caso, o perceptron não será capaz de encontrar uma linha de decisão que separe os dados de forma eficiente.

```python
# Criar conjunto de dados não linearmente separável
X, y = make_circles(n_samples=100, noise=0.1, factor=0.5, random_state=42)

# Dividir o conjunto de dados em treino e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=42)

# Criar e treinar o perceptron
perceptron = Perceptron()
perceptron.fit(X_train, y_train)

# Fazer previsões
y_pred = perceptron.predict(X_test)

# Calcular acurácia
accuracy = accuracy_score(y_test, y_pred)
print("Acurácia:", accuracy)

# Plotar o conjunto de dados e a linha de decisão do perceptron
plt.figure(figsize=(8, 6))
plt.scatter(X[:, 0], X[:, 1], c=y, cmap=plt.cm.Paired)
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')

# Não é possível plotar uma linha de decisão para o perceptron neste caso

plt.title('Perceptron para dados não linearmente separáveis')
plt.show()

```

Lógica do algoritmo 

```python
import numpy as np

class Perceptron:
    def __init__(self, learning_rate=0.1, n_iterations=1000):
        self.learning_rate = learning_rate
        self.n_iterations = n_iterations
        self.weights = None
        self.bias = None
    
    def fit(self, X, y):
        n_samples, n_features = X.shape
        # Iniciando os pesos com zeros
        self.weights = np.zeros(n_features)
        self.bias = 0

        # Treinamento do perceptron
        for _ in range(self.n_iterations):
            for idx, x_i in enumerate(X):
                linear_output = np.dot(x_i, self.weights) + self.bias
                y_predicted = self.step_function(linear_output)
                update = self.learning_rate * (y[idx] - y_predicted)
                self.weights += update * x_i
                self.bias += update
    
    def predict(self, X):
        linear_output = np.dot(X, self.weights) + self.bias
        y_predicted = np.where(linear_output >=0, 1, 0)
        return y_predicted
    
    def step_function(self, x):
        return 1 if x >= 0 else 0
```

## Vídeo 2: Percéptrons

O vídeo aborda os perceptrons probabilísticos como uma evolução dos perceptrons clássicos, destacando três problemas dos perceptrons clássicos: lidavam apenas com dados linearmente separáveis, tinham margens pequenas e não forneciam medidas de confiança para as classificações. Em seguida, o vídeo explora a ideia de margens pequenas, mostrando que pontos muito próximos à linha de separação podem ter confiança diferente de pontos mais distantes.

Para resolver esses problemas, é introduzida a ideia de perceptrons probabilísticos, que atribuem probabilidades às classificações. A probabilidade é calculada usando uma função sigmoide, onde valores positivos levam a probabilidades próximas de 1 e valores negativos levam a probabilidades próximas de 0. A função sigmoide também é capaz de fornecer uma medida de confiança para as classificações.

O vídeo também aborda a questão da separabilidade não linear, mostrando que mesmo quando os dados não podem ser separados por um hiperplano no espaço original, é possível encontrar uma transformação não linear dos dados para um espaço onde a separação é possível. Isso é ilustrado com um exemplo de dados em forma de círculos que são separados por uma transformação para um espaço tridimensional.

Por fim, é mencionado que as transformações não lineares podem ser caras computacionalmente, então é importante encontrar transformações que sejam eficientes. A solução é utilizar redes neurais multicamadas, que são compostas por vários perceptrons e são capazes de aprender transformações não lineares dos dados. Essa abordagem será explorada no próximo segmento do curso.

## Vídeo 3: Redes Feed Forward Multicamadas

O vídeo aborda as redes neurais multicamadas, mostrando como elas surgem como uma extensão dos perceptrons clássicos para lidar com problemas como a função OU exclusivo, que não pode ser aprendida por um único perceptron devido à sua natureza não linear.

Para resolver esse tipo de problema, é introduzida a ideia de Perceptrons Multicamadas, que consistem em múltiplas camadas de neurônios artificiais. Cada neurônio artificial realiza uma soma ponderada das entradas, adiciona um viés e passa o resultado por uma função de ativação não linear, como a função sigmoide, tangente hiperbólica ou ReLu (Rectified Linear Unit). Essas funções introduzem a não linearidade necessária para lidar com problemas mais complexos.

A arquitetura de uma rede neural multicamada é representada por várias camadas de neurônios, onde cada camada se conecta completamente à camada seguinte. A primeira camada é a camada de entrada, seguida por uma ou mais camadas ocultas (intermediárias) e, finalmente, a camada de saída. Os pesos e os viéses de cada neurônio são os parâmetros que a rede aprende durante o treinamento para realizar a classificação ou regressão desejada.

É destacado que redes neurais multicamadas com funções de ativação não lineares são capazes de aproximar qualquer função contínua com precisão arbitrária, tornando-as poderosas ferramentas para aprendizado de máquina e reconhecimento de padrões.

A representação matricial das redes neurais multicamadas simplifica a compreensão do seu funcionamento, mostrando como cada camada é uma transformação dos dados da camada anterior por meio de uma matriz de pesos. O processo de treinamento envolve ajustar essas matrizes de pesos para minimizar a diferença entre as saídas previstas e as saídas reais, utilizando técnicas como o algoritmo de retropropagação.

Em resumo, as redes neurais multicamadas são uma evolução dos perceptrons clássicos, capazes de lidar com problemas complexos e realizar aprendizado de máquina poderoso.

## Vídeo 4: Função custo (_LOSS_)

O vídeo trata do treinamento de redes neurais multicamadas, explicando como os pesos das matrizes são aprendidos durante o processo. Inicialmente, é definida uma função de custo, também chamada de 'loss', que mede a diferença entre a previsão da rede ('y chapéu') e o valor desejado ('y') para os dados de treinamento.

O objetivo do treinamento é minimizar essa função de custo, o que é feito através do método do gradiente descendente. Nesse método, os pesos da rede são atualizados iterativamente com base no gradiente da função de custo em relação a esses pesos. Isso significa que, para cada peso na rede, é calculada a derivada parcial da função de custo em relação a esse peso e esse valor é usado para atualizar o peso na direção que reduz a função de custo.

O algoritmo de backpropagation é fundamental para calcular esses gradientes de forma eficiente. Ele consiste em três partes principais: a propagação para frente (forward pass), onde os dados são passados pela rede e a previsão é calculada; o cálculo da função de custo; e a propagação para trás (backward pass), onde os gradientes são calculados e os pesos são atualizados.

Durante o treinamento, os dados de entrada são passados pela rede em batches (conjuntos) e os pesos são atualizados após cada batch. Uma época é completada quando todos os dados foram vistos uma vez. A taxa de aprendizado ('alfa') é um hiperparâmetro que precisa ser ajustado empiricamente e determina o tamanho dos passos dados na direção do gradiente.

Além disso, são mencionadas técnicas como normalização e regularização, que são usadas para evitar problemas como valores extremamente altos ou baixos nos dados e ajudam a suavizar a função de custo. Existem também otimizadores diferentes que podem ser usados para treinar a rede de forma mais eficiente, evitando mínimos locais e problemas de overfitting e underfitting.

O vídeo encerra anunciando que no próximo módulo será abordada a representação de palavras para começar a processar textos.