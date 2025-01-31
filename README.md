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
SET @NotaDesempenho = 7;
SELECT
	IF(@NotaDesempenho >= 7, 'Recebe bônus de 10%', 'Não recebe bônus');
```

- Exemplo 3: Uma empresa oferece um bônus de 10% e 5% para todos os funcionários que tiveram uma avaliação do RH de acordo com a seguinte regra:
	- NotaDesempenho >= 7 ---> Recebe bônus de 10%
	- NotaDesempenho >= 5 ---> Recebe bônus de 5%
	- NotaDesempenho < 5 ----> Não recebe bônus

```sql
SET @NotaDesempenho = 4;
SELECT
	IF(@NotaDesempenho >= 7, 'Recebe bônus de 10%', IF(@NotaDesempenho >= 5, 'Recebe bônus de 5%', 'Não recebe bônus')) AS 'Resultado';
```

- Exemplo 4. As lojas da nossa empresa que tiverem mais de 20 funcionários receberão uma reforma de ampliação. Utilize a função IF para criar uma coluna na tabela Lojas que informe quais lojas receberão reforma e quais não receberão reforma.

```sql
SELECT
	*,
	IF(Num_Funcionarios > 20, 'Recebe reforma', 'Não recebe reforma') AS 'Status'
FROM lojas;
```

### Aula 2: Funções IFNULL, ISNULL e NULLIF
- Exemplo 1. Utilize a função IFNULL para retornar um valor alternativo para o valor abaixo.

```sql
-- IFNULL(expressão, valor_alternativo)

SELECT
	IFNULL(NULL, 'Valor alternativo')

SELECT
	IFNULL(100, 'Valor alternativo')
```

- Exemplo 2. A tabela de lojas pode ter lojas que não possuem telefone de contato. Neste caso, todas as lojas que tiverem um telefone NULL serão direcionadas para uma central de atendimento com um número padrão: 0800-999-9999. Utilize a função IFNULL para fazer esse ajuste.

```sql
SELECT
	*,
	IFNULL(Telefone, '0800-999-9999') AS 'Telefone corrigido'
FROM lojas;
```

- Exemplo 1. Alguns clientes não cadastraram o telefone de contato. Faça uma consulta com uma coluna extra que identifique esses clientes de alguma forma.

```sql
# ISNULL: Testa se um determinado valor é NULL. Caso seja nulo, retorna 1; caso contrário, retorna zero.

SELECT
	*,
	IF(ISNULL(Telefone), 'Verificar', 'Ok') AS 'Status'
FROM clientes;


# NULLIF: Compara duas expressões e retorna NULL se as duas forem iguais. Se forem, retornar NULL; caso contrário, retorna a primeira expressão. 

SET @var1 = 100;
SET @var2 = 200;

SELECT
	NULLIF(@var1, @var2) AS 'Resultado';
```


### Aula 3: Função CASE-THEN
- Exemplo 1. Utilize a estrutura CASE para criar uma consulta da nossa tabela de clientes que substitua o valor 'M' por 'Masculino' e o valor 'F' por 'Feminino'

```sql
SELECT
	*,
	CASE
		WHEN Sexo = 'M' THEN 'Masculino'
		ELSE 'Feminino'
	END AS 'Sexo 2'
FROM clientes;
```

- Exemplo 2. Na tabela de pedidos, crie uma estrutura CASE para avaliar as seguintes situações de Receita_Venda:
	- Caso Receita_Venda >= 3000 ---> 'Faturamento Alto'
	- Caso Receita_Venda >= 1000 ---> 'Faturamento Médio'
	- Caso Receita_Venda < 1000  ---> 'Faturamento Baixo'

```sql
SELECT
	*,
	CASE
		WHEN Receita_Venda >= 3000 THEN 'Faturamento Alto'
		WHEN Receita_Venda >= 1000 THEN 'Faturamento Médio'
		ELSE 'Faturamento Baixo'
	END AS 'Status'
FROM pedidos;
```

### Aula 4: Função CASE + AND
- APLICAÇÃO AND

```sql
-- Exemplo 1. A empresa está com uma ação de dia das mães/dia dos pais. Como vai funcionar?
-- Caso o cliente seja do sexo Feminino E tenha filhos, receberá ofertas de dia das mães
-- Caso o cliente seja do sexo Marculino E tenha filhos, receberá ofertas de dia dos pais
-- Caso contrário, não receberá oferta

