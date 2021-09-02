# Save & Return Lookup UI Service
Provides a service layer to talk to a database to view records on a SQL table using the npm module knex.

**Reading:**  This service will connect to a SQL database, get the data back off a single table and show in the UI entries for a single table. Currently these can be accessed using either a save and return session ID or email.

## Env Vars
You can set the following to specific how you want your results to look:
- `SERVICE_TYPE` - This specifies what service you are using the lookup UI for. The default is for the modern slavery service. But additional templates could be created which this drives.
- `TABLE_NAME` - This specifies the SQL table name you want to query. This defaults to 'reports'.
- `CLIENT` - This is the database client type. This defaults to postgresql.
- `DB_HOST`,`DB_USER`,`DB_PASS`,`DB_NAME` - These are production credentials for accessing the relevant database. These default to 'knex' for the user and password, and 'knex_session' for the database name. These are only for local development.

## Local Setup
The migrations and seeds folders are used by knex to setup a local DB with dummy information for testing the service. These are not used in production where it is assumed a separate DB is setup for knex to connect to that is already setup.

Run the following commands to setup a test DB:
```
brew install postgres
brew services start postgresql
psql postgres
CREATE ROLE knex WITH LOGIN PASSWORD 'knex';
ALTER ROLE knex WITH SUPERUSER;
CREATE DATABASE knex_session;
\q
yarn run db:setup
```
If you download Postico for Mac (https://eggerapps.at/postico/), you can then inspect your postgres DB for example and look at the test entries inserted into the test table 'Reports'.

## Install & Run <a name="install-and-run"></a>
The application can be run on your local machine

### Dependencies <a name="dependencies"></a>
You will need to have the following installed:

[Node JS](https://nodejs.org/en/download/releases/) ( LTS Erbium v14.x )

[npm](https://www.npmjs.com/get-npm) ( v6.x )

[PostgreSQL](https://www.postgresql.org/download/) ( v12.x )

## Running the application

Ensure your database service is available and running.

Then to run the service use:

 ```npm start``` to run the server.

With the server running you can run the main app with save and return lookup UI functionality.
See details of how to do this in [modern slavery](https://github.com/UKHomeOffice/modern-slavery) application
