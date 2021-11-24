# Dicas MQFS

### 🚩 Pesquisar texto sql mais eficiente

Antes: select codigo, nome from clientes where upper(nome) like '%carlos%';

Depois: select codigo, nome from clientes where nome containing 'carlos';

### 🚩 Jeito certo para arredondar valores

    // Precisa globalizar um cast dentro da operação
    select
        cast(
            cast(5 as numeric (15,5)) / cast (30 as numeric (15,5))
        as numeric(15,2))
    from table