-- As ofertas serão enviadas por e-mail, por isso o setor responsável precisa de uma tabela identificando facilmente quem receberá qual oferta:

-- 'Oferta dia das mães' ---> Mulher com filhos
-- 'Oferta dia dos pais' ---> Homem com filhos
-- 'Sem oferta' ---> Clientes sem filhos

-- Você deve criar uma coluna extra identificando cada status.


```


### Aula 5: Função CASE + OR (IN)
- APLICAÇÃO OR

```sql
-- Exemplo 2. A empresa está com uma parceria com as empresas das marcas 'DELL' e 'SAMSUNG'. Isso significa que os produtos dessas marcas receberão um desconto de 15% em seu custo de aquisição. Faça uma consulta que retorne uma coluna extra de desconto no custo de aquisição de cada produto. 

-- Custo_Unit = X
-- Custo_Unit = x - 15% de x = x - 0.15 * x = (1 - 0.15) * x

SELECT
	*,
	CASE
		WHEN Marca_Produto = 'DELL' OR Marca_Produto = 'SAMSUNG' THEN (1-0.15)*Custo_Unit
		ELSE Custo_Unit
	END AS 'Desconto?'
FROM produtos;

-- Outra solução
SELECT
	*,
	CASE
		WHEN Marca_Produto IN ('DELL', 'SAMSUNG') THEN (1-0.15)*Custo_Unit
		ELSE Custo_Unit
	END AS 'Desconto?'
FROM produtos;
```


----------------
## Módulo 42: Views

### Aula 2: CREATE VIEW
- CREATE VIEW: Cria uma view no nosso banco de dados.

```sql
CREATE VIEW vwclientes AS
SELECT
	ID_Cliente,
	Nome,
	Data_Nascimento,
	Email,
	Telefone
FROM clientes;

SELECT * FROM vwclientes;
```


### Aula 3: ALTER VIEW e DROP VIEW
- ALTER VIEW: Altera uma view existente no banco de dados.

```sql
ALTER VIEW vwclientes AS
SELECT
	ID_Cliente,
	Nome,
	Data_Nascimento,
	Email,
	Telefone,
	Escolaridade
FROM clientes
WHERE Escolaridade = 'Parcial';

SELECT * FROM vwclientes;

DROP VIEW vwclientes;
```

### Aula 4: Exemplo 1 - Criando uma View com o comando WHERE
- Exemplo 1. Crie uma View chamada vwReceitaAcima4000 que armazene todas as colunas da tabela Pedidos. A sua View deverá conter apenas as vendas com receita acima de R$4.000.

```sql
CREATE VIEW vwReceitaAcima4000 AS
SELECT
	*
FROM pedidos
WHERE Receita_Venda > 4000;

SELECT * FROM vwReceitaAcima4000;
```

- Exemplo 2. Crie uma View chamada vwProdutosAtualizada que armazene todas as colunas da tabela Produtos. A sua view deverá conter apenas os produtos das marcas DELL, SAMSUNG e SONY. 

```sql
CREATE VIEW vwProdutosAtualizada AS
SELECT
	*
FROM produtos
WHERE Marca_Produto IN ('DELL', 'SAMSUNG', 'SONY');

SELECT * FROM vwProdutosAtualizada;
```


### Aula 5: Exemplo 2 - Criando uma View com os comandos GROUP BY, WHERE e HAVING
- Exemplo 1. Crie uma view que será o resultado de um agrupamento da tabela de pedidos. A ideia é que você tenha nessa view o total de Receita e Custo agrupados por ID_Produto.

```sql
CREATE VIEW vwReceitaECustoTotal AS
SELECT
	ID_Produto,
	SUM(Receita_Venda) AS 'Receita Total',
	SUM(Custo_Venda) AS 'Custo Total'
FROM pedidos
GROUP BY ID_Produto;

SELECT * FROM vwReceitaECustoTotal;
```

- Exemplo 2. Altere a view anterior para mostrar o agrupamento apenas para os produtos da loja 2. 

```sql
ALTER VIEW vwReceitaECustoTotal AS
SELECT
	ID_Produto,
	ID_Loja,
	SUM(Receita_Venda) AS 'Receita Total',
	SUM(Custo_Venda) AS 'Custo Total'
