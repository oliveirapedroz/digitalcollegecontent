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
