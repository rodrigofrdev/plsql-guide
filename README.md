# plsql-guide
plsq guide for developers

# Operations with negative values

Be careful! To make operations with negative values we need use the abs function.

``` sql
select (-500 + 1000) - abs(-1000) from dual;
```

# Arrays need to be extended

``` sql
select valor into v_billing_type_names(i) -- Unextended arrays. This causes the error beyond the subscript.
from HsPropostaFinanListaValores
where chave = v_billing_types(i)
  and tipo = 'TIPO_DE_FATURAMENTO'
  and ativo = 'S';
```

``` sql
select valor into v_billing_type_name
from HsPropostaFinanListaValores
where chave = v_billing_types(i)
  and tipo = 'TIPO_DE_FATURAMENTO'
  and ativo = 'S';
v_billing_type_names.extend; -- Correct line
v_billing_type_names(i) := v_billing_type_name;
```
# Aggregate functions

When you use a aggregate function always return a value. So, you do not need check no_data_found exception.
Be careful! Check if your logic return the expected value. In the below sample, nvl was added for get 1 for null values returned.
```sql
select nvl(max(item_de_provisao), 0) + 1 into v_next_provision_item
from HsPropostaFinanceiraParcelas 
  inner join HsPropostasFinanceiras 
    on HsPropostaFinanceiraParcelas.proposta_id = HsPropostasFinanceiras.id 
where conta_agrupada_id = p_economic_group_id;
```