FROM pedidos
WHERE ID_Loja = 2
GROUP BY ID_Produto;

SELECT * FROM vwReceitaECustoTotal;
```

- Exemplo 3. Altere a view anterior para mostrar o agrupamento apenas para os produtos que tiveram uma receita total maior que 1 milhão, na loja 2. 

```sql
ALTER VIEW vwReceitaECustoTotal AS
SELECT
	ID_Produto,
	ID_Loja,
	SUM(Receita_Venda) AS 'Receita Total',
	SUM(Custo_Venda) AS 'Custo Total'
FROM pedidos
WHERE ID_Loja = 2
GROUP BY ID_Produto
HAVING SUM(Receita_Venda) >= 1000000;

SELECT * FROM vwReceitaECustoTotal;
```


### Aula 6: Exemplo 3 - Criando uma View com os comandos INNER JOIN e GROUP BY
- Exemplo 1. Crie uma view que seja a junção entre as tabelas de pedidos e de produtos. Ou seja, essa view deve conter todas as colunas da tabela pedidos e as colunas Nome_Produto, Marca_Produto e Num_Serie da tabela de produtos.

```sql
CREATE VIEW vwPedidosCompleta AS
SELECT
	pe.*,
	pr.Nome_Produto,
	pr.Marca_Produto,
	pr.Num_Serie
FROM pedidos AS pe
INNER JOIN produtos AS pr
	ON pe.ID_produto = pr.ID_produto;

SELECT * FROM vwPedidosCompleta;
```

- Exemplo 2. Crie uma view que será o resultado de um agrupamento da tabela de pedidos. A ideia é que você tenha nessa view o total de Receita e Custo agrupados por Nome_Produto.

```sql
CREATE VIEW vwResultadoFinal AS
SELECT
	pr.Nome_Produto,
	SUM(pe.Receita_Venda) AS 'Receita Total',
	SUM(pe.Custo_Venda) AS 'Custo Total'
FROM pedidos AS pe
INNER JOIN produtos AS pr
	ON pe.ID_produto = pr.ID_produto
GROUP BY pr.Nome_Produto;

SELECT * FROM vwResultadoFinal;
```


---------------
## Módulo 43: CRUD

### Aula 2: Criando Bancos de Dados

```sql
# 1. CREATE DATABASE: Criando um banco de dados

-- Para criar um banco de dados, usamos o seguinte comando:

-- CREATE DATABASE nome_bd;

-- CREATE DATABASE IF NOT EXISTS nome_bd;

-- Obs.: O IF NOT EXISTS não é obrigatório. Sua função é evitar o erro que pode acontecer se você já tiver criado um banco de dados com o mesmo nome. 
-- Exemplo:

CREATE DATABASE db_Exemplo;

CREATE DATABASE IF NOT EXISTS db_Exemplo;


# 2. SHOW DATABASES: Verificando um banco de dados

-- É possível verificar os bancos de dados existentes utilizando o comando SHOW:

SHOW DATABASES;


# 3. USE: Usando um BD específico

-- O comando USE define um banco de dados específico como sendo o padrão do sistema.

USE db_Exemplo;

-- Caso você queira saber qual é o banco de dados selecionado no momento, você pode usar o comando:

SELECT DATABASE();


# 4. DROP: Excluindo um banco de dados

-- Para excluir um banco de dados, usamos o seguinte comando:

DROP DATABASE db_Exemplo;
DROP DATABASE IF EXISTS db_Exemplo;
```


### Aula 3: Criando Tabelas - Tipos de Dados, CREATE, SHOW e DROP TABLE

```sql
-- Crie o banco de dados db_Exemplo e defina-o como padrão:

CREATE DATABASE IF NOT EXISTS db_Exemplo;
USE db_Exemplo;
--

# Tipos de Dados no MySQL
-- Quando criamos uma nova tabela, precisamos especificar quais são as colunas que esssa tabela deve conter.
-- Cada uma dessas colunas vai armazenar um tipo de dados específico.
-- Os principais tipos de dados são listados abaixo:

-- INT:
-- Um inteiro médio. O intervalo assinado é de -2147483648 a 2147483647.

