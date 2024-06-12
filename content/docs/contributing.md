# Contributing

## Setting up the environment

Although docker-compose simplifies the reproduction of this app's environment, it does not do everything for you.
Some environment variables are needed by the app so that the production version does not spill out all of our precious secrets!

Our development environment for the API and the frontend is available in [another repo](https://github.com/uni-verse-fm/uni-verse-dev).

In this repository, you can find a `docker-compose.yml` and a `docker.env` file.

How to use all that is simple :

```bash
# Clone the repository with submodules (this one and the frontend)
git clone --recurse-submodules git@github.com:uni-verse-fm/uni-verse-dev.git

docker compose up

```
