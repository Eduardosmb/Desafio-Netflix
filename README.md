# Desafio-Netflix

Esse é um trabalho da disciplina Algebra Linear e Teoria da Informação, do curso ciências da computação do insper. A ideia é prever qual nota um usuário daria a um filme baseado no seu historico de avaliação. Para isso foi usado um csv chamada"ratings_small", em que possue uma base de dados suficiente para realiuzar a previsão.

# Como Rodar

  Para utilizar o programa, basta seguir os passos abaixo:

  1. Instale o Python 3.8 ou superior;

  2. Instale a biblioteca Numpy;
     
     ```pip install numpy```

  3. Instale a biblioteca matplotlib;
     
     ```pip install matplotlib```
     
  4. Instale a biblioteca scipy;
     
     ```pip install scipy```
     
  5. Instale a biblioteca pandas;
     
     ```pip install pandas```

  6. Para facilitar, basta instalar os requirements.txt, que contém todas as bibliotecas necessárias para o funcionamento do programa.
   
      ```pip install -r requirements.txt```
  
  6. Após a instalação de tudo, basta apenas rodar o arquivo++++
  
  
  # Modelo matemático

## Autovalores e autovetores 

São matrizes descobertas apatir de uma matriz A, que nos permite modificar e restaurar a matriz original. Esse fenomêno pode ser verificado apartir da seguinte equação:

   ![img](img\ax=axalpha.png)

 * A: mattriz original
 * X: autovetores
 * alpha: autovalores

 Exemplo:

   ![img](img\exEquacao1.png)


   É importante notar que a matriz de autovetor, nada mais é do que uma matriz com os autovalores na diagonal.



 ## SVD

 O Svd é uma decomposição de uma matriz A em outras 3 matrizes:

 * Autovalores(S): uma matriz diagonal que contém os valores singulares da matriz de entrada, ordenados em ordem decrescente. Os valores singulares representam a importância de cada componente na matriz original e são usados para determinar quantas componentes reter na reconstrução da matriz original.

 * Autovetores(U): é uma matriz ortogonal cujas colunas são os autovetores da matriz de covariância da matriz transposta da entrada $A^TA$.

 * Autovetores ao quadrado(VT): é uma matriz ortogonal cujas colunas são os autovetores da matriz de covariância da matriz de entrada $AA^T$.

 Podemos utilizar 
 





