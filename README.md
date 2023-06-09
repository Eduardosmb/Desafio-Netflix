# Desafio-Netflix

Esse é um trabalho da disciplina Algebra Linear e Teoria da Informação, do curso ciências da computação do Insper. A ideia é prever qual nota um usuário daria a um filme baseado no seu histórico de avaliação. Para isso foi usado um csv chamado "ratings_small".

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
  
  7. Após a instalação de tudo, pode-se rodar o programa de duas distintas maneira:

       1. Rodando o arquivo "netflix.ipynb" no terminal. Importante notar que ao rodar esse arquivo você acaba rodando o código inteiro, ou seja, o tempo de execução será muito grande(podendo ultrapassar 1 hora), pois além de rodar o código que gera o gráfico também rodará o código que busca descobrir qual o K com a menor precisão. 
       
       2. Caso queira executar apenas o código que gera o gráfico, basta rodar apenas as últimas duas células do arquivo "netflix.ipynb" manualmente. Para fazer isso, basta ir na célula descrita como "Testando o menor K 1500 vezes", onde lá você pode escolher um range, visando definir o número de estimações que o código vai executar. Após isso, basta escolher um valor de "k"(delimitador), que pode ser obtido através da análise do csv "results.csv". Depois dessas etapas, basta executar a célula atual e a próxima, onde o gráfico será finalmente gerado.
       
  
  
  # Modelo matemático

 ## SVD

 O Svd é uma decomposição de uma matriz A em outras 3 matrizes:

 * Autovetores(U): uma matriz de uma linha apenas em que cada coluna representa um autovetor.

 * Autovetovalores(S): uma matriz de uma linha apenas em que cada coluna representa um autovalor da matriz A.

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
 * $ \beta $ = autovetores


 A partir desses números podemos realizar diversas operações em que nos permitem transformar e restaurar a matriz original. Para isso precisamos a partir dessas matrizes construir uma nova matriz "sigma". Essa é composta com os autovalores na diagonal. Por exemplo:

$$
 sigma = \begin{bmatrix}
x1 & 0\\
0 & x2
\end{bmatrix}
$$

Agora que possuímos todas as matrizes necessarias, podemos reconstruir a nossa matriz original A aparitr da equação:

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


Tanto os autovalores e autovetores, quanto o sigma, são facilmente calculados apartir de funções do numpy chamadas "svd" e "diagsvd" respectivamente. 



## Implementação

   Para solucionar o problema proposto, primeiro precisamos criar uma matriz A de usuário por filmes a partir do csv "small_ratings.csv". Depois criamos uma cópia dessa matriz chamada de B. Nela, além de substituírmos todos os valores vazios por 2.5 (metade da nota máxima), também substituímos um valor aleatório diferente de 2.5 por uma nova nota aleatória. Tudo isso visando prever qual a nota original atribuida pelo usuário.

   Após isso, a partir de uma função chamada "svd" do numpy, calculamos os autovalores e autovetores da matriz A. Agora precisamos fazer uma compressão dessas novas três matrizes criadas. Para isso, definimos um valor de K com a finalidade de limitar o número de autovalores e autovetores que serão utilizados em cada uma das matrizes: U, S e UT. Todo esse processo é feito com a intenção de achar uma precisão em que a diferença entre a matriz original e a matriz reconstruída seja a menor possível (a precisão é gerada pela limitação do K).

   Após a compressão, pegamos essas novas matrizes comprimidas e a partir da função do numpy "diagsvd" criamos uma nova matriz chamada de "sigma".

   Agora que possuímos todas as matrizes necessarias, podemos reconstruir a nossa matriz original A a partir da equação:

   $$
   A = U * sigma * UT
   $$


Em nosso caso, fizemos uma média das diferenças entre o valor original e o valor final previsto, baseado em dez iterações para cada K. O resultado foi o seguinte:

* Menor diferença: K= 32 e diferença: 0.05

* Maior diferença: K= 582 e diferença: 3.24

OBS: tinham no total 671 K


Por fim, pegamos o K que teve a menor média de diferença e testamos um total de 1500 vezes, e plotamos todas as diferenças em um único gráfico:



![histograma](https://user-images.githubusercontent.com/81189924/233224624-b2da22af-da28-491c-8494-2027d7b17637.png)




# Conclusão

   Com base nos resultados obtidos, acreditamos que o sistema proposto não poderia ser utilizado em produção, uma vez que por mais que possua vezes que a diferença se aproxima de zero, na maioria das vezes a diferença fica entre 1 e 2, que nesse caso não é algo irrelevante.












