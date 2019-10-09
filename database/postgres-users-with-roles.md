# Postgres Users With Roles

I have been doing this for a while but still wanted to document
for my own future reference after doing it couple of times.

### Create readonly role

```sql
CREATE ROLE readonly;
GRANT CONNECT ON DATABASE <DB_NAME> TO readonly;
GRANT USAGE ON SCHEMA public TO readonly;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON TABLES TO readonly;
```

### Create readwrite role

```sql
CREATE ROLE readwrite;
GRANT CONNECT ON DATABASE <DB_NAME> TO readwrite;
GRANT USAGE ON SCHEMA public TO readwrite;
GRANT USAGE, CREATE ON SCHEMA public TO readwrite;
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO readwrite;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO readwrite;
GRANT USAGE ON ALL SEQUENCES IN SCHEMA public TO readwrite;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT USAGE ON SEQUENCES TO readwrite;
```

Replace `public` schema with whatever you need to

### Create users

```sql
CREATE USER myuser1 WITH PASSWORD 'secret_passwd';
GRANT readonly TO myuser1;
```
