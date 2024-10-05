# Histórico de aulas e das minhas observações do curso de Data Analytics
# 🫣 AULA 1 - 27/07/2024
Testando a ferramenta na minha primeira aula do curso de Data Analytics. Tendo em vista que não conheço muita coisa da área de dados, estou com dificuldades em entender alguns termos - o que é normal. No entanto, a professora vem da minha área de atuação (Setor de Gestão de Pessoas), então isso além de me tranquilizar, me deixou animado para aprender mais sobre como convergir essas duas áreas.
# 🤔 AULA 2 - 03/08/2024
Banco de dados é uma coleção organizada de dados que pode ser facilmente acessada, gerenciada e atualizada. Ele é utilizado para armazenar informações de maneira estruturada, assim como organizamos uma planilha, com colunas e linhas. A área de dados usa nomeclaturas diferentes como, por exemplo, tupla (que significa linha).
## Banco de dados relacionais:
São informações que se relacionam, como o nome propõe. Por exemplo: uma turma de alunos que relaciona as turmas aos professores. Essas relações se dão a partir de tabelas que são idênticas a planilhas do Excel, mas estruturadas de uma forma organizada.
## SGBD: Sistemas de Gerenciamento de Banco de Dados
Exemplos: PostgreSQL, Oracle, SQLServer, MYSQL etc
## Como organizar meu Banco de Dados:
Primeiro é preciso fazer um estudo do cliente, levantando as informações cruciais do negócio. O que quero entender? E assim levanto todas as tabelas necessárias: funcionários, empresas de registro, posto de trabalho, funções...
Após é preciso desenhar os relacionamentos, ou seja, o cruzamento de informações.
Por fim, eu irei ao SQL criar os comandos do Banco de Dados
![image](https://github.com/user-attachments/assets/02618b8a-e2ee-4dc0-b681-e972efbacb54)
## Valores de texto (string)
CHAR - textos pequenos de 1 a 255 caracteres (nesse caso ele costuma estar mais próximo do 1 do que do 255)
VACHAR ou CHARACTER VARYING - textos maiores de 1 a 255 caracteres (nesse caso ele costuma estar mais próximo do 255 do que do 1)

É importante entender que nossa string precisa ser conforme a informação que iremos processar. Se eu seleciono minha string em CHAR e na tupla haver mais que 255 caracteres, o Banco vai "quebrar"

Outro questionamento importante é o processamento de dados. Tudo gasta memória, portanto a forma como vamos caracterizar nossa string fará diferencia.
*INT, FLOAT, NUMERIC e SMALLINT* são os mais comuns nos valores númericos

Valores de data: DATE, TIME, TIMESTAMP

## DDL - Linguagem e Definifição de Dados (mais haver com a estrutura)
CREATE table - criar uma tabela

DROP table - apaga/excluir uma tabela

ALTER table - alterar a estrutura de uma tabela

TRUNCATE table - excluir todas as linhas de uma tabela

## DML - Linguagem de Manipulação de Dados (mais haver com os dados dentro da estrutura, ou valores)
SELECT - selecionar uma tupla

INSERT - incluir um registro na tabela

UPTADE - alterar os valores dos dados de uma tabela

DELETE - excluir um dado da tabela

## Criando o primeiro Banco de Dados no PostgreeSQL

Observe que clicamos em QUERY TOOL na Public e no lado direito digita o comando. 
![image](https://github.com/user-attachments/assets/17f0c0ca-1038-4bff-a6ae-3e133251d303)

Estamos usando o CHARACTER VARYING para as maioria justamente porque são textos que não são curtos geralmente. Importante lembrar: se não faremos operações com um número, ele é TEXTO. Por isso, um CPF é texto e não número.

![image](https://github.com/user-attachments/assets/79106730-da64-4ad7-8a0f-d9156a4ce4d7)

ID serial é porque é progressivo. Conforme for cadastrando, ele vai criando 1,2,3,4,5,6...

No numeric é limitado a 18 dígitos e o 2 quer dizer duas casas decimais

Na casa propria o Boolean significa que é algo com duas alternativas como SIM ou NÃO

Em CONSTRAINT (esse nome é o comando do postgree) significaria dizer que o "pessoa_pkey" que significa que a chave primária dessa tabela (pkey) é único, ou seja, aquele ID progressivo é único.

![image](https://github.com/user-attachments/assets/2a406d3a-327e-4be9-ad69-72462d08cdd7)

Caso eu esteja preenchendo um SCRIPT de SQL no Postgree eu não preciso ficar fazendo trecho a trecho. Posso selecionar o que quero executar e ele executará só o que está marcado conforme imagem acima. A professora sugeriu fazer etapa por etapa, o que não sei se é interessante.

Em um cliente que tenha um sistema ERP comum, ou até mesmo sistemas financeiros ou de departamento pessoal simples, já possuem banco de dados. Isso significa que através de uma ATS eu consigo migrar esses dados para um banco de dados novo que eu esteja fazendo ou organizando.

## Exemplo de SCRIPT SQL para criação de tabela e inserção de dados

Lembrando que criar tabela pode ser feito através da interface do postgree conforme imagens abaixo

![image](https://github.com/user-attachments/assets/a86e644e-9e92-47e6-b527-1fa1c2f9de8a)
![image](https://github.com/user-attachments/assets/9adc371a-c982-4363-9e33-d5fcabd5dd90)

Esse abaixo seria o Script do mesmo procedimento, porém via SQL, em vez do postgree. É importante salientar que para criar tabela pode ser via postgree e SQL, mas para INSERT não, essa é exclusivamente via SQL.

```sql
CREATE TABLE IF NOT EXISTS rh.pessoa
(id serial,
nome character varying,
cpf character varying,
email character varying,
nascimento date,
renda numeric(18,2),
casa_propria boolean,
CONSTRAINT pessoa_pkey PRIMARY KEY (id));

INSERT INTO rh.pessoa (nome, cpf, email, nascimento, renda, casa_propria)
VALUES ('Pedro', '01234567890', 'pedro@digital.com.br', '1990-01-01', '2450.75', 'true')
VALUES ('Tauany', '01234585890', 'tauany@digital.com.br', '1991-01-01', '2250.75', 'true');
```

Quem coloca a string como character varying precisa preencher o valor entre a aspa única como ao lado 'Exemplo'

Quando for identificado o texto como INTERGER é preciso apontar um ID como 1,2,3,4... Quando é SERIAL isso é automático. Fica a dica...

PARA VISUALIZAR O RESULTADO DO SCRIPT SQL COMO TABELA:
![image](https://github.com/user-attachments/assets/8d261e03-2a14-4c8a-83d8-9395f11569dd)

APARECERÁ ASSIM:
![image](https://github.com/user-attachments/assets/d493a432-4ad3-4c87-b970-68f368096738)

```
INSERT INTO rh.estado (id, sigla, nome)
VALUES (5, 'BA', 'BAHIA'),
(6, 'CE', 'CEARA'),
(7, 'DF', 'DISTRITO FEDERAL'),
(8, 'ES', 'ESPIRITO SANTO')
```

# 😊 AULA 03 - 10/08/2024

## Modelagem de dados: é o processo que visualizamos, obtemos insights e fazemos a concepção dos dados antes da criação efetiva do banco de dados.

É preciso entender como o negócio funciona primeiro para só então estruturar o banco de dados. O modelo conceitual foca no entendimento dos REQUISITOS do sistema e do negócio. Isso se faz através de uma abstração dessas informações com a equipe de negócios.

"Linguagem alto nível": tem haver com a linguagem humana, interação pessoal

"Linguagem baixo nível": tem haver com a linguagem da máquina, os códigos

## Cardinalidade

1:1 Um pra um. Exemplo: um setor/departamento que é liderado por um coordenador

1:N Um pra muitos. Exemplo: um setor/departamento que contém muitos colaboradores

N:N Muito para muito. Exemplo: muitos livros que podem ser comprados por muitos clientes

Definindo as tabelas necessárias, chamaríamos elas de ENTIDADES. O software para montar a modelagem sugerido pela professora foi o BRMW conforme print abaixo.

## MODELAGEM CONCEITUAL (boa para apresentar ao cliente)

![image](https://github.com/user-attachments/assets/56bc5bb8-9eaf-417e-8d73-eeed070ba521)

## MODELAGEM LÓGICA

![image](https://github.com/user-attachments/assets/702cf342-1d51-4529-9d1b-634a1f8f8f38)

Observações gerais no modelo que fiz de modelagem lógica acima:

01. id é sempre PK e auto increment (serial)

02. texto é vachar e not null

03. a FK é uma característica de uma tabela principal como genero é uma caracteristica de pessoa

CLICANDO EM GERAR SQL ELE TE DAR O SCRIPT:

![image](https://github.com/user-attachments/assets/efcfe317-997c-431c-98ab-92732244800b)

Obs: ele não é perfeito (o script), precisa conferir e fazer ajustes, principalmente se for usar o Postgrees já que esse script não é adaptado a ele. Por exemplo, não existe AUTO_INCREMENT no Postgree trabalhando com SQL, lá o nome é SERIAL. E assim por diante... O ChatGPT pode corrigir e é importante que você pergunte a IA como se deu as correções. 

Exemplo. O BRMW gerou isto de SCRIPT SQL

```CREATE TABLE pessoa 
( 
 id INT PRIMARY KEY AUTO_INCREMENT,  
 nome VARCHAR(n) NOT NULL,  
 cpf VARCHAR(n) NOT NULL,  
 rg VARCHAR(n) NOT NULL,  
 ctps VARCHAR(n) NOT NULL,  
 id_genero INT,  
 UNIQUE (cpf,rg,ctps)
); 

CREATE TABLE genero 
( 
 id INT PRIMARY KEY AUTO_INCREMENT,  
 descricao VARCHAR(n) NOT NULL,  
); 

ALTER TABLE pessoa ADD FOREIGN KEY(id_genero) REFERENCES genero (id_genero)
```

Porém, o correto, para o POSTGRESQL seria:

```
CREATE TABLE Pessoa (
    id SERIAL PRIMARY KEY,
    nome VARCHAR NOT NULL,
    cpf VARCHAR NOT NULL UNIQUE,
    id_genero INT
);

CREATE TABLE Genero 
( 
 id SERIAL PRIMARY KEY,  
 descricao VARCHAR NOT NULL  
); 

ALTER TABLE Pessoa
ADD CONSTRAINT fk_pessoa_genero 
FOREIGN KEY (id_genero) 
REFERENCES Genero(id);
```

Professora sugeriu Midori Toyota para curso de SQL na Udemy

# 🫣 AULA 04 - 17/08/2024

Foi apresentado nessa aula o DBSCHEMA, um programa para criar a modelagem de dados como o da aula passada, mas com integração com SGBDs.

Clica com o botão direito e cria a tabela colocando o nome e nomeando as colunas. Exemplo da tela de criação abaixo:

![image](https://github.com/user-attachments/assets/db275cdd-fac4-4265-b8a9-1684710927fc)

Depois de criar as tabelas seguindo sempre a estrutura de ID (como pk, integer e serial) e as colunas gerais da tabela (como not null), incluindo as que serão FK (como not null) você pode gerar o script sql nesse comando:

![image](https://github.com/user-attachments/assets/c5480514-1ddd-4165-b50f-32c685d483c2)

Para fazer as ligações de FK, é preciso clicar e arrastar da "tabela protagonista" para a "tabela coadjuvante", ou seja, se na Tabela Cliente tem uma FK chamada id_genero, então eu clico em id_genero e arrasto até o ID (PK) da Tabela Genero. Nesse exemplo, a Tabela Cliente é a protagonista e a Tabela Genero é a coadjuvante (se fizer o inverso, não vai dar certo).

Todos os ALTER TABLE (geralmente as FK) eu juntei em um bloco de notas e copiei no final do script segundo orientação da professora (acho que isso é visando um código mais limpo e organizado):

![image](https://github.com/user-attachments/assets/6be7d4ba-f64a-4f11-a1e7-84e69575ed03)

Esse foi o script que eu gerei através do dbschema e rodei no postgreesql

```
CREATE TABLE public.cliente ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	cod_cliente          VARCHAR(100)   NOT NULL,
	cpf                  VARCHAR(100)   NOT NULL,
	rg                   VARCHAR(100)   NOT NULL,
	data_cadastro        DATE   NOT NULL,
	id_genero            INTEGER   NOT NULL,
	id_endereco          INTEGER   NOT NULL,
	CONSTRAINT pk_cliente PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.genero ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	CONSTRAINT pk_genero PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.tipo_contato_cliente ( 
	id                   INTEGER   NOT NULL,
	descricao            VARCHAR(100)   NOT NULL,
	id_tipo_contato      INTEGER   NOT NULL,
	id_cliente           INTEGER   NOT NULL,
	CONSTRAINT pk_tipo_contato_cliente PRIMARY KEY ( id )
 );

CREATE TABLE public.loja_cliente ( 
	id                   INTEGER   NOT NULL,
	id_cliente           INTEGER   NOT NULL,
	id_loja              INTEGER   NOT NULL,
	CONSTRAINT pk_loja_cliente PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.loja ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	cod_loja             VARCHAR(100)   NOT NULL,
	id_endereco          INTEGER   NOT NULL,
	CONSTRAINT pk_loja PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.endereco ( 
	id                   INTEGER   NOT NULL,
	logradouro           VARCHAR(100)   NOT NULL,
	cep                  VARCHAR(100)   NOT NULL,
	numero               VARCHAR(100)   NOT NULL,
	id_bairro            INTEGER   NOT NULL,
	CONSTRAINT pk_endereco PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.tipo_contato ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	CONSTRAINT pk_tipo_contato PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.bairro ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	id_cidade            INTEGER   NOT NULL,
	CONSTRAINT pk_bairro PRIMARY KEY ( id )
 );
 
 CREATE TABLE public.cidade ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	id_estado            INTEGER   NOT NULL,
	CONSTRAINT pk_cidade PRIMARY KEY ( id )
 );

CREATE TABLE public.estado ( 
	id                   INTEGER   NOT NULL,
	nome                 VARCHAR(100)   NOT NULL,
	CONSTRAINT pk_estado PRIMARY KEY ( id )
 );

ALTER TABLE public.cliente ADD CONSTRAINT fk_cliente_genero FOREIGN KEY ( id_genero ) REFERENCES public.genero( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.cliente ADD CONSTRAINT fk_cliente_endereco FOREIGN KEY ( id_endereco ) REFERENCES public.endereco( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.tipo_contato_cliente ADD CONSTRAINT fk_tipo_contato_cliente_tipo_contato FOREIGN KEY ( id_tipo_contato ) REFERENCES public.tipo_contato( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.tipo_contato_cliente ADD CONSTRAINT fk_tipo_contato_cliente_cliente FOREIGN KEY ( id_cliente ) REFERENCES public.cliente( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.loja_cliente ADD CONSTRAINT fk_loja_cliente_cliente FOREIGN KEY ( id_cliente ) REFERENCES public.cliente( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.loja_cliente ADD CONSTRAINT fk_loja_cliente_loja FOREIGN KEY ( id_loja ) REFERENCES public.loja( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.loja ADD CONSTRAINT fk_loja_endereco FOREIGN KEY ( id_endereco ) REFERENCES public.endereco( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.endereco ADD CONSTRAINT fk_endereco_bairro FOREIGN KEY ( id_bairro ) REFERENCES public.bairro( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.bairro ADD CONSTRAINT fk_bairro_cidade FOREIGN KEY ( id_cidade ) REFERENCES public.cidade( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;

ALTER TABLE public.cidade ADD CONSTRAINT fk_cidade_estado FOREIGN KEY ( id_estado ) REFERENCES public.estado( id ) ON DELETE NO ACTION ON UPDATE NO ACTION;
```
Gerando isso aqui:

![image](https://github.com/user-attachments/assets/b1c7ef7b-5f7d-4d35-a908-fd229e04b7ae)

# 😅 AULA 05 - 24/08/2024

A professora trouxe o seguinte Minicenário:

Uma empresa é organizada em departamentos, cada um com um nome único, uma sigla e um funcionário responsável por gerenciá-lo.

Uma data determina quando o funcionário iniciou suas atividades de gerência no departamento.

Um departamento da empresa controla vários projetos, cada um com um código único e um nome.

Um funcionário da empresa está vinculado a um departamento, mas pode trabalhar em vários projetos, sendo determinado o número de horas semanais dedicadas a cada um. Além disso, todo funcionário tem um supervisor direto.

Para cada funcionário são armazenadas informações como: nome, CPF, endereço, telefone(s) de contato,salário e dependentes (primeiroNome, idade, parentesco)

## A partir dos meus entendimentos, criei a seguinte modelagem:

![image](https://github.com/user-attachments/assets/48bc0f8e-46e0-4e2b-b4b0-a1da74152426)

Outro Minicenário foi:

A empresa XPZ Corporation é uma empresa que oferece serviços de Outsourcing e vem crescendo consideravelmente em todo Brasil. 

A empresa contrata seus funcionários, registra nos respectivos departamentos de acordo com suas especialidades (desenvolvimento, banco de dados, infraestrutura e análise de dados) e então aloca o funcionário em projetos. 

Alguns funcionários trabalham remotamente e outros são alocados fisicamente em clientes da empresa. 

Funcionários com perfil generalista podem trabalhar em mais de um projeto simultaneamente e quando
simultaneamente e quando isso ocorre, o custo do funcionário é alocado de acordo com o percentual trabalhado em cada projeto.

Todos os funcionários passam por uma avaliação anual, que define as promoções ou mesmo desligamento da empresa, caso o funcionário tenha avaliações ruins por dois anos consecutivos. 

Cada funcionário da empresa possui um supervisor responsável pelas avaliações anuais, por atribuir tarefas e ajudar em caso de dúvidas.

Cada departamento possui um gerente responsável pela organização dos projetos naquele departamento. Cada departamento controla diversos projetos.

Todos os empregados são contratados e todas as informações são registradas em planilhas Excel. Como a empresa fornece plano de saúde aos funcionários e extensivo aos familiares em primeiro grau, os dados de dependentes também são registrados.

Códigos de identificação únicos são usados em todos os registros e datas são usadas no registro de empregados; gerentes e supervisores. 

Como os projetos ocorrem em clientes em todo Brasil, a localização de cada projeto também é registrada. Cada funcionário tem apenas um supervisor e cada departamento tem apenas um gerente.

A empresa pretende implementar um sistema de informação que no futuro permita extrair relatórios sobre o funcionamento dos departamentos, como funcionários alocados por projeto e supervisores das equipes de alta performance.

## A partir dos meus entendimentos, criei a seguinte modelagem:

![image](https://github.com/user-attachments/assets/ce30bf69-a56b-4ca6-9626-b1026a785b8c)

Esperando a correção...

# 😁 AULA 06 - 31/08/2024

Começamos a aula entendendo como faz o backup de uma base de dados bem como se restaura.

Aqui é para entender que o comando * significa "all", como também posso definir o que quero selecionar
![image](https://github.com/user-attachments/assets/12f7497d-730e-49ed-8787-2ed8b297c785)

Aqui para entender o comando UPDATE. Lembrando que toda string vachar tem de estar entre aspas (uma aspa)
![image](https://github.com/user-attachments/assets/78394c03-2c76-4a7b-8238-ae4defa1e21b)

Resumo da professora sobre os comandos SQL
![image](https://github.com/user-attachments/assets/9525554c-bd93-46e1-ba4f-9ac9345f94b5)

Tem o PDF desse resumo da professora aqui:
https://www.linkedin.com/posts/nayaraba_resumo-sql-inciantes-activity-7206804085562421248-fKL7?utm_source=share&utm_medium=member_android

## Comandos variados

Nessa aula aprendemos vários tipos de comandos SQL como: SELECT, DELETE, ALTER, operações como SUM, ORDER BY, INNER JOIN, condições como WHERE, FROM e etc. Esses conceitos estão na apresentação da aula 06.

No exemplo do INNER JOIN, foram usadas abreviações para as tabelas. Uma prática para simplificar as buscas como no exemplo abaixo
![image](https://github.com/user-attachments/assets/a1b07de5-cf88-4a09-949c-6dc199cd0775)

# 🙈 AULA 07 - 14/09/2024

Faltei... 

SCRIPT QUE A PROF DISPONIBILIZOU SOBRE JOINS

```
--- INNER JOIN (JUNÇÃO SIMPLES)
-- EX. CARGO + SALARIO

SELECT 
	c.nome as cargo, 
	salario
FROM corporativo.cargo c
INNER JOIN corporativo.lotacao l on  c.id = l.id_cargo 

--- EX. ESSE COMANDO TRÁS O NOME DO CARGO E O SALÁRIO DA LOTAÇÃO,
--- MAS APENAS OS REGISTROS QUE ESTÃO PRESENTES EM AMBAS AS TABELAS.


--- LEFT JOIN (JUNÇÃO A ESQUERDA)

SELECT 
	c.nome as cargo, 
	salario
FROM corporativo.cargo c
LEFT JOIN corporativo.lotacao l on  c.id = l.id_cargo 

--- EX. ESSE COMANDO RETORNA TODOS OS CARGOS, MESMO QUE NÃO TENHAM CORRESPONDENCIA
--- NA TABELA LOTAÇÃO. QUANDO NÃO HOUVER CORRESPONDENCIA, O VALOR DE SALARIO SERÁ NULL.


--- RIGHT JOIN (JUNÇÃO A DIREITA)

SELECT 
	c.nome as cargo, 
	salario
FROM corporativo.cargo c
RIGHT JOIN corporativo.lotacao l on  c.id = l.id_cargo 

--- EX. ESSE COMANDO RETORNA TODAS AS LINHAS DA TABELA LOTACAO, MESMO QUE NÃO TENHAM
--- CORRESPONDENCIA NA TABELA CARGO.
--- QUANDO NÃO HOUVER CORRESPONDENCIA, O VALOR DO NOME DO CARGO SERÁ NULL.

--- FULL OUTER JOIN (JUNÇÃO COMPLETA)

SELECT c.nome, salario
FROM corporativo.cargo c
FULL JOIN corporativo.lotacao l on c.id = l.id_cargo 

--- EX. ESSE COMANDO RETORNA TODAS AS LINHAS DE AMBAS AS TABELAS.
--- SE HOUVER REGISTROS SEM CORRESPONDENCIA EM UMA DAS TABELAS, AS COLUNAS
--- DA OUTRA TABELA SERÃO PREENCHIDAS COM NULL.
```

# 😅 AULA 08 - 21/09/2024

Essa é uma revisão da aula passada, que eu não vim...

Todo operador (AVG, SUM etc) inicia com ele e a coluna que se quer calcular. 

Exemplo (a mistura de vários comandos, não funcionará necessariamente)
```
SELECT pcd,
FROM corporativo.funcionario
WHERE is true
ORDER BY ASC
AVG(pretensao_salarial) ; numeric (18,2) --- Esse comando (o numeric) é para simplificar a visualização do número em duas casas decimais
AS media_pretensao --- Só para renomear a nova informação
AND pcd = true --- Quando se quer gerar duas condições
OR --- Quando quero "duas verdades"
NOT pcd --- Isso funciona para tirar os que não são pcd, como o pcd = true traz os que são
GROUP BY pcd --- É preciso colocar o Group By para identificar no que você quer calcular
HAVING AVG(pretensao_salarial) >=5000 --- O Having é para estipular uma outra condição dentro da condição que eu já busquei, ou seja, depois de calcular a média, eu quero as médias iguais ou acima de 5000
SELECT MAX(pretensao_salarial) --- A pretensão maxima como é obvio ser
FROM corporativo.funcionario

SELECT
nome as cargo --- Só renomeei para melhor visualização
salario
FROM corporativo.cargo --- No entanto, não tem salario na tabela cargo, tem na lotacao, portanto precisa juntar (JOIN)
INNER JOIN corporativo.lotacao --- Juntando
ON cargo.id = lotacao.id_cargo --- Atribuindo uma condição que considera que há o id_cargo na tabela da lotação, ou seja, lá tem essa FK
Estou definindo que o cargo.id seja IGUAL (=) a FK que está na tabela lotacao chamada de lotacao.id_cargo (assim ela vai juntar)
OU SEJAAAAAAAAAA sempre que for fazer o inner join deve-se referenciar a tabela que contém as FK. A professora chamou de "Tabela Pai", enquanto as outras são "filhas"
```
Pode-se dar apelidos as tabelas abreviando para a primeira letra ou para as 3 primeiras letras caso você queira escrever menos nas querys
Exemplo:
SELECT funcionario.nome func
Em vez disso
SELECT func.nome

Se usar o apelido, tem que usar em todos e para dar esse apelido basta colocar ele do lado do select como acima.

Lógica do SQL:
![image](https://github.com/user-attachments/assets/ac0d61b5-857f-40ad-b184-33f531a7a73f)

SCRIPT DA ATIVIDADE FEITA EM SALA DE AULA

```
--- QUESTÃO 1: 
---Selecione todos os registros da tabela sales.funnel, exibindo as colunas: visit_id, 
---customer_id, product_id, e store_id.

SELECT * FROM sales.funnel

SELECT 
	 visit_id,
	 customer_id, 
	 product_id,
	 store_id
FROM sales.funnel;


SELECT 
	 visit_id 
	,customer_id 
	,product_id
FROM sales.funnel;	


--- QUESTÃO 2: 
--- Liste todos os produtos (product_id) que foram adicionados ao carrinho, exibindo 
--- também as datas em que isso ocorreu (add_to_cart_date).

SELECT * FROM sales.customers --- CLIENTE PF
SELECT * FROM sales.products --- PRODUTOS
SELECT * FROM sales.stores --- CLIENTE PJ
SELECT * FROM sales.funnel --- VENDAS -- OBS TEM VÁRIAS CHAVES ESTRANGEIRAS.

--- OPÇÃO COM JOIN
SELECT 
	products.product_id as produto,
	funnel.add_to_cart_date as data_carrinho	
FROM sales.funnel 
INNER JOIN sales.products ON products.product_id = funnel.product_id

--- OPÇÃO SEM O JOIN
SELECT 
	product_id as produto,
	add_to_cart_date as data_carrinho
FROM sales.funnel 

--- QUESTÃO 3: 
--- Recupere todos os registros onde a data de pagamento (paid_date) não é nula. 
--- Exiba os campos visit_id, customer_id, e paid_date. 

SELECT 
	visit_id as visita,
	customer_id as cliente,
	paid_date as data_pagamento
FROM sales.funnel 
WHERE paid_date IS NOT NULL;

--- QUESTÃO 4: 
--- Liste as visitas onde o cliente iniciou o processo de checkout 
--- (start_checkout_date), exibindo as colunas visit_id, customer_id, product_id e 
--- start_checkout_date. 

SELECT 
	visit_id as visita,
	customer_id as cliente,
	product_id as produto,
	start_checkout_date as data_checkout
FROM sales.funnel 
WHERE start_checkout_date IS NOT NULL;

--- QUESTÃO 5: 
--- Encontre as visitas onde o desconto aplicado foi maior do que 20% (discount < 
--- (-0.20). Exiba as colunas visit_id, product_id, e discount.

SELECT 
	visit_id,
	product_id,
	discount
FROM sales.funnel
WHERE discount > -0.20

--- QUESTÃO 6: 
--- Selecione as visitas feitas por clientes em lojas específicas. Liste todos os 
--- registros onde o store_id é 'BF580E604866'. Exiba as colunas visit_id, customer_id, 
--- product_id, e store_id.

SELECT 
	visit_id,
	customer_id,
	product_id,
	store_id
FROM sales.funnel
WHERE store_id = 'BF580E604866'

--- QUESTÃO 7: 
--- Calcule a média do desconto aplicado em todas as transações. Exiba a média do 
--- campo discount. 
--- :: type_cast é o nome do conversor.

SELECT 
	AVG(discount)::numeric(18,2) as media_desconto
FROM sales.funnel	


--- QUESTÃO 8: 
--- Conte quantas transações foram iniciadas com um processo de checkout 
--- (start_checkout_date). Nomeie a contagem como checkout_count.

SELECT
	count(start_checkout_date) as checkout_count
FROM sales.funnel
WHERE start_checkout_date IS NOT NULL;

--- QUESTÃO 9: 
--- Calcule a taxa de conversão para cada loja. Para isso, obtenha o número total de 
--- visitas (COUNT(*)) e o número de transações finalizadas (onde paid_date não é 
--- nulo), depois calcule a taxa de conversão (transações finalizadas / total de visitas 
--- * 100). Exiba store_id, o total de visitas, transações finalizadas e a taxa de 
--- conversão, nomeando a coluna como conversion_rate.

--- calculo - (vendas/visitas)*100 (100 transformar em percentual)

SELECT * FROM sales.customers --- CLIENTE PF
SELECT * FROM sales.products --- PRODUTOS
SELECT * FROM sales.stores --- CLIENTE PJ
SELECT * FROM sales.funnel --- VENDAS -- OBS TEM VÁRIAS CHAVES ESTRANGEIRAS.

--- visit_id = total de visitas
--- paid_date (data de pagamento) = vendas

---- Calcula a taxa de conversão como uma porcentagem de transações finalizadas em relação ao 
---número de visitas. Se não houver visitas, 
--- a taxa de conversão é definida como 0 usando a função COALESCE para evitar divisão por zero.

--- O CASE WHEN é uma condição que verifica se o campo paid_date contém um valor 
--- (significando que houve pagamento e, portanto, a transação foi finalizada). Se a condição for 
--- verdadeira, a consulta conta essa linha.

--- Exemplo: Se em 200 visitas, 50 delas resultaram em transações pagas, o valor de transacao_finalizada 
--- será 50 para essa loja.


--- COM O COLASCE
SELECT 
    store_id,
    count(visit_id) AS total_visita,
    count(case when paid_date is not null then 1 end) as transacao_finalizada,
    coalesce(
        (count(case when paid_date is not null then 1 end) * 100.0 / count(visit_id)),
		0
    ) as taxa_conversao
from sales.funnel
group by store_id;
	
	
--- QUESTÃO 10: 
--- Liste os 5 produtos mais vendidos (com transações pagas), exibindo as colunas 
--- product_id, paid_date e store_id. Ordene os resultados pela data de pagamento 
--- mais recente.

select
	product_id as produto, 
	MAX(paid_date) as data_pagamento, -- data mais recente
	store_id,
	count(*) as total_vendido
from sales.funnel
where paid_date is not null
group by product_id, store_id
order by total_vendido desc
limit 5;

----Por que usar MAX em vez de incluir paid_date no GROUP BY?
--- Agrupamento por product_id e store_id:

---A consulta está agrupando os dados por product_id (identificador do produto) e 
---store_id (identificador da loja). 
---Isso significa que, para cada combinação de produto e loja, você quer obter 
---a contagem total de vendas, sem dividir por data.
---Se incluirmos paid_date no GROUP BY, o resultado seria dividido por cada data 
---de pagamento, o que não faz sentido aqui, pois estamos interessados no total vendido por produto, 
---independentemente da data.

--- Selecionando a data mais recente:

--- Como estamos agrupando por produto e loja, mas ainda queremos saber a data mais recente 
---em que o produto foi vendido (ou seja, a última vez que houve uma transação), usamos a 
---função de agregação MAX(paid_date).
---MAX(paid_date) retorna a data mais recente da transação (o maior valor de paid_date) 
---dentro de cada grupo (neste caso, para cada combinação de product_id e store_id).

--- Resumo:
--- Usar MAX(paid_date) permite que você obtenha a data mais recente de venda para cada produto/loja, 
--- enquanto ainda agrupa os resultados para contar o total de vendas por produto.
--- Incluir paid_date no GROUP BY seria problemático, pois dividiria os resultados por data, 
--- enquanto o objetivo é somar o total de vendas, sem se preocupar com a data específica.
```


# 😒 AULA 09 - 28/09/2024

Na aula de hoje está sendo apresentado o conceito de DW - DATA WAREHOUSE. Foi explicado que os Banco de Dados Relacionais com todas suas tabelas infinitas de correlações não são usualmente utilizadas no dia-a-dia de um Analista de Dados. Na realidade, usa-se o DW para fazer um recorte de dados e tabelas relevantes para as análises que se quer fazer e é em cima disso que o Analista trabalha.

É comum existirem Analistas que recebem esses dados já em DW em vez de manipular Banco de Dados Relacionais (chamado de banco de produção).

Cria-se, então, um banco de dados novo para utilizar como STAGE - ou seja, o recorte do banco de produção.
Depois disso é que se faz as modelagens de Data Warehouse, trazendo do STAGE e não do banco de produção.

É possível criar as tabelas pelo DB SCHEMA conectando ele ao Postgres.

Tabela Fato x Tabela Dimensão
STAR MODEL x SNOWFLAKE MODEL

SCRIPT FEITO NA AULA

```
---> BANCO RELACIONAL (BANCO DE PRODUÇÃO) ---> BANCO DE STAGE (CÓPIA DE ALGUMAS INFORMAÇÕES DO
--- DO MEU BANCO RELACIONAL, GERALMENTE JÁ É UMA ESTRUTURA PARA CRIAR O MEU BANCO DATA WAREHOUSE) --->
--- BANCO DATA WAREHOUSE(BANCO DE DADOS DIMENSIONAL (TABELAS FATO E DIMENSÃO), NESSE BANCO, GERALMENTE
--- ELE TRÁS INFORMAÇÕES ESPECIFICAS DE UMA ÁREA, SETOR, FILIAL (NÃO TRÁS TUDO QUE TEM NO RELACIONAL))
--- NO BANCO DE STAGE EU COPIO TABELAS (PODE SELECIONAR COLUNAS)

--- CRIANDO UM BANCO DE STAGE

--- VOU FAZER UM RECORTE DE UM BANCO ESPECIFICO E LEVAR AS TABELAS QUE EU QUERO TRABALHAR.

--- PRIMEIRO PASSO CRIAR TABELAS.

--- COMO INSERIR OS DADOS SEM USAR A FORMA TRADICIONAL DO INSERT

---- Carregamento da stage forma de pagamento

insert into stage.forma_pagamento (id, descricao) -- TODAS AS COLUNAS DA MINHA MODELAGEM
select id, descricao from vendas.forma_pagamento

SELECT * FROM stage.forma_pagamento --- STAGE
SELECT * FROM vendas.forma_pagamento --- RELACIONAL (PRODUÇÃO))

 ---- Carregamento da stage pessoa física
 
insert into stage.pessoa_fisica (id, nome)
select id, nome from geral.pessoa_fisica

SELECT * FROM stage.pessoa_fisica
SELECT * FROM geral.pessoa_fisica

--- Carregamento da stage pessoa jurídica

insert into stage.pessoa_juridica (id, razao_social)
select id, razao_social from geral.pessoa_juridica

SELECT * FROM stage.pessoa_juridica
SELECT * FROM geral.pessoa_juridica

 --- Carregamento da stage nota fiscal
 
insert into stage.nota_fiscal
(id, id_vendedor, id_cliente, id_forma_pagto, data_venda, 
numero_nf, valor)
SELECT id, id_vendedor, id_cliente, id_forma_pagto, data_venda, 
numero_nf, valor
FROM vendas.nota_fiscal

--- COM * --- DEU CERTO -- A ORDEM TEM QUE ESTÁ IGUAL DA TABELA.
insert into stage.nota_fiscal
(id, id_vendedor, id_cliente, id_forma_pagto, data_venda, 
numero_nf, valor)
SELECT *
FROM vendas.nota_fiscal

SELECT * FROM stage.nota_fiscal
SELECT * FROM vendas.nota_fiscal

--- DEPOIS DO STAGE - EU CRIO E MODELO O MEU DATA WAREHOUSE (DW)

--- TABELAS DIMENSOES - ELAS SÃO TABELAS (TEXTO, CARACTERISTICA, DESCRIÇÕES)
--- TABELA FATO - ELAS SÃO TABELAS (NUMEROS, REGISTROS HISTORICOS, MOVIMENTAÇÕES, VALORES, DATA)

--- DIMENSÃO TEMPO


INSERT INTO data_warehouse.dim_tempo(data, ano, mes, dia, dia_da_semana, mes_extenso)
SELECT 
dt as data,
 EXTRACT(YEAR FROM dt) AS ano,
 EXTRACT(MONTH FROM dt) AS mes,
 EXTRACT(DAY FROM dt) AS dia,
 TO_CHAR(dt, 'Day') AS dia_da_semana,
 TO_CHAR(dt, 'Month') AS mes_extenso
 FROM
 generate_series(CURRENT_DATE - INTERVAL '30 years', 
CURRENT_DATE + INTERVAL '5 years', INTERVAL '1 day') AS dt;

SELECT * 
FROM data_warehouse.dim_tempo
ORDER BY data DESC

---- CARREGANDO OS DADOS


--- Carregamento Data Warehouse da dimensão forma de pagamento

 insert into data_warehouse.dim_forma_pagamento (id, descricao)
 select id, descricao from stage.forma_pagamento

 SELECT * FROM data_warehouse.dim_forma_pagamento
 SELECT * FROM stage.forma_pagamento


 ---- Carregamento Data Warehouse da dimensão cliente
 
 insert into data_warehouse.dim_cliente (id, nome)
 select distinct id_cliente, nome
 from stage.nota_fiscal nf
 inner join stage.pessoa_fisica pf on pf.id = nf.id_cliente ---- PESSOA FISICA
 union
 select distinct id_cliente, razao_social
 from stage.nota_fiscal nf
 inner join stage.pessoa_juridica pj on pj.id = nf.id_cliente --- PESSOA JURIDICA


 SELECT * FROM data_warehouse.dim_cliente

--- Carregamento Data Warehouse da dimensão vendedor

 insert into data_warehouse.dim_vendedor (id, nome)
 select distinct id_vendedor, nome
 from stage.nota_fiscal nf
 inner join stage.pessoa_fisica pf on pf.id = nf.id_vendedor

 SELECT * FROM data_warehouse.dim_vendedor


 ---Carregamento Data Warehouse da fato vendas
 
INSERT INTO data_warehouse.fato_vendas(
id, id_cliente, id_vendedor, id_forma_pagamento,  
id_data_venda, numero_nf, valor)
select nf.id, id_cliente, id_vendedor, id_forma_pagto, 
dt.id as id_data_venda, numero_nf, valor
from stage.nota_fiscal nf
inner join data_warehouse.dim_tempo dt on dt.data = nf.data_venda

SELECT * FROM data_warehouse.fato_vendas
```

# 😥 AULA 10 - 05/10/2024


Recaptulando as informações do DW. O Stage é um recorte do Banco Relacional. Nele, nós faremos uma cópia das informações do Banco, mas temos que criar novamente as tabelas, pois não da pra copiá-las.

Depois de copiá-las, a gente cria o DW. Nele, faremos UMA NOVA MODELAGEM que condensa as informações em TABELA FATO e TABELAS DIMENSÃO. Com as informações condensadas, copiaremos do stage para o DW o que queremos ver para, só depois, fazermos a ANÁLISE DE DADOS.

1. Analisar o Banco Relacional
2. Verificar onde estão as informações que meu cliente quer usar
3. Criar o STAGE e fazer o recorte do que queremos
4. Condensar as tabelas e construir uma nova modelagem para o DW

Tabela Dimensão só vão texto. Tabela Fato que podem ir valores.

```
--- 1º FAZER A MODELAGEM E CRIAÇÃO DAS TABELAS.
--- 2º ENTENDER SOBRE AS COLUNAS QUE VAI NAS DIMENSÕES E FATO
--- 3º CRIAR A MINHA DIM_TEMPO
--- 4º CRIAR AS DIMENSÕES, SEMPRE ANTES DA FATO.

--- DIM_TEMPO
--- PODE SER UM SCRIPT PADRÃO

INSERT INTO data_warehouse.dim_tempo(data, ano, mes, dia, dia_da_semana, mes_extenso)
SELECT 
	dt as data,
    EXTRACT(YEAR FROM dt) AS ano,
    EXTRACT(MONTH FROM dt) AS mes,
    EXTRACT(DAY FROM dt) AS dia,
    TO_CHAR(dt, 'Day') AS dia_da_semana,
    TO_CHAR(dt, 'Month') AS mes_extenso
FROM
    generate_series(CURRENT_DATE - INTERVAL '30 years', 
	CURRENT_DATE + INTERVAL '5 years', INTERVAL '1 day') AS dt;

SELECT * 
FROM data_warehouse.dim_tempo
ORDER BY id DESC


--- Carregamento da Dimensão de Região

INSERT INTO data_warehouse.dim_regiao (pais, cidade, regiao)
SELECT DISTINCT 
pais_navio as pais, 
cidade_navio as cidade, 
regiao_navio as regiao
FROM pedidos 

SELECT * FROM data_warehouse.dim_regiao
SELECT * FROM pedidos


--- Carregamento da Dimensão de Produtos

INSERT INTO data_warehouse.dim_produto (nome, categoria)
SELECT DISTINCT  
pr.nome, 
c.nome as categoria
FROM produtos pr
INNER JOIN categorias c on c.id = pr.id_categoria

SELECT * FROM data_warehouse.dim_produto
SELECT * FROM produtos


--- Carregamento da Fato

--- Identificar tabelas
--- Apontar as colunas que queremos trabalhar

INSERT INTO data_warehouse.fato_vendas(id_tempo,id_produto,id_regiao, quantidade, venda)

--- Selecionar os id das dimensões (tempo, produto e regiao)

SELECT
dt.id as id_tempo, --- dim_tempo
dp.id as id_produto, --- dim_produto
dr.id as id_regiao, --- dim_regiao

pd.quantidade, --- tabela de pedido detalhe
(pd.quantidade * pd.preco_unitario * (1 - pd.desconto))::numeric(18,2) as venda 
FROM pedidos p --- tabela de pedidos

INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id
INNER JOIN produtos pr ON pr.id = pd.id_produto
INNER JOIN data_warehouse.dim_tempo dt ON dt.data = p.data_pedido
INNER JOIN data_warehouse.dim_produto dp ON dp.nome = pr.nome
INNER JOIN data_warehouse.dim_regiao dr ON dr.cidade = p.cidade_navio and dr.pais = p.pais_navio 

SELECT * FROM data_warehouse.fato_vendas
SELECT * FROM produtos

SELECT SUM(venda)::numeric(18,2) as total_venda
FROM data_warehouse.fato_vendas
```

QUAIS AS VANTAGENS DE TER O DW EM VEZ DE FAZER CONSULTAS NO RELACIONAL? A PROF MOSTROU NA PRÁTICA ABAIXO

```
--1. Total de venda

---Relacional

--- Analisar a lógica de como calcular o total de vendas.

SELECT 
	SUM((pd.preco_unitario * pd.quantidade) * (1 - pd.desconto))::numeric(18,2) as total_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id

SELECT * FROM pedidos
SELECT * FROM pedido_detalhe

---Data Warehouse

SELECT SUM(venda)::numeric(18,2) as total_venda
FROM data_warehouse.fato_vendas 

SELECT * FROM data_warehouse.fato_vendas 

--2. Média de venda

---Relacional

SELECT AVG((pd.preco_unitario * pd.quantidade) * (1 - pd.desconto))::numeric(18,2) as media_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id

SELECT * FROM pedidos


---Data Warehouse

SELECT AVG(venda)::numeric(18,2) as media_venda
FROM data_warehouse.fato_vendas 

SELECT * FROM data_warehouse.fato_vendas 

--3. Maior venda

--- Relacional
--- o calculo se refere ao total da venda.

SELECT MAX((pd.preco_unitario * pd.quantidade) * (1 - pd.desconto))::numeric(18,2) as maior_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id


--- Data Warehouse

SELECT MAX(venda)::numeric(18,2) as maior_venda
FROM data_warehouse.fato_vendas 

--4. Menor venda

--- Relacional

SELECT MIN((pd.preco_unitario * pd.quantidade) * (1 - pd.desconto))::numeric(18,2) as menor_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id

--- Data Warehouse

SELECT MIN(venda)::numeric(18,2) as menor_venda
FROM data_warehouse.fato_vendas 


--5. Listar venda por ano
--- Vou particionar a minha data, utilizando o comando date_part
--- Uma operação para calcular o total das vendas (SUM).

--- Relacional

SELECT 
	date_part('Year', data_pedido) as ano, 
SUM((pd.quantidade * pd.preco_unitario * (1 - pd.desconto)))::numeric(18,2)  as total_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id
GROUP BY ano

SELECT * FROM pedidos

--- Data Warehouse

SELECT 
	ano, 
	SUM(venda) as total_venda
FROM data_warehouse.fato_vendas fv
INNER JOIN data_warehouse.dim_tempo dt ON dt.id = fv.id_tempo
GROUP BY ano

SELECT * FROM data_warehouse.dim_tempo
SELECT * FROM data_warehouse.fato_vendas

--6. Listar venda por categoria
--- Verificar onde tem a informação de categoria.
--- Calcular o meu total de venda.

--- Relacional

SELECT 
	c.nome as categoria,
	SUM((pd.preco_unitario * pd.quantidade)*(1 - pd.desconto))::numeric(18,2) as total_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id
INNER JOIN produtos pr ON pr.id  = pd.id_produto
INNER JOIN categorias c ON c.id = pr.id_categoria
GROUP BY c.nome
ORDER BY total_venda DESC


--- Data Warehouse

SELECT 
	dp.categoria, 
	SUM(venda) as total_venda
FROM data_warehouse.fato_vendas fv
INNER JOIN data_warehouse.dim_produto dp ON dp.id = fv.id_produto
GROUP BY dp.categoria
ORDER BY total_venda DESC

SELECT * FROM data_warehouse.dim_produto
SELECT * FROM data_warehouse.fato_vendas

--7. Listar venda por produto

--- Relacional

SELECT 
	pr.nome as produto,
	SUM((pd.preco_unitario * pd.quantidade)*(1 - pd.desconto))::numeric(18,2) as total_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id
INNER JOIN produtos pr ON pr.id  = pd.id_produto
GROUP BY pr.nome
ORDER BY total_venda DESC

SELECT * FROM produtos

--- Data Warehouse

SELECT 
	dp.nome, 
	SUM(venda) as total_venda
FROM data_warehouse.fato_vendas fv
INNER JOIN data_warehouse.dim_produto dp ON dp.id = fv.id_produto
GROUP BY dp.nome
ORDER BY total_venda DESC

SELECT * FROM data_warehouse.dim_produto
SELECT * FROM data_warehouse.fato_vendas


--8.Listar venda por país

--Relacional

SELECT 
	p.pais_navio as pais,
	SUM((pd.preco_unitario * pd.quantidade)*(1 - pd.desconto))::numeric(18,2) as total_venda
FROM pedidos p
INNER JOIN pedido_detalhe pd ON pd.id_pedido = p.id
GROUP BY p.pais_navio
ORDER BY total_venda DESC

SELECT * FROM pedidos


--Data Warehouse

SELECT 
	pais, 
	SUM(venda) as total_venda
FROM data_warehouse.fato_vendas fv
INNER JOIN data_warehouse.dim_regiao dr ON dr.id = fv.id_regiao
GROUP BY pais
ORDER BY total_venda DESC


SELECT * FROM data_warehouse.dim_regiao
SELECT * FROM data_warehouse.fato_vendas

SELECT COUNT(venda)::numeric(18,2) as menor_venda
FROM data_warehouse.fato_vendas
```

RELEMBRANDO O JOIN

É a junção de duas informações que estão em tabelas diferentes. Por exemplo, na Tabela Fato de Venda eu tenho a quantidade e a venda, na de Dim_Regiao eu tenho País. Se eu quiser as vendas por País, eu precisaria fazer o Join.

```
SELECT 
	pais, 
	SUM(venda) as total_venda
FROM data_warehouse.fato_vendas fv
INNER JOIN data_warehouse.dim_regiao dr --- Trago o schema e a tabela
ON --- Comando para juntar
dr.id --- A dimensao_tempo (o id)
= --- Outro comando 
fv.id_regiao --- A fato_venda (o id)
GROUP BY pais
ORDER BY total_venda DESC
```

FIZ MEU PRIMEIRO DASH NO POWERBI

![image](https://github.com/user-attachments/assets/6be9cd8a-dd1d-42e1-b61e-f8ed954f19ab)

