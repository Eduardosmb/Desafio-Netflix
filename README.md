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
* $X$ tem uma linha por usuário e uma coluna por perfil,
* $Y$ é quadrada e mapeia perfis para perfis,
* $Z$ tem uma linha por perfil e uma coluna por filme.

## Implementação

Partindo agora para o código, para acharmos o X, Y e Z. Usamos uma função do numpy chamada apartir da matriz A (já criada na primeira etapa) 



