# Containerization

Uni-verse was built using containers.

Containers allow for a reproducible, controlable, isolated runtime for our applications.

It also allows granularity in how we manage our apps' components, making it easy to add load-balancers in the equation.

## For development

Installing mongodb, ES, RabbitMQ and whatnot on a machine would cost time and possibly make the machine less operational if it has too many processes.
Having containers for development allows turning on uni-verse as a whole whenever we need to, and turning it off when we're done.

It makes the development environment distro-independant, allowing any-one coding to use the toolchain they like.

To make development easier and quicker, containers for the frontend and the backend have mounts with the host machine, defined in the [dev environment's docker-compose](https://github.com/uni-verse-fm/uni-verse-dev).

They are ran using `watch` features, allowing any change in the code to be immediately applied.

## For production

Production environments have different needs compared to development:

The images need to be weight less, turn up faster, take less resources.

This is why dockerfiles for the development and for the production must not be the same.

Our production dockerfiles for the [frontend](https://github.com/uni-verse-fm/uni-verse-frontend/blob/main/Dockerfile) and for the [backend](https://github.com/uni-verse-fm/uni-verse-api/blob/main/Dockerfile) are using alpine versions of node's image, and multistage in order to strip any un-needed dependency from the container that will be sent to production.

Not only does that reduce the attack surface, it mainly just create lighter final images.

For uni-verse's production, writing this, the frontend image is 152MB and the backend image is 264MB, while they are based on the 151MB node:22-alpine image.

Note that this is the global, uncompressed size given by `docker images`.

To finish with, our docker images are stored in a private container registry, from which productions servers can pull images anytime.
