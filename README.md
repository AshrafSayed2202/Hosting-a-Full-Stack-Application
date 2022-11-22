# Hosting a Full-Stack Application

## Getting Started

1. Clone this repo locally into the location of your choice.
1. Move the content of the udagram folder at the root of the repository as this will become the main content of the project.
1. Open a terminal and navigate to the root of the repo
1. follow the instructions in the installation step

The project can run but is missing some information to connect to the database and storage service. These will be setup during the course of the project

### Dependencies
A list of project dependencies can be found [here](docs/dependencies.md).

### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres.
2. In AWS, provision a s3 bucket for hosting the uploaded files.
3. Export the ENV variables needed or use a package like [dotnev](https://www.npmjs.com/package/dotenv).
- connect to the default postgres databage as the server's root user `psgl -U postgres`
- In psql run the following to create a user
    - `CREATE USER test_user WITH PASSWORD 'test_user';`
- In psql run the following to create the database
    - `CREATE DATABASE store WITH OWNER test_user;`
- Connect to the database and grant all privileges
    - Grant for dev database
        - `\c store test_user` then enter the password 'test_user'
        - `GRANT ALL PRIVILEGES ON DATABASE udagram TO test_user;`
### Create  `.env` file in `udagram/udagram-api` directory with the following vars
```
POSTGRES_HOST=localhost
DB_PORT=5432
PORT=8080
POSTGRES_USERNAME=test_user
POSTGRES_PASSWORD=test_user
POSTGRES_DB=udagram
JWT_SECRET=IreliaTop
URL=http://localhost
AWS_BUCKET=""
AWS_REGION=""
AWS_PROFILE=""
AWS_ACCESS_KEY_ID=""
AWS_SECRET_ACCESS_KEY=""
```
4. From the root of the repo, navigate udagram-api folder `cd udagram/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
5. Without closing the terminal in step 4, navigate to the udagram-frontend `cd udagram/udagram-frontend` to install the node_modules `npm install -f`. After installation is done start the api in dev mode with `npm run start`.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd udagram/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End-to-End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework
