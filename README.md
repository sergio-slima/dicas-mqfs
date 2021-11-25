
<div align="center"> 
	<h1>Dicas</h1>
	<img src='/src/mqfs.jpg' />
	<h5>Projeto de estudo do canal mqFS(Meu Querido Firebird Sql), estudando e registrando o apredizado.</h5>
</div>	

<h6 align="center"> 
	🚧  Dicas MqFS 🚀 Em andamento...  🚧
</h6>

### Tabela de conteúdos
=================
<!--ts-->
   * [Pesquisar texto sql mais eficiente](#Pesquisar-texto-sql-mais-eficiente)
   * [Jeito certo para arredondar valores](#Jeito-certo-para-arredondar-valores)
   * [Explorando Order By](#Explorando-Order-By)
   * [Concatenar com nulo](#Concatenar-com-nulo)
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