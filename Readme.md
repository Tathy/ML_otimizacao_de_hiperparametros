# :chart_with_upwards_trend: Machine Learning parte 1: Otimização de modelos através de hiperparâmetros

[Link do Google Colab (parte 1)](https://colab.research.google.com/drive/1zkmLyzgb1jqOybg_ZRvQR9_uk0_AIYHr?usp=sharing)

[Link do Google Colab (parte 2)](https://colab.research.google.com/drive/1DDqL4WoLeOMauQwrYOxvWIFGpMCKMX5x?usp=sharing)

* Este estudo é uma continuação do estudo de [Validação Cruzada](https://github.com/Tathy/ML_validacao-de-modelos).

* **Base de Dados:** Características físicas de alguns carros que estão ou estiveram à venda, seus preços de venda, e se foram vendidos ou não. Site de vendas fictício.

## Profundida máxima de uma árvore

* O primeiro hiperparâmetro estudado foi o max_depth do algoritmo DecisionTree, que pode sofrer overfit caso seja muito alto.

![graph_cross_validate_mean_scores](https://github.com/Tathy/ML_otimizacao_de_hiperparametros/blob/main/img/graph_cross_validate_mean_scores.png?raw=true)

* O modelo fica "viciado" nos valores das features de treino e acaba classificando erroneamente as entradas de teste. 

* Neste caso, a árvore que melhor classificou os dados foi a de profundidade máxima 3.

## Exploração de mais dimensões

* A visualização de duas dimensões ainda é viável, mas a análise com três ou mais já se torna mais complicada.

* Além disso, ainda há o aumento exponencial do tempo gasto, dependente do espaço de busca escolhido.

## Simplificando o processo de busca

* Para simplificar código escrito e melhorar a legibilidade, é utilizado o GridSearchCV.

* Esta é uma busca exaustiva, então não há tanta economia de recurso em comparação com a busca "manual", feita com uma e duas dimensões anteriormente.

* Depois de encontrar o melhor modelo indicado pelo GridSearch, ainda é necessário fazer mais uma validação cruzada, com um cálculo de uma margem de taxa de acerto. Esta segunda validação é chamada Nested Cross-Validation.

### Conclusões

* A busca utilizando grid é um processo demorado até se encontrar um bom resultado e não tem garantia de encotrar um modelo ótimo para um dado dataset.

* Ainda existem otimizações e análises que podem ser feitas.

# :chart_with_upwards_trend: Parte 2: Otimização com exploração aleatória

## Busca aleatória

* Foi utilizado o Randomized Search CV.

* Define-se um espaço de parâmetros e uma quantidade de iterações que o algoritmo deve executar, menor do que o espaço completo.

* A exploração é feita a quantidade de vezes definida, portanto nem todo o espaço será explorado, reduzindo o custo do processo.

* Utilizando a busca aleatória, foi possível usar um espaço de busca maior, mais abrangente, com resultado melhor e encontrado mais rapidamente.

# GridSearchCV x RandomizedSearch

* O GridSearch traz mais certeza da análise sobre um espaço de parâmetros, mas o RandomizedSearch traz muito mais controle sobre o custo computacional.

* Os testes de comparação das duas explorações foram feitos com Random Forest Classifier.

* Os resultados do Randomized Search eram encontrados em um tempo consideravelmente menor, mas tinha uma acurácia média "um pouco" menor. Apesar da redução do tempo ser benéfica, em alguns contextos a diferença de acurácia pode ser fundamental, sobretudo em modelos relacionados a resultados médicos, por exemplo.

# Alternativa caso o Cross Validation não sejam viável

* Caso seja computacionalmente inviável fazer uma validação cruzada, é preciso separar o dataset em um conjunto a mais, ou seja: treino, teste e validação. Pois a validação deve ser feita com entradas que nunca tiveram contato com o modelo.

* No estudo, foi usado o StratifiedShuffleSplit.

## Referências

Este projeto foi desenvolvido com referência nos cursos: 
  * [Machine Learning parte 1: otimização de modelos através de hiperparâmetros](https://cursos.alura.com.br/course/machine-learning-otimizacao-de-modelos-atraves-de-hiperparametros)
  * [Machine Learning parte 2: otimização com exploração aleatória](https://cursos.alura.com.br/course/machine-learning-otimizacao-com-exploracao-aleatoria)
