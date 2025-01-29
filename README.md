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
