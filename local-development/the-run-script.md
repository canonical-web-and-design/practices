# Running our projects with the ./run script

Each of our projects should conform to exactly the same local development interface,
which should be documented in the project's `README.md`. This should make it simple
for anyone to run any of our projects.

This interface is the `./run` script. Each project's `./run` script should take the same set of commands.
The script will use [Docker](https://www.docker.com/community-edition) containers to spin up each of the required services
for the project in question. Docker should therefore be the single dependency needed to run any of the webteam projects.

## Using the ./run script

First [install Docker](https://docs.docker.com/engine/installation/)
(on Linux you may need to [add your user to the `docker` group](https://docs.docker.com/engine/installation/linux/linux-postinstall/)).

Then to learn about this script's options, type:

``` bash
./run --help
```

The basic options are:

``` bash
./run serve  # Start the Django server, optionally watching for changes
./run build  # Build the CSS
./run watch  # Watch and build the CSS whenever Sass changes
./run test   # Check code syntax and run unit tests
./run clean  # Remove created files and docker containers
```

### Watching in the background

The `serve` function optionally takes a `--watch` argument:

``` bash
./run serve --watch
```

This will effectively run the `./run watch` command in the background while also running the server.

**NB:** You won't see the output from the watcher by default. This makes it difficult to know if it's working properly.

To check if the watcher daemon is running, use `docker ps`. Then you can use `docker attach` to follow the output from the background watcher.

