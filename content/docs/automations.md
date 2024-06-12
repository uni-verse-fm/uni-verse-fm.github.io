# Automations

Uni-verse runs via lots of automations, powered by github-action.

The whole project includes more than a dozen of jobs, performing checks, builds, and deployments.

## Api

### [ci](https://github.com/uni-verse-fm/uni-verse-api/blob/main/.github/workflows/ci.yml)

Runs on pull requests and prevent any push if it does not pass.

Its role is to ensure a clean codebase and avoid regressions as much as possible.

- Check best practices via eslint
- Check formatting via prettier
- Runs unit tests

### [build](https://github.com/uni-verse-fm/uni-verse-api/blob/main/.github/workflows/build.yml)

Ensures that the container image made from the project builds.
In the meantime, it makes sure the project itself builds.

It is meant to run during PRs, just as the previous one, to avoid regressions and make sure that a release would not fail because of this PR.

- Builds an OCI compliant image from [Dockerfile](https://github.com/uni-verse-fm/uni-verse-api/blob/main/Dockerfile) via Docker.

### [release](https://github.com/uni-verse-fm/uni-verse-api/blob/main/.github/workflows/release.yml)

Builds and pushes an OCI compliant image to our private docker image registry (Hosted on Vultr).
Triggered when a new Github release is created (`gh release create 1.2.3`).

This docker image can then be pulled by production anytime for it to be updated.

- Builds an OCI compliant image from [Dockerfile](https://github.com/uni-verse-fm/uni-verse-api/blob/main/Dockerfile) via Docker.
- Tags the image with the name uni-verse-api:latest and uni-verse-api:x.x.x

## Frontend

The frontend almost has exactly the same workflows as the API.
It only adds e2e tests and type checks.

### [ci](https://github.com/uni-verse-fm/uni-verse-frontend/blob/main/.github/workflows/ci.yml)

Runs on pull requests and prevent any push if it does not pass.

Its role is to ensure a clean codebase and avoid regressions as much as possible.

- Check best practices via eslint
- Check formatting via prettier
- Runs unit tests and e2e
- Runs type checks

### [build](https://github.com/uni-verse-fm/uni-verse-frontend/blob/main/.github/workflows/build.yml)

Ensures that the container image made from the project builds.
In the meantime, it makes sure the project itself builds.

It is meant to run during PRs, just as the previous one, to avoid regressions and make sure that a release would not fail because of this PR.

- Builds an OCI compliant image from [Dockerfile](https://github.com/uni-verse-fm/uni-verse-frontend/blob/main/Dockerfile) via Docker.

### [release](https://github.com/uni-verse-fm/uni-verse-frontend/blob/main/.github/workflows/release.yml)

Builds and pushes an OCI compliant image to our private docker image registry (Hosted on Vultr).
Triggered when a new Github release is created (`gh release create 1.2.3`).

This docker image can then be pulled by production anytime for it to be updated.

- Builds an OCI compliant image from [Dockerfile](https://github.com/uni-verse-fm/uni-verse-api/blob/main/Dockerfile) via Docker.
- Tags the image with the name uni-verse-api:latest and uni-verse-api:x.x.x

## Android app

The android app follows the frontend and the API in its automation structure:

### [build](https://github.com/uni-verse-fm/uni-verse-app/blob/main/.github/workflows/build.yml)

Builds the APK of the app, detecting any issue preventing build before it can be merged

- Builds the app into an APK

### [ci](https://github.com/uni-verse-fm/uni-verse-app/blob/main/.github/workflows/ci.yml)

Runs on pull requests and prevent any push if it does not pass.

Its role is to ensure a clean codebase and avoid regressions as much as possible.

- Check best practices via eslint
- Check formatting via prettier

### [release](https://github.com/uni-verse-fm/uni-verse-app/blob/main/.github/workflows/release.yml)

Runs on Github releases to build the app

- Builds the app's APK
- Exports the APK in the release artifacts

## Wiki

### [hugo](https://github.com/uni-verse-fm/uni-verse-fm.github.io/blob/main/.github/workflows/hugo.yaml)

Builds the wiki and pushes it to production.

- Uses hugo to build a static website from these files
- Pushes the built website to GH pages to update production
