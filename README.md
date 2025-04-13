## Launching the container 

```bash
docker-compose up
```

### TODO on every geometry column 
```sql
ALTER TABLE features
ALTER COLUMN geometry TYPE geometry(Geometry,4326)
USING ST_SetSRID(geometry,4326);
```
### and then unforce the columns to be exactly 4326 as srid
```sql
ALTER TABLE features
ADD CONSTRAINT enforce_geometry_srid_4326
CHECK (ST_SRID(geometry) = 4326);
```
that enforce SRID to be 4326 so we can call postgis function without being worried the srid not
matching
