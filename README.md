# plsql-guide
plsq guide for developers

# Operations with negative values

Be careful! To make operations with negative values we need use the abs function.

-- FILEPATH: Untitled-1
-- BEGIN: ed8c6549bwf9
select (-500 + 1000) - abs(-1000) from dual;
-- END: ed8c6549bwf9