-- DECIMAL(M, D):
-- O número total de dígitos é especificado em M. O número de dígitos após o ponto decimal é especificado no parâmetro D. O número máximo para M é 65. O número máximo para D é 30. O valor padrão para M é 10. O valor padrão para D é 0. 

-- 1500.59 -- DECIMAL(6, 2)
 
-- VARCHAR(N):
-- Uma string de comprimento VARIÁVEL (pode conter letras, números e caracteres especiais). O parâmetro N especifica o comprimento máximo da coluna em caracteres - pode ser de 0 a 65535. 

-- DATE:
-- Uma data no formato: YYYY-MM-DD. O intervalor compatível é de '1000-01-01' a '9999-12-31'.

-- DATETIME:
-- Uma combinação de data e hora. Formato: YYYY-MM-DD HH:MM:SS. O intervalo compatível é de '1000-01-01 00:00:00' a '9999-12-31 23:59:59'.


-- Agora que sabemos os principais tipos de dados, podemos criar nossas tabelas. 

CREATE TABLE IF NOT EXISTS dAlunos(
	ID_Aluno INT,
	Nome_Aluno VARCHAR(100),
	Email VARCHAR(100)
);

CREATE TABLE IF NOT EXISTS dCursos(
	ID_Curso INT,
	Nome_Curso VARCHAR(100),
	Preco_Curso DECIMAL(10, 2)
);

CREATE TABLE IF NOT EXISTS fMatriculas(
	ID_Matricula INT,
	ID_Aluno INT,
	ID_Curso INT,
	Data_Cadastro DATE
);


SHOW TABLES;

DROP TABLE dAlunos;

SELECT * FROM dAlunos;
SELECT * FROM dCursos;
SELECT * FROM fMatriculas;
```


### Aula 4: Constraints - O que são e como usar

```sql
# 4. Adicionando constraints nas colunas das tabelas criadas.

-- Restrições (Constraints) são regras aplicadas nas colunas de uma tabela.
	-- Ex1: Podemos especificar que uma coluna não pode ter valores NULL;
    -- Ex2: Podemos especificar que uma coluna deverá ser uma chave primária ou chave estrangeira;
-- São usadas para limitar os tipso de dados que são inseridos. 

# Principais:

# I. NOT NULL:
-- A constraint NOT NULL faz com que uma coluna não aceite valores NULL. Um valor NULL é diferente de zero ou vazio, ele identifica que nenhum valor foi definido. 
-- A constraint NOT NULL obriga um campo a sempre possuir um valor. 
-- Dessa forma, não é possível inserir um registro ou atualizar sem entrar com um valor neste campo. 

		-- Nome_Cliente VARCHAR(100) NOT NULL

# II. UNIQUE
-- A restrição UNIQUE identifica de forma única cada registro em uma tabela de um banco de dados.
-- As constraints UNIQUE e PRIMARY KEY garantem a unicidade em uma coluna ou conjunto de colunas.
-- Uma constraint PRIMARY KEY automaticamente possui uma restrição UNIQUE definida.
-- Você pode ter várias constraints UNIQUE em uma tabela, mas apenas uma Chave Primária por tabela.

# III. DEFAULT
-- Essa restrição insere um valor padrão na coluna.
-- O valor padrão será adicionado a todos os novos registros caso nenhum outro valor seja especificado. 

# IV. PRIMARY KEY (Chave Primária)
-- A PRIMARY KEY identifica de forma única cada registro em uma tabela do banco de dados.
-- Chaves primárias devem conter valores únicos.
-- Uma coluna de chave primária não pode conter valores NULL. 
-- Cada tabela deve conter 1 e apenas 1 chave primária.

# V. FOREIGN KEY (Chave Estrangeira)
-- Uma FOREIGN KEY em uma tabela é um campo que aponta para uma chave primária em outra tabela. 

DROP TABLE IF EXISTS dAlunos;
DROP TABLE IF EXISTS dCursos;
DROP TABLE IF EXISTS fMatriculas;


CREATE TABLE IF NOT EXISTS dAlunos(
	ID_Aluno INT,
	Nome_Aluno VARCHAR(100) NOT NULL,
	Email VARCHAR(100) NOT NULL,
	PRIMARY KEY(ID_Aluno)
);

