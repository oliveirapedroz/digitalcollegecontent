# Histórico de aulas e do meu desenvolvimento no curso de Data Analytics da Digital College
## 🫣 AULA 1 - 27/07/2024
Testando a ferramenta na minha primeira aula do curso de Data Analytics. Tendo em vista que não conheço muita coisa da área de dados, estou com dificuldades em entender alguns termos - o que é normal. No entanto, a professora vem da minha área de atuação (Setor de Gestão de Pessoas), então isso além de me tranquilizar, me deixou animado para aprender mais sobre como convergir essas duas aulas.
## 🤔 AULA 2 - 03/08/2024
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

