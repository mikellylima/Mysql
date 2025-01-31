## Módulo 34: Consultas Básicas

### Aula 1: Antes de começar, alguns comentários...

```sql
# Este é um comentário
-- Esste é outro comentário
/*
	Este é um comentário
*/
```


### Aula 2: SELECT (Parte 1)
- Selecione todas as colunas da tabela de pedidos

```sql
SELECT * FROM pedidos;
```

- Selecione todas as colunas da tabela de produtos

```sql
SELECT * FROM produtos;
```


### Aula 6: SELECT (Parte 2)
- Selecione todas as colunas da tabela PRODUTOS

```sql
SELECT * FROM produtos;
```

- Selecione apenas a coluna Nome_Produto da tabela PRODUTOS

```sql
SELECT Nome_Produto FROM produtos;
```

- Selecione as colunas ID_Produto, Nome_Produto, Preco_Unit da tabela PRODUTOS

```sql
SELECT ID_Produto, Nome_Produto, Preco_Unit FROM produtos;
```

- Escolha 4 colunas da tabela de PRODUTOS e as selecione

```sql
SELECT 
  ID_Produto,
  Nome_Produto,
  Marca_Produto,
  Custo_Unit 
FROM produtos;
```


### Aula 7: AS - Renomeando Colunas e Tabela

```sql
SELECT 
  ID_Produto AS 'ID Produto', 
  Nome_Produto AS 'Nome do Produto', 
  Marca_Produto AS 'Marca do Produto', 
  Custo_Unit AS 'Custo Unitário' 
FROM produtos;
```

- Renomeando a tabela

```sql
SELECT 
  p.ID_Produto, 
  p.Nome_Produto, 
  p.Marca_Produto, 
  p.Custo_Unit 
FROM produtos AS p;
```


### Aula 8: LIMIT e OFFSET

```sql
SELECT * FROM pedidos LIMIT 100;
SELECT * FROM pedidos LIMIT 100 OFFSET 5;
```


### Aula 9: DISTINCT

```sql
SELECT DISTINCT Marca_Produto FROM produtos;
```


### Aula 10: ORDER BY
- Exemplo 1. Ordenar a coluna Nome da tabela CLIENTES de forma ASC.

```sql
SELECT
  *
FROM clientes
ORDER BY Nome ASC;
```

- Exemplo 2. Ordenar a coluna Nome da tabela CLIENTES de forma DESC.

```sql
SELECT
  *
FROM clientes
ORDER BY Nome DESC;
```

- Exemplo 3. Ordenar a coluna Renda_Anual de forma ASC.

```sql
SELECT
  *
FROM clientes
ORDER BY Renda_Anual ASC;
```

- Exemplo 4. Ordenar a coluna Renda_Anual de forma DESC.

```sql
SELECT
  *
FROM clientes
ORDER BY Renda_Anual DESC;
```

- Exemplo 5. Ordenar a coluna Data_Nascimento de forma ASC.

```sql
SELECT
  *
FROM clientes
ORDER BY Data_Nascimento ASC;
```

- Exemplo 6. Ordenar a coluna Data_Nascimento de forma DESC.

```sql
SELECT
  *
FROM clientes
ORDER BY Data_Nascimento DESC;
```

- Exemplo final. Ordenar as colunas Renda_Anual e Data_Nascimento.

```sql
SELECT
	*
FROM clientes
ORDER BY Renda_Anual DESC, Data_Nascimento DESC;
```

- Exemplo final 2. Ordenar as colunas Nome e Sobrenome.

```sql
SELECT
	*
FROM clientes
ORDER BY Nome, Sobrenome;
```


------------------
## Módulo 35: Filtros no MySQL

### Aula 1 de 7: Comando WHERE
- Exemplo 1. Crie um filtro na tabela de CLIENTES para mostrar apenas as linhas referentes aos clientes com Renda_Anual >= 80000.

```sql
SELECT *
FROM clientes
WHERE Renda_Anual >= 80000;
```

- Exemplo 2. Crie um filtro na tabela de CLIENTES para mostrar apenas as linhas referentes aos clientes do sexo Masculino.

```sql
SELECT *
FROM clientes
WHERE Sexo = 'M';
```

- Exemplo 2.1. Crie um filtro na tabela de CLIENTES para mostrar apenas as linhas referentes aos clientes com escolaridade = 'Parcial'

```sql
SELECT *
FROM clientes
WHERE Escolaridade = 'Parcial';
```

