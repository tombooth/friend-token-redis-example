# friend-token-redis-example

An example compojure app using friend-token-redis.

## Prerequisites

You will need [Leiningen][1] 1.7.0 or above installed.

[1]: https://github.com/technomancy/leiningen

You will also need redis running on 127.0.0.1:6379

## Running

To start the example web app, run:

    lein ring server

If you run:

    curl -v http://localhost:3000

You should get a 401. If you then run:

    curl -v -XPOST -H "Accept: application/json" -H "Content-type: application/json" http://localhost:3000/authenticate -d '{"username":"friend","password":"clojure"}'

You should get a 200 with X-Auth-Token as a response header. To see that this is valid run, with <token_value> being the value of the returned X-Auth-Token header:

    curl -v -H 'X-Auth-Token: <token_value>'  http://localhost:3000

The TTL is only 30 seconds (as defined in the call to RedisTokenStore) so if it 401s it is likely this.

## License

Copyright © 2013 Tom Booth
