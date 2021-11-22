# Dicas MQFS

### 🚩 Pesquisar texto sql mais eficiente

Antes: select codigo, nome from clientes where upper(nome) like '%carlos%';

Depois: select codigo, nome from clientes where nome containing 'carlos';