CREATE TABLE IF NOT EXISTS dCursos(
	ID_Curso INT,
	Nome_Curso VARCHAR(100) NOT NULL,
	Preco_Curso DECIMAL(10, 2) NOT NULL,
	PRIMARY KEY(ID_Curso)
);

CREATE TABLE IF NOT EXISTS fMatriculas(
	ID_Matricula INT,
	ID_Aluno INT NOT NULL,
	ID_Curso INT NOT NULL,
	Data_Cadastro DATE NOT NULL,
	PRIMARY KEY(ID_Matricula),
	FOREIGN KEY(ID_Aluno) REFERENCES dAlunos(ID_Aluno),
	FOREIGN KEY(ID_Curso) REFERENCES dCursos(ID_Curso)
);
```


### Aula 6: INSERT INTO - Inserindo dados em uma tabela no banco de dados

```sql
# 5. Inserindo dados nas tabelas. 

INSERT INTO dAlunos(ID_Aluno, Nome_Aluno, Email)
VALUES
	(1, 'Ana'	, 'ana123@gmail.com'		),
	(2, 'Bruno'	, 'bruno_vargas@outlook.com'	),
	(3, 'carla'	, 'carlinha1999@gmail.com'	),
	(4, 'Diego'	, 'diicastroneves@gmail.com'	);
    
SELECT * FROM dAlunos;


INSERT INTO dCursos(ID_Curso, Nome_Curso, Preco_Curso)
VALUES
	(1, 'Excel'	, 100),
	(2, 'VBA'	, 200),
	(3, 'Power BI'	, 150);
    
SELECT * FROM dCursos;


INSERT INTO fMatriculas(ID_Matricula, ID_Aluno, ID_Curso, Data_Cadastro)
VALUES
	(1, 1, 1, '2021-03-11'),
	(2, 1, 2, '2021-06-21'),
	(3, 2, 3, '2021-01-08'),
	(4, 3, 1, '2021-04-03'),
	(5, 4, 1, '2021-05-10'),
	(6, 4, 3, '2021-05-10');
    
SELECT * FROM fMatriculas;
```


### Aula 7: UPDATE - Atualizar registros de uma tabela

```sql
# 6. Atualizando dados de uma tabela com o UPDATE

UPDATE dCursos
SET Preco_Curso = 300
WHERE ID_Curso = 1;

SELECT * FROM dCursos;
```


### 

```sql
# 7. Deletando registros de uma tabela

DELETE FROM fMatriculas
WHERE ID_Matricula = 6;

SELECT * FROM fMatriculas;
```


### Aula 9: TRUNCATE TABLE x DROP TABLE

```sql
# TRUNCATE TABLE x DROP TABLE

-- TRUNCATE TABLE: Deleta todos os registros da tabela de uma vez, mas a tabela continua existindo.

-- DROP TABLE: Deleta todos os registros da tabela, inclusive a própria tabela. 

SELECT * FROM fMatriculas;

TRUNCATE TABLE fMatriculas;
DROP TABLE fMatriculas;
```


-----------------
## Módulo 44: Functions e Stored Procedures

### Aula 1: Functions - Introdução
- 

```sql
-- 1. Introdução 
-- Uma função é uma rotina, um conjunto de instruções que você pode salvar no seu banco de dados e executar quando quiser, sem a necessidade de criar o código do zero toda vez que você precisar dele. 

-- 2. Sintaxe
/*

DELIMITER $$

CREATE FUNCTION nome_funcao(param1 tipo1, param2 tipo2)
RETURNS tipo DETERMINISTIC
BEGIN
	instruções1;
	instruções2;
	instruções3;
	RETURN expressao
END $$

DELIMITER ;

SELECT nome_funcao(valor1, valor2);
*/
```


### Aula 2: Functions - Exemplo 1
- Exemplo 1. Crie uma função que retorna o seguinte texto: "Olá _____, tudo bem?"

```sql
DELIMITER $$

CREATE FUNCTION fn_BoasVindas(nome VARCHAR(100))
RETURNS VARCHAR(100) DETERMINISTIC
BEGIN
	RETURN CONCAT('Olá ', nome, ', tudo bem?');
END $$

