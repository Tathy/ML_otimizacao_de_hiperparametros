# ::chart_with_upwards_trend:: Machine Learning: Otimização de modelos através de hiperparâmetros

[Link do Google Colab](https://colab.research.google.com/drive/1zkmLyzgb1jqOybg_ZRvQR9_uk0_AIYHr?usp=sharing)

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

## Conclusões

* A busca utilizando grid é um processo demorado até se encontrar um bom resultado e não tem garantia de encotrar um modelo ótimo para um dado dataset.

* Ainda existem otimizações e análises que podem ser feitas.

## Referências

Este projeto foi desenvolvido com referência no curso [Machine Learning parte 1: otimização de modelos através de hiperparâmetros](https://cursos.alura.com.br/course/machine-learning-otimizacao-de-modelos-atraves-de-hiperparametros).
