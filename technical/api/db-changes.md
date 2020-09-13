# Migrating database changes

The API uses the popular NodeJS ORM called Sequalize to manage it's models and corresponding SQL queries (using either MariaDB or MySql). When first installing the tables can be created and seeded by running:

```
node reset.js
```

This command will reset the tables, so don't run on an existing installation.

Af the databases are created every now and then database changes are necessary, these are run through the migrations.

The following command will run the migrations, this should be run

```
node migrate.js
```

Migrations are found in the /migrations folder in the root. Order is managed by adding a number to it.

When creating a database everyting is generated from the Sequalize model definition. All existing migrations are set to done, so it won't collide with future migrations. Best practice is to write migrations that allow for a table or column to already exists, but mysql doesn't alway make that easy.

```
node reset.js
```

This means that if migrations and the model differ slightly a new database and migrated database is not always the (exactly) same.

In a production setup alway run node migrate.js before deploymen. The Openstad Kubernetes setup takes care of this.