- Exemplo 3. Crie um filtro na tabela de CLIENTES para mostrar apenas as linhas referentes aos clientes que nasceram após o dia '01/01/2000'.

```sql
SELECT *
FROM clientes
WHERE Data_Nascimento > '01/01/2000';
```

### Aula 2: Operadores AND, OR e NOT
- Exemplo 1. Crie um filtro na tabela PRODUTOS para mostrar apenas as linhas referentes aos produtos da Marca_Produto DELL e Preco_Unit maior ou igual a R$2.000.

```sql
SELECT *
FROM produtos
WHERE Marca_Produto = 'DELL' AND Preco_Unit >= 2000;
```

- Exemplo 2. Crie um filtro na tabela PRODUTOS para mostrar apenas as linhas referentes aos produtos da marca DELL OU ALTURA.

```sql
SELECT *
FROM produtos
WHERE Marca_Produto = 'DELL' OR Marca_Produto = 'ALTURA';
```

- Exemplo 3. Crie um filtro na tabela PRODUTOS para mostrar apenas as os produtos que não são da Marca_Produto igual a SAMSUNG.

```sql
SELECT *
FROM produtos
WHERE NOT Marca_Produto = 'SAMSUNG';
```


### Aula 3: IS NULL e IS NOT NULL
- Exemplo 1. Descubra quais clientes não cadastraram o celular.

```sql
SELECT *
FROM clientes
WHERE Telefone IS NULL;
```

- Exemplo 2. Descubra quais lojas cadastraram um contato telefônico.

```sql
SELECT *
FROM lojas
WHERE Telefone IS NOT NULL;
```


### Aula 4: Não confunda NULL com vazio

```sql
SELECT *
FROM clientes
WHERE Telefone = '';
```


### Aula 5 de 7: WHERE e LIKE
- Exemplo 1. Descubra quais clientes possuem um e-mail do gmail.

```sql
SELECT *
FROM clientes
WHERE Email LIKE '%gmail%';
```

- Exemplo 2. Descubra quais clientes possuem um e-mail terminado em '.br'.

```sql
SELECT *
FROM clientes
WHERE Email LIKE '%.br';
```


### Aula 6: WHERE e IN, NOT IN
- Exemplo. Faça um filtro que retorne todos os produtos de uma das 3 marcas a seguir: DELL, SONY ou ALTURA.

```sql
SELECT *
FROM produtos
WHERE Marca_Produto IN ('DELL', 'SONY', 'ALTURA');
```

- Retornar os produtos que NÃO SÃO das marcas DELL, SONY ou ALTURA.

```sql
SELECT *
FROM produtos
WHERE Marca_Produto NOT IN ('DELL', 'SONY', 'ALTURA');
```

### Aula 7 de 7: WHERE e BETWEEN
- Exemplo 1. Faça um filtro que retorno todos os produtos com Preco_Unit entre R$1.000 e R$2.500.

```sql
SELECT *
FROM produtos
WHERE Preco_Unit BETWEEN 1000 AND 2500;
```

- Exemplo 2. Faça um filtro que retorno todos os clientes que nasceram entre 01/01/1995 e 31/12/1999.

```sql
SELECT *
FROM clientes
WHERE Data_Nascimento BETWEEN '1995/01/01' AND '1999/12/31';
```


--------------
## Módulo 36: Operações Básicas e Funções de Agregação

### Aula 1: Operações básicas e funções de arredondamento
- Operações básicas

```sql
SELECT
	10 + 20			AS 'Soma',
	100 - 40		AS 'Subtração',
	5 * 20			AS 'Multiplicação',
	300 / 12		AS 'Divisão',
	(100 - 10) * 4	AS 'Operação',
	22 % 5			AS 'Resto da divisão';
```

- Funções de arredondamento

```sql
SELECT
	ROUND(87.149, 2)		AS 'Arred.',
	FLOOR(87.149)			AS 'Arred. p/ baixo',
	CEILING(87.149)			AS 'Arred. p/ cima',
	TRUNCATE(87.149, 2) 	AS 'Truncar';
```

### Aula 2: COUNT, COUNT DISTINCT
- a) Conte a quantidade de clientes a partir da coluna de Nome

```sql
SELECT
    COUNT(Nome) AS 'Contagem'
FROM clientes;
```

- b) Conte a quantidade de clientes a partir da coluna de Telefone

```sql
SELECT
    COUNT(Telefone) AS 'Contagem'
FROM clientes;
```

