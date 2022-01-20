# Magicbell GraphQL Back End Demo

This project uses [Hasura](https://hasura.io) to expose a [Postgresql](https://www.postgresql.org/) database.

Due to IP constraints, all database metadata has been removed from this project and will need to be rebuilt via the Hasura Console.

## Running This Project

A) Spin up Magicbell locally for development.

B) To run this project:

1. Setup [Docker Desktop](https://www.docker.com/products/docker-desktop)
2. Run:

   ```bash
   # install dependencies
   cd projects; yarn install

   # see docker-compose.yml
   yarn docker:up

   # apply hasura metadeta: see package.json for details
   yarn dev:create
   ```

3. Using the admin-secret `dummypassword` to login, navigate to [http://localhost:8087/console](http://localhost:8087/console). Note: see `./projects/.env.local` for admin-secret `HASURA_GRAPHQL_ADMIN_SECRET` and console port `HASURA_PORT_EXPOSED`.

   - add a header: `x-hasura-user-id` with value `admin`

## Development

### Resetting Environment

Reset your environment by running the following `docker` commands:

```bash
# WARNING: This will restart everything and you will LOSE ANY CHANGES made in
# the hasura console if you haven't run yarn hasura:export first.

# docker ps -a
# docker images
# docker volume ls
yarn dev:destroy-everything

# spin up docker again
yarn docker:up

# apply hasura metadeta and sql migration: see package.json for details
yarn dev:create
```

### Core Technologies Used

- [Graphql](https://graphql.org/)
- [Hasura](https://hasura.io)
- [Postgresql](https://www.postgresql.org/)
