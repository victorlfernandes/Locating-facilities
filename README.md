# Aplicação do problema de localização de facilidades
## Descrição do problema
O problema que escolhemos foi a localização de hospitais públicos de acordo com a demanda da população de São Carlos. Consideramos que a cidade já possui uma unidade da Santa Casa, além do hospital universitário da UFScar. 
O objetivo é auxiliar a prefeitura em uma possível construção de um novo hospital, fornecendo a localização ótima para tal de acordo com os custos de cada bairro e a necessidade dos pacientes.

## Variáveis e parâmetros

Utilizamos uma variável binária para determinar se um hospital é aberto ou não, e uma variável contínua correspondente a fração da demanda de cada paciente atendida pelos hospitais.

Como parâmetros temos  o custo de instalação e a capacidade de cada hospital, a demanda de atendimento dos pacientes de cada região e o custo de transporte de cada bairro para os hospitais.

## Função objetivo e restrições

A nossa função objetivo visa minimizar o custo total de distribuição dos hospitais, com base no custo fixo de cada e dos custos de transporte dos pacientes até o mesmo.

Elaboramos as seguintes restrições:
- Todos os pacientes devem ter suas demandas por atendimento médico atendidas
- A capacidade de cada um dos hospitais é respeitada, evitando um colapso no atendimento
- As hospitais 1 (Santa Casa) e 2 (Federal) já estão abertos
- Limita a abertura de apenas um novo hospital
- Domínio das variáveis



## Modelagem
![image](https://github.com/victorlfernandes/Locating-facilities/assets/87901904/5f1d7e3f-b563-4a3c-921d-5a46d7766335)

## Solução obtida

O valor ótimo encontrado foi de 73, que é correspondente a ambos os limitantes primal e dual, e o hospital selecionado para ser aberto foi o 5. Com isso, a distribuição dos pacientes pelos hospitais ficou da seguinte forma:

- Hospital Santa Casa: Paciente 5, Paciente 6, Paciente 7, Paciente 9, Paciente 10
- Hospital da Federal: Paciente 1, Paciente 3
- Novo Hospital: Paciente 2, Paciente 4, Paciente 8


## Análise de Resultados
Com base nos dados obtidos, pudemos obter algumas comparações entre os solves Gurobi e Scip, para os modelos inteiro e relaxado.

## Tempo

![image](https://github.com/victorlfernandes/Locating-facilities/assets/87901904/955be715-f3ec-42a9-83f7-2d7eb924d6f1)


Com base no gráfico apresentado, podemos observar que os solvers Gurobi (em vermelho) e Scip (em azul) obtiverem resultados semelhantes em questão do tempo, com exceção para a instância 1, onde o Gurobi foi muito mais performático (8.15s) com relação ao Scip (300.43s).

![image](https://github.com/victorlfernandes/Locating-facilities/assets/87901904/56ff46de-258b-4ca7-a7f2-178203b72409)

Já para o modelo relaxado (em verde), utilizando o Scip, as instâncias 1, 2 e 3 obtiveram uma grande vantagem com relação ao modelo inteiro (em azul). Já nas instâncias 4 e 5, o tempo de execução foi semelhante entre os dois modelos. 

## Valor Ótimo

![image](https://github.com/victorlfernandes/Locating-facilities/assets/87901904/d9b09ba5-8ca6-4711-baca-acd8c0cbda70)

Para o valor ótimo, foi possível concluir que ouve uma vantagem do Gurobi (em vermelho) com relação ao Scip (em azul) apenas para a instância 5, onde o Gurobi foi capaz de melhor minimizar a solução.

![image](https://github.com/victorlfernandes/Locating-facilities/assets/87901904/13435681-dbd2-48a4-9b56-c73bb1d44a12)

No modelo relaxado (em verde), pudemos notar que os valores ótimos com relação ao modelo inteiro (em azul) foram muito semelhantes, com exceção da instância 5, onde apenas o modelo inteiro obteve uma solução.

No Toy problem, o solver não teve muita dificuldade em achar a solução ótima, e demorou apenas 0.01 segundos. Ademais, podemos perceber que a distribuição dos pacientes foi feita de maneira consideravelmente uniforme entre os hospitais, representando uma solução que dificulta o colapso do sistema de saúde na cidade.

## Conclusão
Portanto, temos que as propostas exigidas pelo trabalho foram concluídas de maneira esperada. Os dois solvers tiveram um desempenho semelhante, gerando soluções condizentes com as instâncias dadas. Além disso, a pesquisa para o desenvolvimento de uma aplicação voltada para a cidade de São Carlos nos auxiliou em enxergar as possibilidades que os conceitos de otimização aprendidos nessa disciplina possuem em ser aplicados no cotidiano real.