- c) Houve alguma diferença nos resultados? Por quê? Teve diferença de resultados porque o COUNT ignora (ou seja, não considera) os valores nulos de uma coluna. Conte a quantidade total de linhas da tabela de CLIENTES.

```sql
SELECT
    COUNT(*) AS 'Contagem'
FROM clientes;
```

- Conte a quantidade de marcas distintas na tabela de PRODUTOS

```sql
SELECT
    COUNT(DISTINCT Marca_Produto) AS 'Contagem'
FROM produtos;
```


### Aula 3 de 3: SUM, AVG, MIN e MAX
- a) Soma de Receita_Total
- b) Média de Receita_Total
- c) Mínimo de Receita_Total
- d) Máximo de Receita_Total

```sql
SELECT
	SUM(Receita_Venda) AS 'Soma de Receita',
    AVG(Receita_Venda) AS 'Média de Receita',
    MIN(Receita_Venda) AS 'Menor Receita',
    MAX(Receita_Venda) AS 'Maior Receita'
FROM pedidos;
```


----------------
## Módulo 37: Agrupamentos no MySQL

### Aula 1 de 4: GROUP BY (Parte 1)
- Exemplo 1. Crie um agrupamento mostrando o total de produtos por marca.

```sql
SELECT
	Marca_Produto,
    COUNT(*) AS 'Qtd. de Produtos'
FROM produtos
GROUP BY Marca_Produto
ORDER BY COUNT(*) DESC;
```

- Exemplo 2. Crie um agrupamento mostrando o total de clientes por sexo.

```sql
SELECT
	Sexo,
    COUNT(*) AS 'Qtd. de Clientes'
FROM clientes
GROUP BY Sexo
ORDER BY COUNT(*) DESC;
```

- Exemplo 3. Crie um agrupamento mostrando o total de vendas por ID do Produto.

```sql
SELECT
	ID_Produto,
	SUM(Receita_Venda) AS 'Total Receita'
FROM pedidos
GROUP BY ID_Produto
ORDER BY SUM(Receita_Venda) DESC;
```


### Aula 2: GROUP BY (Parte 2)
- Exemplo 4. Crie um agrupamento mostrando o total de clientes por escolaridade e sexo.

```sql
SELECT
	Escolaridade,
	Sexo,
	COUNT(*) AS 'Qtd. Clientes'
FROM clientes
GROUP BY Escolaridade, Sexo
ORDER BY COUNT(*) DESC;
```

- Exemplo 5. Crie um agrupamento mostrando o total de receita por ID do Produto e ID da Loja.

```sql
SELECT
	ID_Produto,
	ID_Loja,
	SUM(Receita_Venda) AS 'Qtd. VENDAS'
FROM pedidos
GROUP BY ID_Produto, ID_Loja;
```

### Aula 3: GROUP BY e WHERE
- Exemplo 1. Crie um agrupamento mostrando o total de clientes por escolaridade, mas apenas os clientes do sexo feminino.

```sql
SELECT
	Escolaridade,
	Sexo,
	COUNT(*) AS 'Qtd. Cliente'
FROM clientes
WHERE Sexo = 'F'
GROUP BY Escolaridade;
```


### Aula 4: GROUP BY e HAVING
- Exemplo 1. Crie um agrupamento mostrando o total de clientes por escolaridade. Filtre o agrupamento resultante para mostrar apenas as escolaridades com mais de 25 clientes.

```sql
SELECT
	Escolaridade,
	COUNT(*) AS 'Qtd. Cliente'
FROM clientes
GROUP BY Escolaridade
HAVING COUNT(*) > 25;
```

- Exemplo 2. Crie um agrupamento mostrando o total de receita por ID_Produto. Filtre o agrupamento resultante para mostrar apenas os produtos que tiveram uma receita total superior a R$5MM.

```sql
SELECT
	ID_Produto,
	SUM(Receita_Venda) AS 'Receita Total'
FROM pedidos
GROUP BY ID_produto
HAVING SUM(Receita_Venda) > 5000000;
```


--------------
## Módulo 38: Variáveis no MySQL

### Aula 2: User-Defined Variables na prática
- Exemplo 1: Uma loja vendeu 10 unidades de um determinado produto, a um preço de R$10,90 cada. Utilize variáveis para calcular a receita total gerada nessa venda.

```sql
SET @varQuantidade = 10;
SET @varPreco = 10.9;

SELECT @varQuantidade * @varPreco AS 'Receita Total';
```

