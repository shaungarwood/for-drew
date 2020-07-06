# For Drew

To the end of "well it works on my machine..."

Build
```
$ docker build -t for-drew .
```

Run
```
$ docker run --rm -it for-drew
```

The ```--rm``` will remove the container after you exit out. Kind of the default, if you're not in it anymore - you don't want it running.

```it``` is interactive. Allows the docker container to bind to your terminal so you can type in it.
