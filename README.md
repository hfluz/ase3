# Atividade Somativa em Equipe 3

Atividade Somativa em Equipe 3 (ASE3) da disciplina de Resolução de Problemas Estruturados em Computação
do curso de Engenharia de Software da PUCPR, campus Londrina, com prazo de entrega para o dia 23/06/2021.

**Organização do projeto:**

src/main:
* br.pucpr.ed.ase3.list: pacote contendo a implementação de listas não ordenada, ordenada e ordenável,
  baseado no projeto AFI8, além da implementação dos algoritmos de ordenação.
* br.pucpr.ed.ase3.map: pacote contendo a implementação de hash map da AFI7
* br.pucpr.ed.ase3.tree: pacote contendo a implementação de árvore binária da AFI6
* br.pucpr.ed.ase3.util: pacote contendo as classes utilitárias `StringUtil` e `Timer`.

srv/test:
* br.pucpr.ed.ase3: Classe com testes unitários que devem ser executados para validar o funcionamento
  dos algoritmos de ordenação.

**Requisitos:**

1) Adicionar a implementação dos algoritmos de busca bubble-sort, merge-sort, shell-sort e quick-sort 
   na classe `ListSort`, pedidos como entrega na AFI8.
   
2.1) Adicionar a implementação do método UnorderedArrayList.find, 
   pedido como entrega na AFI7 (exercício 4).

2.2) Adicionar a implementação do método put na classe UnorderedMap, 
   pedido como entrega na AFI7 (exercício 6).

3) Implementar na classe `MainApp` a alocação de listas, árvores e hash maps com quantidade variada de 
   elementos e de buscas. A tabela abaixo indica todas as combinações que deverão ser testadas:

Quantidade de elementos | Quantidade de buscas
------------ | -------------
10000 | 10000
10000 | 35000
10000 | 60000
10000 | 85000
10000 | 110000
20000 | 10000
20000 | 35000
20000 | 60000
20000 | 85000
20000 | 110000
30000 | 10000
30000 | 35000
30000 | 60000
30000 | 85000
30000 | 110000
   
Cada iteração marcará a duração em milissegundos da alocação, ordenação, busca de elementos e a duração total nas seguintes
estruturas de dados e algoritmos:  
* Lista não ordenada com busca sequencial (já implementado)
* Lista ordenada com busca binária (já implementado)
* Lista não ordenada com ordenação por bubble-sort e busca binária
* Lista não ordenada com ordenação por merge-sort e busca binária
* Lista não ordenada com ordenação por shell-sort e busca binária
* Lista não ordenada com ordenação por quick-sort e busca binária
* Árvore binária
* Hash map

**Como obter a duração de cada etapa de execução**

Foi criada a classe `Timer`, que facilita o registro do início e marcação da conclusão de cada etapa.
Anter de utilizar o timer é necessário instancia-lo:

    Timer timer = new Timer();

Todos os métodos (`startTimer`, `stopTimer`, `getResult` e `getTotal` esperam o identificador do timer
como parâmetro. Permitindo o registro de tempo de execução para cada algoritmo separadamente.

Para iniciar o timer logo antes da alocação execute (nos exemplos a seguir, usamos "merge-sort" como 
identificador do timer):

    timer.startTimer("merge-sort");

Após a conclusão de cada etapa, execute:

    timer.addStop("merge-sort");

Para obter os resultados, execute:

    List<Long> result = timer.getResult("merge-sort");

O método acima retornará uma lista com a duração de cada etapa, sendo que `result.get(0)` indicará
a duração da primeira etapa (alocação), `result.get(1)` indicará a duração da segunda etapa (ordenação),
e assim por diante.

Para obter a duração total execute:

    Long total = timer.getTotal("merge-sort")

Nos casos em que a ordenação não é necessária (lista ordenada, árvore binária e hash map), execute
o método `addStop` 2 vezes seguidas, fazendo com que a etapa de ordenação seja registrada com duração 0.
Por exemplo:

    timer.addStop("arvore-binária");
    timer.addStop("arvore-binária");

**Formatação do resultado**

Ao final deste arquivo há um exemplo de resultado que deverá ser gerado por este programa. Para
melhor formatar o resultado, foi incluída neste projeto a classe `StringUtil`, que possui o método
`lpad` (left pad), que recebe como parâmetro a palavra/valor que será exibido e a quantidade de caracteres
que ela deverá ocupar na tela. 

Se a palavra passada como parâmetro for "Algoritmo" (possui 9 caracteres) e o parâmetro `pad` for 20,
o método completará a string com 11 espaços a esquerda, permitindo que os dados fiquem alinhados, como
em uma tabela. 

Exemplo:

    StringUtil.lpad("Algoritmo", 20)

**Critérios de Avaliação**

1) (0,8 ponto) Execução dos testes unitários com sucesso (0,2 por teste).

2) (0,8 ponto) Execução correta da classe MainApp com os 8 algoritmos indicados na seção de requisitos se o 
trabalho for feito em grupo, ou 6 algoritmos a escolha do estudante caso seja feito individual.

3) (0,4 ponto) Inspeção do código-fonte. Adequação a boas práticas de programação e orientação a objetos.  
   Dica: utilize ferramentas de inspeção de código. Por exemplo Analyze->Inspect Code no IntelliJ IDEA,
   ou o SonarLint, que está disponível em diversas IDEs.

