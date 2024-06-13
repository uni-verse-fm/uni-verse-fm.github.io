# Nix

Uni-verse is now hosted on a NixOS server, using a flake system module that can be imported and used in any NixOS server.

Using this technology allows for a fine grained control over how uni-verse could be distributed, without complicating the process of scaling it up if needed.
Nix also allows creating a fully reproducible, reliable development environment that prevents any configuration or installation from being needed.

In those ways, Nix could is going to be the backbone of uni-verse's development platform.

PS: Please note that for priority reasons, [the flake](https://github.com/uni-verse-fm/uni-verse-production/blob/main/nix/module.nix) currently behave no differently than a docker-compose. This is meant to be changed in the future, after the frontend rewrite.
