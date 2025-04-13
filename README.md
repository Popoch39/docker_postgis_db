## Launching the container 

```bash
docker-compose up
```

### TODO on every geometry column 
```sql
ALTER TABLE table_name
ALTER COLUMN column_name TYPE geometry(Geometry,4326)
USING ST_SetSRID(column_name,4326);
```
### and then unforce the columns to be exactly 4326 as srid
```sql
ALTER TABLE table_name
ADD CONSTRAINT enforce_geometry_srid_4326
CHECK (ST_SRID(column_name) = 4326);
```
that enforce SRID to be 4326 so we can call postgis function without being worried the srid not
matching