*Exemplo de saída da execução do programa*

    QUANTIDADE NÚMEROS: 10000	 QUANTIDADE BUSCAS: 10000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   2                   0                  49                  51
                 binária                  94                   0                   4                  98
             bubble-sort                   4                 463                   3                 470
              merge-sort                   1                  36                   3                  40
          arvore-binária                   5                   0                   3                   8
                hash-map                   4                   0                   1                   5
    
    QUANTIDADE NÚMEROS: 10000	 QUANTIDADE BUSCAS: 35000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                 118                 119
                 binária                  79                   0                   7                  86
             bubble-sort                   0                 426                   5                 431
              merge-sort                   1                  11                   3                  15
          arvore-binária                   3                   0                   9                  12
                hash-map                   3                   0                   3                   6
    
    QUANTIDADE NÚMEROS: 10000	 QUANTIDADE BUSCAS: 60000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                 194                 195
                 binária                  77                   0                   8                  85
             bubble-sort                   1                 456                  11                 468
              merge-sort                   0                   4                   5                   9
          arvore-binária                   1                   0                  10                  11
                hash-map                   1                   0                   3                   4
    
    QUANTIDADE NÚMEROS: 10000	 QUANTIDADE BUSCAS: 85000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                 277                 277
                 binária                  79                   0                  11                  90
             bubble-sort                   0                 400                   9                 409
              merge-sort                   1                   5                   3                   9
          arvore-binária                   2                   0                  12                  14
                hash-map                   2                   0                   1                   3
    
    QUANTIDADE NÚMEROS: 10000	 QUANTIDADE BUSCAS: 110000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                 381                 382
                 binária                  77                   0                  14                  91
             bubble-sort                   1                 399                  12                 412
              merge-sort                   1                   5                   5                  11
          arvore-binária                   2                   0                  15                  17
                hash-map                   1                   0                   1                   2
    
    QUANTIDADE NÚMEROS: 20000	 QUANTIDADE BUSCAS: 10000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                  68                  69
                 binária                 368                   0                   2                 370
             bubble-sort                   0                1808                   1                1809
              merge-sort                   4                   8                   1                  13
          arvore-binária                   4                   0                   1                   5
                hash-map                   3                   0                   1                   4
    
    QUANTIDADE NÚMEROS: 20000	 QUANTIDADE BUSCAS: 35000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                 238                 238
                 binária                 366                   0                   5                 371
             bubble-sort                   0                1959                   5                1964
              merge-sort                   0                   7                   2                   9
          arvore-binária                   3                   0                   5                   8
                hash-map                   1                   0                   1                   2
    
    QUANTIDADE NÚMEROS: 20000	 QUANTIDADE BUSCAS: 60000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                 405                 405
                 binária                 372                   0                   9                 381
             bubble-sort                   1                1790                   7                1798
              merge-sort                   0                   7                   3                  10
          arvore-binária                   3                   0                   9                  12
                hash-map                   0                   0                   1                   1
    
    QUANTIDADE NÚMEROS: 20000	 QUANTIDADE BUSCAS: 85000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                 576                 576
                 binária                 366                   0                  13                 379
             bubble-sort                   0                1793                  11                1804
              merge-sort                   0                  12                   4                  16
          arvore-binária                   3                   0                  13                  16
                hash-map                   1                   0                   1                   2
    
    QUANTIDADE NÚMEROS: 20000	 QUANTIDADE BUSCAS: 110000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                 748                 748
                 binária                 372                   0                  17                 389
             bubble-sort                   0                2031                  17                2048
              merge-sort                   0                  12                   6                  18
          arvore-binária                   3                   0                  17                  20
                hash-map                   1                   0                   1                   2
    
    QUANTIDADE NÚMEROS: 30000	 QUANTIDADE BUSCAS: 10000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                  95                  96
                 binária                1237                   0                   2                1239
             bubble-sort                   0                4660                   2                4662
              merge-sort                   0                  18                   1                  19
          arvore-binária                   5                   0                   1                   6
                hash-map                   2                   0                   0                   2
    
    QUANTIDADE NÚMEROS: 30000	 QUANTIDADE BUSCAS: 35000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                 348                 348
                 binária                 882                   0                   6                 888
             bubble-sort                   1                5017                   6                5024
              merge-sort                   0                  18                   2                  20
          arvore-binária                   5                   0                   6                  11
                hash-map                   1                   0                   0                   1
    
    QUANTIDADE NÚMEROS: 30000	 QUANTIDADE BUSCAS: 60000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                 578                 579
                 binária                1055                   0                  10                1065
             bubble-sort                   0                4638                   9                4647
              merge-sort                   1                  18                   3                  22
          arvore-binária                   5                   0                  11                  16
                hash-map                   1                   0                   1                   2
    
    QUANTIDADE NÚMEROS: 30000	 QUANTIDADE BUSCAS: 85000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   1                   0                 816                 817
                 binária                 882                   0                  14                 896
             bubble-sort                   1                4610                  13                4624
              merge-sort                   1                  18                   4                  23
          arvore-binária                   5                   0                  15                  20
                hash-map                   1                   0                   1                   2
    
    QUANTIDADE NÚMEROS: 30000	 QUANTIDADE BUSCAS: 110000
               Algoritmo            Alocação           Ordenação               Busca               Total
              sequencial                   0                   0                1056                1056
                 binária                 906                   0                  19                 925
             bubble-sort                   1                4649                  17                4667
              merge-sort                   0                  19                   5                  24
          arvore-binária                   6                   0                  18                  24
                hash-map                   2                   0                   6                   8

