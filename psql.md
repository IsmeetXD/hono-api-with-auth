# PostgreSQL Terminal (`psql`) Cheatsheet

## Connecting to a Database
To connect to a PostgreSQL database using `psql`, use the following syntax from your normal terminal:

```bash
psql -h <host> -p <port> -U <username> -d <database_name>
```

**Example (connecting to your local setup from `.env`):**
```bash
psql -h localhost -p 5433 -U postgres -d hono_api
```
*(It will prompt you for the password, which is `postgres`)*

---

## Important Docker Command
If you are running PostgreSQL inside Docker (like in this project) and don't have `psql` installed on your host machine, you can run `psql` directly inside the container:

```bash
docker exec -it <container_name_or_id> psql -U postgres -d hono_api
```
*(To find the container name, run `docker ps`)*

---

## General `psql` Commands
Once you are inside the `psql` interactive prompt (your terminal will look like `hono_api=#`), you can use these slash (`\`) commands:

- `\q` : Quit `psql` and return to the terminal.
- `\c <database_name>` : Connect to a different database.
- `\l` : List all databases on the server.
- `\dt` : List all tables in the current connected database.
- `\d <table_name>` : Show the schema and details of a specific table.
- `\dn` : List all schemas.
- `\du` : List all database roles and users.
- `\x` : Toggle expanded display formatting (turns rows into a vertical list, useful for reading large rows).
- `\?` : Show help for `psql` slash commands.
- `\h <SQL command>` : Show help for a specific SQL command (e.g., `\h SELECT`).

---

## Executing SQL Queries
You can run any standard SQL query directly in the `psql` prompt. 
**Important: Remember to end every SQL statement with a semicolon (`;`).**

```sql
-- View all data in the books table
SELECT * FROM books;

-- View specific columns
SELECT title, "pageCount" FROM books;

-- Insert a new row
INSERT INTO authors (name, birthday) VALUES ('John Doe', '1990-01-01');

-- Delete a row
DELETE FROM authors WHERE id = 1;
```

---

## Running a SQL Script File
If you have a file containing SQL commands (e.g., `seed.sql`), you can execute it without entering the interactive prompt:

```bash
psql -h localhost -U postgres -d hono_api -f path/to/your/file.sql
```
