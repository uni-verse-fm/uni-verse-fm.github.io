# Nix
Uni-verse is now hosted on a NixOS server, using a flake system module that can be imported and used in any NixOS server.

Using this technology allows for a fine grained control over how uni-verse could be distributed, without complicating the process of scaling it up if needed.

PS: Please note that for priority reasons, the flake currently behave no differently than a docker-compose. This is meant to be changed in the future.
