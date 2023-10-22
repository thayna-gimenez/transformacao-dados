## Processando e transformando dados com Power BI

No início do projeto, após a criação de uma instância no Azure, ocorreram alguns erros relacionados ao script de inserção de dados e a configuração do Power BI, mas foi possível, no fim, integrar o Power BI com MySQL no Azure da forma correta.

Não foi necessário mudar os tipos de dados dos cabeçalhos (com exceção dos valores monetários), mas seus nomes foram alterados para melhor visualização no momento de criar o relatório. 
Na tabela employee, onde existia um valor nulo no Super_ssn, foi inserido o valor correspondente do gerente. A coluna Adress foi separada em rua, número, cidade e estado, e as colunas Fname, Minit e Lname foram mescladas em uma coluna apenas, com o nome completo do colaborador.

As tabelas employee e departament foram mescladas em uma nova tabela, com o nome e SSN dos colaboradores, além do número e nome dos departamentos de cada um deles. Também foi mesclada a tabela employee com ela mesma, para gerar uma nova, apenas com os nomes e SSN dos gerentes. Utilizando essa nova tabela, foi possível fazer uma nova consulta entre ela e a tabela employee, assim, realizando a junção dos colaboradores e seus respectivos gerentes. 

Os nomes dos departamentos foram mesclados com as suas respectivas localizações, em dois passos: primeiro, foi realizado o mesclar entre a tabela departament e dept_locations na própria tabela departament (imagem 1). Logo após, a coluna com as localizações foi expandida (imagem 2) e, assim, foi possível mesclar as colunas Dname e Dlocation. 

![image](https://github.com/thayna-gimenez/transformacao-dados/assets/88508228/3970cdd7-31a5-45c3-932c-8eaced6c01df)

![image](https://github.com/thayna-gimenez/transformacao-dados/assets/88508228/f3e372d9-43e1-464a-99be-64e57f4e9703)

A função mesclar consiste em juntar duas tabelas a partir de um fator em comum (no caso supracitado, foi levado em consideração o número do departamento, que era originalmente da tabela departament, mas referenciado na tabela dept_location), gerando uma nova coluna com os dados da tabela mesclada. Sendo assim, essa função faz a junção de duas tabelas dependendo do critério escolhido, o que permite a criação de um menor número de linhas no momento em que elas se juntam, como exemplificado nas imagens anteriores.

Em contrapartida, a função atribuir não conta com critérios para a junção de duas tabelas, ela apenas une todas as linhas e colunas de uma, com todas as linhas e colunas da outra. Se as duas não tiverem a mesma quantidade de colunas com o mesmo nome e mesmo tipo, a função apenas acrescentará as colunas de uma tabela na outra a qual ela está se juntando, acrescentando linhas com valores nulos onde elas não coincidirem (imagem 3).

![image](https://github.com/thayna-gimenez/transformacao-dados/assets/88508228/c00cc8a0-eed7-4ee7-8e0d-e29c461eedda)

Sendo assim, para juntar os nomes dos departamentos com suas localizações, pode-se utilizar apenas o mesclar, e não o atribuir.

Por fim, foi criada uma última tabela para agrupar os dados de forma a facilitar a visualização de quantos colaboradores existem por gerente, colunas desnecessárias ao projeto e relatório foram deletadas e um relatório simples foi montado para completar o desafio.
