# Modified SA:MP Image for Pterodactyl

The only difference between this image and the official one is the version used for `openssl` and is plug-and-play with existing SA:MP servers created on Pterodactyl (meaning you can replace the Server Docker image and just rebuild the container)

## Why?

**TL;DR:** This downgrade fixes some crashes/errors on some plugins.

When using `maddinat0r/samp-discord-connector` we noticed that our servers were crashing with the message "Service not found (-8)" when trying to resolve `gateway.discord.gg`, which is an `EAI_SERVICE` error on [getaddrinfo](http://man7.org/linux/man-pages/man3/getaddrinfo.3.html).

After hours modifying container capabilities, previleged mode, disabling AppArmor, replacing the image with `dennorske/pterodactyl-samp-new` fixed everything.

This repository was forked only to allow other people with the same problem to find this solution.

## How to use

  * Clone this repository on your node;
  * Navigate to the repository directory with `cd pterodactyl-samp-new`;
  * Build the image with `docker build -t my_samp_image .`;
  * Update Egg default Docker image or current server image with `~my_samp_image`
  * Rebuild server container
