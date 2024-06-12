# API

Uni-verse's API is its central component, being a gateway to every other micro-services in Uni-Verse's architecture.
It interacts with :

- Stripe
- Minio
- Elastic Search
- RabbitMQ
- MongoDB

This API is meant to be hosted at [this address](https://uni-verse.api.vagahbond.com), and its auto-generated OpenAPI compliant documentation is [available here](https://uni-verse.api.vagahbond.com/docs).

## About the tech

### Typescript

The whole project is coded in typescript and ran in NodeJS, for the versatility and ease of development (let's not forget this is a POC and not a commercial product)

### NestJS

This Nest was the framework of choice for a few different reasons:

- The architecture is well defined and future-proof, which is important for such a big project.
- It allows a fait amount of scalability for the app, with extensive documentation on how to actually scale.

### Swagger

Thanks to [Swagger](https://swagger.io/docs/), we could auto-generate a documentation for this web API and save a good amount of time while being compliant to OpenAPI specifications. That documentation also has the advantage to be interactive.

![](doc/assets/swagger.png)

### Mongoose

Uni-verse relies on Mongo DB with [Mongoose](https://mongoosejs.com/) ORM for persistence. Although it might not perform as well as a relational database for most usecases, it allowed us to get a POC working faster.

### Docker

Uni-verse's architecture is complex and has numerous components. To get a development environment working easily, we rely on [docker](https://www.docker.com/) with docker-compose. This also alows setting up the production pretty easily using docker swarm, in case of a pre-production environment, or a demo for instance.

Using docker, it's trivial to deploy images for this API on registers via CI and then pull them when needed.

### ESLint et Prettier

This API is made to be a demonstration of good software craftmanship. In this endeavour, we made use of [Eslint](https://eslint.org/) and [Prettier](https://prettier.io/) to check and enforce good practices across the codebase.

Lint and formatting checks are performed on any PR before they can be merged to the main branch.

### Github Actions

As mentioned before, CI/CD plays an inportant role in this project. This is where Github Actions shines.
We leverage GH Actions on different aspects of the project:

1. Enforce best practices via Prettier and ESLint checking on each PR (no one can push to `master`)
2. Run unit and integration tests on each PR
3. Build and push the Docker images to our registries.

### Winston + Filebeat

This APi's logs are written in a file that's shared with Kibana using Filebeat so that they can be thoroughly analyzed if ever needed.
This allows having a dashboard with a good overview on what's going on in the app.


