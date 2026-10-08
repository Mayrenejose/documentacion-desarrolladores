# Consultas útiles

### Buscar por texto
- SELECT OWNER,
       NAME,
       TYPE,
       LINE,
       TEXT
FROM ALL_SOURCE
WHERE UPPER(TEXT) LIKE '%RESCATA_RETIROS_CONSULTA_CAI%'
ORDER BY OWNER, NAME, TYPE, LINE;

### Conocer llaves de tabla
P → Primary Key
U → Unique
R → Foreign Key
C → Check constraint

-  SELECT constraint_name,
       constraint_type,
       status
FROM ALL_CONSTRAINTS
WHERE owner = 'NEWAFP'
  AND table_name = 'WEB_BLOQUEO_CLAVE';

### Conocer quien tiene la primary key
-  SELECT constraint_name,
       column_name,
       position
FROM ALL_CONS_COLUMNS
WHERE owner = 'NEWAFP'
  AND table_name = 'WEB_BLOQUEO_CLAVE'
  AND constraint_name = 'WEB_BLOQUEO_CLAVE_PK'
ORDER BY position;

### Conocer restricciones
- SELECT constraint_name,
       search_condition
FROM ALL_CONSTRAINTS
WHERE owner = 'NEWAFP'
  AND table_name = 'WEB_BLOQUEO_CLAVE'
  AND constraint_type = 'C';

### Conocer valores por defecto de las columnas 
- SELECT column_name,
       data_default
FROM ALL_TAB_COLUMNS
WHERE owner = 'NEWAFP'
  AND table_name = 'WEB_BLOQUEO_CLAVE'
ORDER BY column_id;