DELIMITER ;
```


### Aula 3: Functions - Exemplo 2
- Exemplo 2. Crie uma função chamada fn_Faturamento, que receba como parâmetros de entrada o preço (DECIMAL) e a quantidade (INT), e retorne o faturamento da venda, representado pela multiplicação entre preço e quantidade. 

```sql
DELIMITER $$

CREATE FUNCTION fn_Faturamento(preco DECIMAL(10, 2), quantidade INT)
RETURNS DECIMAL(10, 2) DETERMINISTIC
BEGIN
	RETURN preco * quantidade;
END $$

DELIMITER ;
```

- Exemplo 3. Crie uma função que substitua de um texto os caracteres com acentos para caracteres sem acentos (exemplo: 'á' por 'a', 'à' por 'a', e assim vai), assim como substituir o ç por c.

```sql
DELIMITER $$

CREATE FUNCTION fn_RemoveAcentos(texto VARCHAR(100))
RETURNS VARCHAR(100) DETERMINISTIC
BEGIN
	SET texto = REPLACE(texto, 'á', 'a'),
	texto = REPLACE(texto, 'é', 'e'),
	texto = REPLACE(texto, 'í', 'i'),
	texto = REPLACE(texto, 'ó', 'o'),
	texto = REPLACE(texto, 'ú', 'u'),
	texto = REPLACE(texto, 'à', 'a'),
	texto = REPLACE(texto, 'è', 'e'),
	texto = REPLACE(texto, 'ì', 'i'),
	texto = REPLACE(texto, 'ò', 'o'),
	texto = REPLACE(texto, 'ù', 'u'),
	texto = REPLACE(texto, 'ã', 'a'),
	texto = REPLACE(texto, 'õ', 'o'),
	texto = REPLACE(texto, 'Á', 'A'),
	texto = REPLACE(texto, 'É', 'E'),
	texto = REPLACE(texto, 'Í', 'I'),
	texto = REPLACE(texto, 'Ó', 'O'),
	texto = REPLACE(texto, 'Ú', 'U'),
	texto = REPLACE(texto, 'À', 'A'),
	texto = REPLACE(texto, 'È', 'E'),
	texto = REPLACE(texto, 'Ì', 'I'),
	texto = REPLACE(texto, 'Ò', 'O'),
	texto = REPLACE(texto, 'Ù', 'U'),
	texto = REPLACE(texto, 'Ã', 'A'),
	texto = REPLACE(texto, 'Õ', 'O'),
	texto = REPLACE(texto, 'ç', 'c'),
	texto = REPLACE(texto, 'Ç', 'C'),
	texto = REPLACE(texto, 'â', 'a'),
	texto = REPLACE(texto, 'ê', 'e'),
	texto = REPLACE(texto, 'î', 'i'),
	texto = REPLACE(texto, 'ô', 'o'),
	texto = REPLACE(texto, 'û', 'u'),
	texto = REPLACE(texto, 'Â', 'A'),
	texto = REPLACE(texto, 'Ê', 'E'),
	texto = REPLACE(texto, 'Î', 'I'),
	texto = REPLACE(texto, 'Ô', 'O'),
	texto = REPLACE(texto, 'Û', 'U');
        RETURN texto;
END $$

DELIMITER ;

SELECT
	Loja,
	Endereco,
	fn_RemoveAcentos(Endereco)
FROM lojas;
```


### Aula 6 de 11: Para que serve esse DETERMINISTIC

```sql
-- Exemplo 1. Crie uma função que retorna o seguinte texto: "Olá _____, tudo bem?"

DELIMITER $$

CREATE FUNCTION fn_BoasVindas2(nome VARCHAR(100))
RETURNS VARCHAR(100)
BEGIN
	RETURN CONCAT('Olá ', nome, ', tudo bem?');
END $$

DELIMITER ;

-- Error Code: 1418. This function has none of DETERMINISTIC...

-- Ao criar uma função armazenada, você deve declarar que ela é determinística ou que não modifica os dados. Caso contrário, pode ser inseguro para recuperação ou replicação de dados. 


-- Solução 1)
-- Fazer da forma como fizemos até agora

-- Solução 2)
SET GLOBAL log_bin_trust_function_creators = 1;

-- Documentação: 
-- https://dev.mysql.com/doc/refman/8.0/en/stored-programs-logging.html
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
