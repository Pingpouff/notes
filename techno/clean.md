# Clean disk

This doc explains how to free up some memory on ubuntu. Mainly free up docker images spaces.

## Journal

Cleans journal log size until it only takes about 200M
> sudo journalctl --vacuum-size=200M

## Docker
Cleans all images
> docker image prune -a --force
