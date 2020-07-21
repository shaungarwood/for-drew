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

---

## Running multiple containers w/ docker-compose

1. ```docker-compose up -d redis``` start just redis
2. ```docker-compose ps``` see that redis is running
3. ```docker-compose run killer-app``` run a one-off container, sometimes followed by a command

Notice the ```stdin_open: true``` and ```tty: true``` in the docker-compose.yml file. This is the same as "docker run -it" above.

Connect to the redis container using the pry session in "killer-app":
```
[1] pry(main)> require 'redis'
=> true
[2] pry(main)> redis = Redis.new(host: "redis")
=> #<Redis client v4.2.1 for redis://redis:6379/0>
[3] pry(main)> redis.ping
=> "PONG"
```

Notice too, that you must specify the host for connecting to redis. That's because it's not actually "localhost". It's a seperate container. But docker-compose makes networking really easy, each container can be referenced/connected to using the service name you used in the docker-compose.yml file, "redis" in this case.
