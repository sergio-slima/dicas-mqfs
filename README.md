
# Dicas MQFS
![](/src/mqfs.jpg)

##### Projeto de estudo do canal mqFS(Meu Querido Firebird Sql), aprendendo e registrando o apredizado.

![Badge](https://img.shields.io/badge/Blog-Rocketseat-%237159c1?style=for-the-badge&logo=ghost)

### Tabela de conteúdos
=================
<!--ts-->
   * [Pesquisar texto sql mais eficiente](#Pesquisar-texto-sql-mais-eficiente)
   * [Tabela de Conteudo](#tabela-de-conteudo)
   * [Instalação](#instalacao)
   * [Como usar](#como-usar)
      * [Pre Requisitos](#pre-requisitos)
      * [Local files](#local-files)
      * [Remote files](#remote-files)
      * [Multiple files](#multiple-files)
      * [Combo](#combo)
   * [Tests](#testes)
   * [Tecnologias](#tecnologias)
<!--te-->

<h4 align="center"> 
	🚧  Dicas MqFS 🚀 Em construção...  🚧
</h4>

### Pesquisar texto sql mais eficiente

    ```
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
    ```

- **Jeito certo para arredondar valores**

    *Precisa globalizar um cast dentro da operação*
    ```
    select
        cast(
            cast(5 as numeric (15,5)) / 
            cast (30 as numeric (15,5))
        as numeric(15,2))
    from table
    ```

- **Explorando Order By**

    *Deixando registro com campo nulo pra baixo ou dois campos ou por posição do campo no sql*
    ```
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
    ```
