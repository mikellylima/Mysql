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