- Exemplo 2. Crie uma consulta à tabela de produtos para mostrar apenas os produtos da marca DELL. Faça de forma que a marca DELL seja armazenada em uma variável.

```sql
SET @varMarca = 'DELL';

SELECT *
FROM produtos
WHERE Marca_Produto = @varMarca;
```


### Aula 3: Função CAST

```sql
# A função CAST converte um valor de qualquer típo em outro tipo de dados especificado. 

-- Obs.: No CAST, especificamos o INT coo SIGNED ou UNSIGNED e o VARCHAR como CHAR.

SET @varNumero = 10.9200;

SELECT @varNumero,
	CAST(@varNumero AS SIGNED),
	CAST(@varNumero AS DECIMAL(10, 2)),
	CAST(@varNumero AS CHAR(3));

SET @varData = '2021-01-01';

SELECT @varData,
	CAST(@varData AS DATE),
	CAST(@varData AS DATETIME);
```


--------------
## Módulo 39: Funções de Texto e Data no MySQL

### Aula 1: Função LENGTH
- Exemplo 1. Descubra a quantidade de caracteres do texto 'SQL Impressionador'.

```sql
SET @varCurso = 'SQL Impressionador';

SELECT LENGHT(@varCurso);
```

- Exemplo 2. Descubra a quantidade de caracteres de cada nome na tabela clientes.ALTER

```sql
SELECT
	Nome AS 'Nome',
	LENGTH(Nome) AS 'Núm. Caract.'
FROM clientes;
```

### Aula 2: Funções CONCAT e CONCAT_WS (Parte 1)
- Exemplo 1. Crie 2 variáveis: @varNome e @varSobrenome, e declare um nome e um sobrenome, respectivamente. Utilize as funções CONCAT e CONCAT_WS para criar uma 3ª variável que retorne o nome completo.ALTER

```sql
SET @varNome = 'Marcus';
SET @varSobrenome = 'Cavalcanti';
SET @varUltimoNome = 'Jesus';

SET @varNomeCompleto = CONCAT(@varNome, ' ', @varSobrenome, ' ', @varUltimoNome);
SET @varNomeCompleto2 = CONCAT_WS(' ', @varNome, @varSobrenome, @varUltimoNome);

SELECT @varNomeCompleto;
SELECT @varNomeCompleto2;
```


### Aula 3: Funções CONCAT e CONCAT_WS (Parte 2)
- Exemplo 2. Utilize as funções CONCAT e CONCAT_WS na tabela de clientes para criar uma coluna de nome completo.

```sql
SELECT
	ID_Cliente,
	Nome,
	Sobrenome,
	Email,
	CONCAT(Nome, ' ', Sobrenome) AS 'Nome Completo',
	CONCAT_WS(' ', Nome, Sobrenome) AS 'Nome Completo'
FROM clientes;
```

### Aula 4: Funções LCASE e UCASE
- Exemplo 1. Utilize as funções LCASE e UCASE com as variáveis abaixo.

```sql
SET @nome = 'fernando';
SET @sobrenome = 'martins';

SELECT
	LCASE(@nome),
	UCASE(@sobrenome)
```

- Exemplo 2. Utilize as funções LCASE e UCASE nas colunas de nome completo abaixo.

```sql
SELECT
	LCASE(CONCAT(Nome, ' ', Sobrenome)) AS 'Nome Completo (Concat)',
	UCASE(CONCAT_WS(' ', Nome, Sobrenome)) AS 'Nome Completo (Concat_ws)'
FROM clientes;
```


### Aula 5: Funções RIGHT e LEFT
- Exemplo 1. Separe o texto abaixo em 2 partes: 'SQL' e "Hashtag'.

```sql
SET @var = 'SQL Hashtag';

SELECT
	LEFT(@var, 3) AS 'Left',
	RIGHT(@var, 7) AS 'Right'
```

- Exemplo 2. Separe os códigos da coluna Num_Serie (tabela 'produtos') em 2 partes.

```sql
SELECT
	LEFT(Num_Serie, 6) AS 'Cod 1',
	RIGHT(Num_Serie, 6) AS 'Cod 2'
FROM produtos;
```


### Aula 6: Funções REPLACE
- Exemplo 1. No texto abaixo, substitua 'HIMYM' por 'Friends'.

```sql
SET @texto = 'HIMYM é a melhor série de comédia.';

SET @textonovo = REPLACE(@texto, 'HIMYM', 'Friends');

SELECT @textonovo;
```

