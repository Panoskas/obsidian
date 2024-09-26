## Connect as postgres user
- `sudo -i -u postgres  `
- `psql`

### Commands
- show databases
`\l`

- connect to database
`\c <database>`

- list all databases after you connect
`\dt`

- run a docker container with postgres
```bash
docker run --name smart_metering -p 5433:5432 -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -d postgres
```

- connect to docker container
```bash
docker exec -it <container_id> bash
psql -U postgres
```

- restore database that is running in a container (Windows)
```sql
cat your_dump.sql | docker exec -i your-db-container psql -U postgres -d <name_of_database>
```