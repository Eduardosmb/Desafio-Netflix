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

 ## SVD

 O Svd é uma decomposição de uma matriz A em outras 3 matrizes:

 * Autovetores(U):uma matriz de uma linha apenas em que cada coluna representa um autovetor.

 * Autovetovalores(S): uma matriz de uma linha apenas com todos os autovalores da matriz A: 

 * Autovetores ao transpostos(UT): uma matriz de uma coluna apenas em que cada linha representa um autovetor. Note que, essa matriz é a transposta da matriz U.

Exemplo:

$$
 U = \begin{bmatrix}
\beta1 & \beta2\\
\end{bmatrix}
$$
$$
 S= \begin{bmatrix}
x1 & x2\\
\end{bmatrix}
$$
$$
 UT = \begin{bmatrix}
\beta1 \\
\beta2
\end{bmatrix}
$$

 

 * X = autovalores
 * $ \beta $ = autvetores


 Apartir desses números podemos realizar diversas operações em que nos permitem transformar e restaurar a matriz original. Para isso precisamos apartir dessas matrizes construir uma nova matriz "sigma". Essa é composta com os autovalores na diagonal. Por exemplo:

$$
 sigma = \begin{bmatrix}
x1 & 0\\
0 & x2
\end{bmatrix}
$$

Agora que possuimos todas as matrizes necessarias, podemos reconstruir a nossa matriz original A aparitr da equação:

   $$
   A = U * sigma * UT
   $$


   $$
      Ou
   $$

$$
 A = \begin{bmatrix}
\beta1 & \beta2\\
\end{bmatrix}

 * \begin{bmatrix}
x1 & 0\\
0 & x2
\end{bmatrix}

 * \begin{bmatrix}
\beta1 \\
\beta2
\end{bmatrix}
$$