- Exemplo 2. Substitua o texto 'S' por 'Solteiro'. Em seguida, substitua 'C' por 'Casado'.

```sql
SELECT
	Nome,
	Estado_Civil,
	REPLACE(REPLACE(Estado_Civil, 'S', 'Solteiro'), 'C', 'Casado')
FROM clientes;
```


### Aula 7: Funções INSTR e MID (Parte 1)
- Exemplo 1: Utilize o e-mail abaixo para fazer as seguintes ações:
- a) Retornar a posição do caractere '@';

```sql
SET @email = 'marcus@gmail.com';

SET @varPosArroba = INSTR(@email, '@');

SELECT @varPosArroba;
```

- b) Retornar o id do e-mail.

```sql
SET @email = 'marcus@gmail.com';

-- Usando Left
SET @varIdEmail = LEFT(@email, 6);

-- Usando Mid
SET @varIdEmailMid = MID(@email, 1, 6);

SELECT @varIdEmailMid;

-- Automatizando
SET @varIdEmailMid = MID(@email, 1, INSTR(@email, '@') - 1);
SELECT @varIdEmailMid;
```


### Aula 8: Funções INSTR e MID (Parte 2)
- Exemplo 2. Utilize as funções INSTR e MID para retornar o ID de todos os e-mails da tabela de clientes.ALTER

```sql
SELECT
	Email,
	MID(Email, 1, INSTR(Email, '@') - 1) AS 'ID email'
FROM clientes;
```


### Aula 9: Funções DAY, YEAR e MONTH

```sql
# 1. DAY(): Retorna o dia de uma data
# 2. MONTH(): Retorna o mês de uma data
# 3. YEAR(): Retorna o ano de uma data

SELECT
	Nome,
	Data_Nascimento,
	DAY(Data_Nascimento) AS 'Dia',
	MONTH(Data_Nascimento) AS 'Mês',
	YEAR(Data_Nascimento) AS 'Ano'
FROM clientes;
```


### Aula 10: Funções NOW, CURDATE e CURTIME

```sql
# 1. NOW(): Retorna a data e hora atuais
# 2. CURDATE(): Retorna a data atual
# 3. CURTIME(): Retorna a hora atual

SELECT
	NOW(),
	CURDATE(),
	CURTIME()
```


### Aula 11: Funções DATE_DIFF, DATE_ADD e DATE_SUB
- 1. DATEDIFF: Retorna a diferença entre duas datas. Calcular o tempo de entrega (em dias) de um projeto.

```sql
SET @varDataInicio = '2021-04-10';
SET @varDataFim = '2021-07-15';
 
SELECT DATEDIFF(@varDataFim, @varDataInicio);
```

- 2. DATE_ADD: Adiciona uma quantidade de dias/meses/anos a uma determinada data. Um projeto deve ser entregue 10 dias após a data de início. Qual é a data final de entrega?
 
```sql
SET @varDataInicio = '2021-04-10';
 
SELECT DATE_ADD(@varDataInicio, INTERVAL 10 DAY);
```

- 3. DATE_SUB: Subtrai uma quantidade de dias/meses/anos a uma determinada data. Um projeto finalizou no dia '2021-09-21' e teve 10 dias de duração. Qual foi a data de início?

```sql
SET @varDataFim = '2021-09-21';

SELECT DATE_SUB(@varDataFim, INTERVAL 10 DAY);
```


--------------
## Módulo 40: Joins 

### Aula 4: INNER JOIN - Exemplo 1
- Exemplo 1. Faça uma consulta para relacionar as tabelas de produtos e pedidos.

```sql
SELECT
	pedidos.ID_Pedido,
	pedidos.Data_Venda,
	pedidos.ID_Produto,
	pedidos.Qtd_Vendida,
	pedidos.Receita_Venda,
	produtos.Nome_Produto,
	produtos.Marca_Produto
FROM pedidos
INNER JOIN produtos
	ON pedidos.ID_Produto = produtos.ID_Produto;
```


### Aula 5: INNER JOIN - Exemplo 2
- Exemplo 2. Faça uma consulta para relacionar as tabelas de clientes e pedidos.

```sql
SELECT
	pedidos.ID_Pedido AS 'ID Pedido',
	pedidos.Data_Venda AS 'Data da Venda',
	pedidos.ID_Cliente AS 'ID Cliente',
	pedidos.Qtd_Vendida AS 'Qtd. Vendida',
	clientes.Nome AS 'Nome do Cliente',
	clientes.Email AS 'E-mail',
	clientes.Telefone AS 'Telefone'
FROM pedidos
INNER JOIN clientes
	ON pedidos.ID_Cliente = clientes.ID_Clientes;
```


