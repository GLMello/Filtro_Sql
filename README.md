<h1> Aplicando filtros às consultas SQL</h1>

 ### You can also read this in: [English](https://github.com/GLMello/Sql_Filtering)

<h2>Descrição</h2>
Este projeto consiste em utilizar filtros SQL (Queries) para investigar potenciais riscos de segurança em diferentes áreas. Ao longo deste projeto, farei uso de diferentes filtros e operadores para obter as informações necessárias para iniciar a mitigação de riscos.
<br />


<h2>Cenário</h2>
Você é um profissional de segurança em uma grande organização. Parte do seu trabalho é investigar ocorrências de segurança para ajudar a manter o sistema seguro. Recentemente, você descobriu alguns problemas em potencial relacionados a tentativas de login e aos computadores de funcionários.

Sua tarefa é examinar os dados da organização nas tables de funcionários (Employees) e tentativas de login (log in attempts). Você precisará usar filtros SQL para recuperar registros de diferentes bancos de dados e investigar os potenciais problemas de segurança.


<h2>Walkthrough</h2>

<p align="left">
  
**Task 1:** <br/>
_Você descobriu recentemente um possível incidente de segurança que ocorreu após o horário comercial. Para investiga-lo, você precisa consultar a tabela log_in_attempts e avaliar os logins após o horário de trabalho. Use filtros em SQL para criar um query que identifique todas as tentativas de login não sucedidas que ocorreram após as 18:00._ <br/><br/>

Para obter apenas as tentativas de login não sucedidas que ocorreram após as 18:00, utilizei o seguinte comando:<br/><br/>
``
SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = '0';
``
<br/><br />
Ao usar o operador "and", fui capaz de estabelecer as duas restrições de uma vez só e encontrei o seguinte:
<br/><br />
<img src="https://i.imgur.com/fc6lFqw.png" height="55%" width="55%" alt="Logins depois do horário"/>
<br /><br />

**Tarefa 2**:<br/>
_Um evento suspeito ocorreu em 2022-05-09. Para investigar esse evento, você deseja avaliar todas as tentativas de login que ocorreram nesse dia e no dia anterior. Use filtros em SQL para criar um query que identifique todas as tentativas de login que ocorreram em 2022-05-09 ou 2022-05-08._
<br/><br/>
Aqui, eu usei:<br/><br/>
``
SELECT * FROM log_in_attempts WHERE login_date = '2022-05-09' or login_date = '2022-05-08';``<br/> <br/>
Com o operador "or", eu restringi o query para os dois dias desejados:
<br/><br/>
<img src="https://i.imgur.com/tD5lA3T.png" height="55%" width="55%" alt="Between date"/>
<br /><br />
**Tarefa 3**:<br/>
_Houve uma atividade suspeita de tentativas de login, mas o time conseguiu estabelecer que essa atividade não se originou no México. Agora, você precisa investigar as tentativas de login que ocorreram fora do México. Use filtros em SQL para criar um query que identifique todas as tentativas de login que ocorreram fora do México._ <br/><br />

Nessa tarefa eu consultei buscas anteriores para notar como o México teria sido inserido na tabela. Descobri que tanto MEXICO como MEX eram utilizados na tabela. Esse fato me levou a utilizar um wildcard para complementar a filtragem. Eu então, utilizei o comando:
 <br/>

``SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';``<br/> <br/>
Utilizar o wildcard "%" me permitiu excluir tanto MEX quando MEXICo da busca. Eu então fiquei com:<br/><br/>
<img src="https://i.imgur.com/Qtxknw7.png" height="55%" width="55%" alt="Not Mexico"/>
<br /><br />
**Tarefa 4**:<br/>
_Sua equipe deseja realizar manutenções de segurança em computadores de funcionários específicamente no departamento de Marketing. Você é responsável por obter informações sobre esses computadores e precisará consultar a tabela de funcionários. Use filtros em SQL para criar um query que identifique todos os funcionários no departamento de Marketing para todos os escritórios no prédio leste._
<br /><br />
Mais uma vez me deparei com vários inputs desejados, já que existem multiplas oficinas no prédio Leste. Isso, novamente, pede pelo uso de um wild card junto da mudança de tabelas para pesquisa, levando ao comando:

``
SELECT * FROM Employees WHERE department = 'marketing' AND office LIKE 'east%';``<br/> <br/>

Fui deixado então com o query desejado o qual incluiu todos os empregados de marketing de oficinas no prédio Leste.<br/><br/>
<img src="https://i.imgur.com/gNwfTwJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<h2>Nota</h2>

 Esse projeto é parte do curso [Google Cybersecurity Professional Certificate.](https://www.coursera.org/professional-certificates/google-cybersecurity)<br />
