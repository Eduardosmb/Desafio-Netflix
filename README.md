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
  
  Primeiramente, precisamos entender o csv "ratings_small" que nos foi fornecido. O sheets é organizado em colunas com os respectivos valores: 
  
   - ```UserId```: Id de cada usuário
    
   - ```MovieID```: id de cada filme
    
   - ```Rating```: Nota dada ao filme pelo usuário
    
   - ```TimeStamp```: Tempo de cada filme
  
