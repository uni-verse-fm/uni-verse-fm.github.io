# Production

Uni-verse is meant to be readily scalable, in prevision of a massive userbase growth.

For this reason, it uses industry-standard Production means, with OCI container images.

Those images are meant to be as light as possible (notably thanks to multi-stage docker builds) and deployed in a streamlined workflow.

Having every component containerized allows deploying them easily in any environment, whether it is an auto-scale expensive cloud, or an on-premise architecture with kubernetes or similar.

A [nix](https://nixos.org/) flake is also available, and pulls our home built docker images in OCI containers, to run them in Podman. Modifications are on their way to have a proper systemd-powered NixOS module enabling a server to run a replica of Uni-Verse in just a few commands.
Along with it, there will be a totally reproducible development environment enabled by `nix develop` and a single container running the whole architecture with bindings to update the code.
