# plsql-guide
plsq guide for developers

# Operations with negative values

Be careful! To make operations with negative values we need use the abs function.

``` sql
select (-500 + 1000) - abs(-1000) from dual;
```

# Arrays need to be extended

``` sql
select valor into v_billing_type_name
from HsPropostaFinanListaValores
where chave = v_billing_types(i)
  and tipo = 'TIPO_DE_FATURAMENTO'
  and ativo = 'S';
v_billing_type_names.extend; -- Correct line
v_billing_type_names(i) := v_billing_type_name;
```
