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
  
  ## Preaparando ambiente inicial
  
  Primeiramente, precisamos entender o csv "ratings_small" que nos foi fornecido. O sheets é organizado em colunas com os respectivos valores: 
  
   - ```UserId```: Id de cada usuário
    
   - ```MovieID```: id de cada filme
    
   - ```Rating```: Nota dada ao filme pelo usuário
    
   - ```TimeStamp```: Tempo de cada filme

  Apartir disso, criamos uma matriz A da seguinte maneira: as linhas representam o id do usuário, as colunas o Id do filme e os valores as notas. Nesse caso podemos ignorar o TimeStamp. Também preenechemos os valores vazios por 2.5 (metade). Dessa forma, temos uma matriz em que cada linha representa um perfil de um usuário, onde está todas as notas atribuidas por ele.
  
## Entendendo o Sistema de Recomendação

A ideia por trás do sistema de recomendação é que existem "perfis" de usuários, que representam as preferências típicas de cada grupo de pessoas. Esses perfis são vetores que mostram as notas que os usuários daquele grupo normalmente dão a cada filme. Por exemplo, suponha que temos dois grupos de usuários e três filmes, e que esses grupos têm as seguintes preferências:

- `p_0 = [2, 5, 2]`, que significa que as pessoas no grupo `0` gostam muito do filme `f_1`;
- `p_1 = [5, 0, 4]`, que significa que as pessoas no grupo `1` gostam dos filmes `f_0` e `f_2`.

No entanto, sabemos que os usuários reais geralmente não seguem um perfil de preferências tão estrito. As notas que eles dão aos filmes são, portanto, modeladas como combinações lineares dos perfis. Por exemplo, podemos ter usuários como:

- `u_0 = 0.1 p_0 + 0.9 p_1`, que é um usuário muito próximo do perfil `p_1` mas distante de `p_0`;
- `u_1 = 0.1 p_0 + 0.1 p_1`, que é um usuário que está distante tanto do perfil `p_0` quanto do `p_1`.

Assim, o que precisamos é de uma maneira de associar usuários aos perfis e, em seguida, os perfis aos filmes. Precisamos, portanto, "decompor" nossa matriz nos seguintes componentes:

* $A$ tem uma linha por usuário e uma coluna por filme,
* $U$ tem uma linha por usuário e uma coluna por perfil,
* $S$ é quadrada e mapeia perfis para perfis,
* $VT$ tem uma linha por perfil e uma coluna por filme.

## Implementação

Partindo agora para o código, a primeira coisa que devemos fazer é uma cópia da nossa matriz A (já criada na primeira etapa) chamada de B, para assim podermos mexer nela sem alterar a original. Iremos sortear uma posição aleatória na matriz B e substituir a nota atribuida por um valor aleatório (de 0 a 5). Esse será o valor que iremos prever.

Para acharmos esse valor primeiramente precisamos decompor a matriz para assim decobrirmos os os valores S, U e VT. Usamos uma função do numpy chamada "svd" apartir da matriz B O svd nada mais é do que uma decomposição de uma matriz (nesse caso a matriz B em outras três matrizes: 

* Autovalores (Matriz S): uma matriz diagonal que contém os valores singulares da matriz de entrada, ordenados em ordem decrescente. Os valores singulares representam a importância de cada componente na matriz original e são usados para determinar quantas componentes reter na reconstrução da matriz original.

* Atuvetores da direita (Matriz U): é uma matriz ortogonal cujas colunas são os autovetores da matriz de covariância da matriz transposta da entrada $A^TA$.

* Autorvetores da esquerda (Matriz VT): é uma matriz ortogonal cujas colunas são os autovetores da matriz de covariância da matriz de entrada $AA^T$.


Logo depois, delimitamos as nossas respectivas matrizes a um valor K, ou seja, dependendo da matriz delimitamos as nossas linhas ou as nossas colunas até certo ponto. Isso com o objetivo de procurar uma precisão. Para descobrir qual K que melhor desempenha nessa questão, testamos todos os possiveis 671 e guardamos o resultado em um csv.

Por fim, para finalmente acharmos a nota esperada pelo usuário usamos uma função do numpy chamada diagsvd