### Aula 7 de 9: Renomeando as tabelas com o AS
- Exemplo 2. Faça uma consulta para relacionar as tabelas de clientes e pedidos.

```sql
SELECT
	p.ID_Pedido AS 'ID Pedido',
	p.Data_Venda AS 'Data da Venda',
	p.ID_Cliente AS 'ID Cliente',
	p.Qtd_Vendida AS 'Qtd. Vendida',
	c.Nome AS 'Nome do Cliente',
	c.Email AS 'E-mail',
	c.Telefone AS 'Telefone'
FROM pedidos AS p
INNER JOIN clientes as C
	ON p.ID_Cliente = c.ID_Clientes;
```


### Aula 8: INNER JOIN + WHERE
- Altere a consulta abaixo para incluir a coluna de Sexo da tabela clientes. Faça um filtro para mostrar apenas os clientes do sexo masculino.

```sql
SELECT
	p.ID_Pedido AS 'ID Pedido',
	p.Data_Venda AS 'Data da Venda',
	p.ID_Cliente AS 'ID Cliente',
	p.Qtd_Vendida AS 'Qtd. Vendida',
	c.Nome AS 'Nome do Cliente',
	c.Email AS 'E-mail',
	c.Telefone AS 'Telefone',
	c.Sexo AS 'Sexo'
FROM pedidos AS p
INNER JOIN clientes as C
	ON p.ID_Cliente = c.ID_Clientes
WHERE Sexo = 'M';
```


### Aula 9: INNER JOIN + GROUP BY
- a) Faça um agrupamento para mostrar o total de receita por ID do produto.

```sql
SELECT
	ID_Produto,
	SUM(Receita_Venda) AS 'Receita Total'
FROM pedidos
GROUP BY ID_Produto;
```

- b) Altere a consulta criada para mostrar o nome do produto em vez do ID do produto.

```sql
SELECT
	Nome_Produto,
	SUM(Receita_Venda) AS 'Receita Total'
FROM pedidos
INNER JOIN produtos
	ON pedidos.ID_Produto = produtos.ID_Produto
GROUP BY Nome_Produto;
```

- a) Faça um agrupamento para mostrar o total de receita e custo por ID da loja.

```sql
SELECT
	ID_Loja,
	SUM(Receita_Venda) AS 'Receita Total',
	SUM(Custo_Venda) AS 'Custo Total'
FROM pedidos
GROUP BY Loja;
```

- b) Altere a consulta criada para mostrar o nome da loja em vez do ID da loja.

```sql
SELECT
	Loja,
	SUM(Receita_Venda) AS 'Receita Total',
	SUM(Custo_Venda) AS 'Custo Total'
FROM pedidos
INNER JOIN lojas
	ON pedidos.ID_Loja = lojas.ID_Loja
GROUP BY Loja;
```


--------------
## Módulo 41: Funções Condicionais

### Aula 1: Função IF

```sql
-- IF(teste_logico, valor_se_verdadeiro, valor_se_falso)
-- IF(teste_logico1, valor_se_verdadeiro1, IF(teste_logico2, valor_se_verdadeiro2, valor_se_falso))

SELECT
	IF(0 > 15, 'Verdadeiro', 'Falso')
```

- Exemplo 2: Uma empresa oferece um bônus de 10% para todos os funcionários que tiveram uma avaliação do RH de acordo com a seguinte regra:
	- NotaDesempenho >= 7 ---> Recebe bônus de 10%
	- NotaDesempenho < 7 ----> Não recebe bônus

```sql

```

- Exemplo 3: Uma empresa oferece um bônus de 10% e 5% para todos os funcionários que tiveram uma avaliação do RH de acordo com a seguinte regra:
	- NotaDesempenho >= 7 ---> Recebe bônus de 10%
	- NotaDesempenho >= 5 ---> Recebe bônus de 5%
	- NotaDesempenho < 7 ----> Não recebe bônus

```sql

```

- Exemplo 4. As lojas da nossa empresa que tiverem mais de 20 funcionários receberão uma reforma de ampliação. Utilize a função IF para criar uma coluna na tabela Lojas que informe quais lojas receberão reforma e quais não receberão reforma.

```sql

```

### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```

### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```


### 
- 

```sql

```
