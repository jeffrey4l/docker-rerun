docker-rerun
===============================================================================

`docker-rerun` is a small utility script that makes it easy to re-run docker
containers using the same arguments you used previously.

Want to update to a newer image, or add a missing port publication?
docker-rerun's got you covered.

## How to use

In the most basic usage, you pass in a container name and it will be
stopped, deleted and recreated:

    $ ./docker-rerun apache

To check what exactly is going to be performed beforehand, use the --dry-run
option:

    $ ./docker-rerun --dry-run apache
    docker stop apache
    docker rm apache
    docker run --name=apache -p=80:80/tcp --restart=always apache:latest

## What's supported

At present docker-rerun supports a small number of commonly used arguments:

    * Names (--name)
    * Networks (--net)
    * Port publications (-p)
    * Restart policies (--restart)
    * Volumes (-v/--volume, and --volumes-from)

## What's not done yet

Many other command line arguments:

    * Commands
    * Environment variables
    * Labels
    * Linking and aliases
    * Permissions and policies

Additional options to allow mutating the container config when rerunning.
For example:

    $ ./docker-rerun --image nginx:1.11.1 nginx

Should replace the previously used image with the one specified.
