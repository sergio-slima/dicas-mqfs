
<div align="center"> 
	<h1>Dicas</h1>
	<img src='/src/mqfs.jpg' />
	<h5>Projeto de estudo do canal mqFS(Meu Querido Firebird Sql), estudando e registrando o apredizado.</h5>
</div>	

<h6 align="center"> 
	🚧  Dicas MqFS 🚀 Em andamento...  🚧
</h6>

[![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg)](https://github.com/Naereen/StrapDown.js/blob/master/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/contribuition-welcome-brightgreen.svg)](http://makeapullrequest.com)

### Tabela de conteúdos
=================
<!--ts-->
   * [Pesquisar texto sql mais eficiente](#Pesquisar-texto-sql-mais-eficiente)
   * [Jeito certo para arredondar valores](#Jeito-certo-para-arredondar-valores)
   * [Explorando Order By](#Explorando-Order-By)
   * [Concatenar com nulo](#Concatenar-com-nulo)   
   * [Char Varchar](#Char-Varchar)
   * [Trabalhar Data Hora](#Trabalhar-Data-Hora)
   * [Conta Registros SQL](#Conta-Registros-SQL)
   * [Substring SQL](#Substring-SQL)
   * [Autor](#Autor)
<!--te-->

### Pesquisar texto sql mais eficiente

    Antes:
        
        select 
            codigo, 
            nome 
        from clientes 
        where upper(nome) like '%carlos%';
    
    Depois: 
    
        select 
            codigo, 
            nome 
        from clientes 
        where nome containing 'carlos';


### Jeito certo para arredondar valores

    // Precisa globalizar um cast dentro da operação
 
    select
        cast(
            cast(5 as numeric (15,5)) / 
            cast (30 as numeric (15,5))
        as numeric(15,2))
    from table
   

### Explorando Order By

    // Deixando registro com campo nulo pra baixo ou dois campos ou por posição do campo no sql
   
    select
        id,
        nome,
        nome2
    from table
    order by nome nulls last
    ou
    order by nome nulls last, nome2
    ou
    order by 2
  
### Concatenar com nulo

    // Modo correto de concatenar campos com valor nulo, usando "coalesce(field,'')"

    select
        'Código: ' || n.id || ' - ' ||
        'Posição: ' || coalesce(n.posicao, 999) || ' - ' ||
        'Menino: ' || coalesce(n.menino, 'Vazio') || ' - ' ||
        'Menina: ' || coalesce(n.menina, 'Vazio') 
        as "NOMES"
    from nome n

### Char Varchar

    // Campos Char utiliza todo seu valor, diferente do varchar que usa só o conteudo

    select
        '"' || 'Sergio' as varchar(100) || '"'    
    from exemplo

    Result: "Sergio"

    select
        '"' || 'Sergio' as char(100) || '"'    
    from exemplo

    Result: "Sergio                       "

### Trabalhar Data Hora

    // Resultado de Data e hora no Sql

    select
        current_date,
        current_time,
        current_timestamp
    from table   

### Conta Registros SQL

    // Listar somente registros com repetição na contagem

    select
        n.menino,
        count(n.id)
    from nome n
    group by n.menino
    having count(n.id) > 1  

### Substring SQL

    // copiar string com Sql
    select
        n.menino,
        substring(n.menino from 1 for 3),   //pega três primeiro caractere
        substring(n.menimo from 4),         //pega partir do quarto pro ultimo caractere
        right(n.menino, 3)                  //pega os três ultimos caractere
    
    
### Autor

<a href="https://app.rocketseat.com.br/me/sergio-silva-lima-1567192156">
 <img style="border-radius: 50%;" src="https://avatars1.githubusercontent.com/u/48762187?v=4" width="100px;" alt="Sergio SLima"/>
 <br />
 <sub><b>Sergio Silva Lima</b></sub></a> <a href="https://app.rocketseat.com.br/me/sergio-silva-lima-1567192156" title="Rocketseat">🚀
</a>

Desenvolvido por:
Sergio SLima 👋🏽
Entre em contato!

[![Github Badge](https://img.shields.io/badge/-Github-000?style=flat-square&logo=Github&logoColor=white&link=https://github.com/fagnerpsantos)](https://github.com/sergio-slima)
[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/fagnerpsantos/)](https://www.linkedin.com/in/sergio-silva-lima-b99237140/)
[![Instagram Badge](https://img.shields.io/badge/-Instagram-red?style=flat-square&labelColor=red&logo=instagram&logoColor=white&link=https://www.instagram.com/sergio_silva_/)](https://www.instagram.com/sergio_silva_/)
    
