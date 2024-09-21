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




