---
title: PostgreSQL
---

# PostgreSQL

## Config Files
- general config (Ubuntu): `/etc/postgresql/10/main/postgresql.conf`
- general config (Archlinux): `/var/lib/postgres/data/postgresql.conf`
  - to allow access from everywhere: `listen_addresses = '*'`
- who can access what from where and how (Ubuntu):
  `/etc/postgresql/10/main/pg_hba.conf`
- who can access what from where and how:
  (archlinux)`/var/lib/postgres/data/pg_hba.conf`
  - example: `host <database> <user> 0.0.0.0/0 md5`
  - example: `hostssl <database> <user> 0.0.0.0/0 md5`

## Commands (prompt)
- change the user from root to postgres: `su -l postgres`
- init the db: `initdb --locale=en_US.UTF-8 -E UTF8 -D
  /var/lib/postgres/data`
- enter db tool psql: `psql`
- create user: `createuser --interactive`
- create database
  - `createdb <db_name>`
  - create and set owner: `createdb <db_name> -O <role_name>`
- restart the db: `systemctl restart postgresql.service`

## Commands (psql)
- connect: `psql -h <host_or_ip> -p <port> -d <database> -U <username>`
- set password: `\password <role_name>`
- list user (roles): `\du`
- list user (roles) with passwords to check if they are set: `select *
  from pg_shadow;`
- list databases: `\l`
- detele db: `DROP DATABASE <db_name>;`
- delete role: `DROP ROLE <role_name>;`

## Create User / Database
- `CREATE USER <username> WITH PASSWORD '<password>';` - https://www.postgresql.org/docs/8.0/sql-createuser.html
- `CREATE DATABASE <db_name> OWNER <username>;` - https://www.postgresql.org/docs/9.0/sql-createdatabase.html

## Links
- alter databases:
  <https://www.postgresql.org/docs/10/sql-alterdatabase.html>
- backup:
  <https://www.linode.com/docs/databases/postgresql/how-to-back-up-your-postgresql-database/>
