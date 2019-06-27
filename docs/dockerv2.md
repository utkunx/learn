# docker commands v2

## Table of Contents

**[`docker images`](#docker-images)**<br>
**[`docker pull`](#`docker-pull`)**<br>
**[`docker run`](#`docker-run`)**<br>
**[-it](##`-it`)**<br>
**[`docker ps`](#`docker-ps`)**<br>
**[`extarnal links`](#extarnal-links)**<br>

## `docker images`

* `docker images` command to see a list of all images on your system.

* An important distinction with regard to images is between `base images` and `child images`.
    * `Base images` are images that have no parent images, usually images with an `OS` like `ubuntu`, `alpine` or `debian`.
    * `Child images` are images that `build` on `base images` and add additional functionality.

----

## `docker pull`

* `docker pull alpine` command fetches image and saves it in our system.

----

## `docker run`

* `docker run alpine ls -l`
    * When you call `run`,
        * `docker pull` > create the `container` > `docker run`

* `docker run alpine /bin/sh`
    * These `interactive shells` will exit after running any scripted commands,
* `docker run -it alpine /bin/sh`
    * unless they are run in an `interactive terminal`

----

## `-it`

* `-it` means `interactive terminal`
    * `-i`, `--interactive`; Keep STDIN open even if not attached
    * `-t`, `--tty`; Allocate a pseudo-TTY

* other commands, `ls -l`, `uname -a`

----

## `docker ps`

* `docker ps` command shows you all `containers` that are currently running.
* `docker ps -a` command shows a list of all `containers` that you ran.

----

## extarnal links

* [docker-baby-steps](https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md)

----
