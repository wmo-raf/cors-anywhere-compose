# cors-anywhere


The docker/docker compose config for [cors-anywhere](https://github.com/Rob--W/cors-anywhere).

### Supported tags and respective `Dockerfile` links

* [`0.4.4`, `latest`](https://github.com/testcab/docker-cors-anywhere/blob/master/Dockerfile)
* [`0.4.3`](https://github.com/testcab/docker-cors-anywhere/blob/0.4.3/Dockerfile)


### Envirionment Variables

Env  | Default | Description
---- | ------- | -----------
PORT | 8080    | Server listening port
KEY  |         | Content or filename of TLS Key
CERT |         | Content or filename of TLS Certificate
CORSANYWHERE_BLACKLIST | | If set, requests whose origin is listed are blocked.<br>Comma separated. Example: `https://abuse.example.com,http://abuse.example.com`
CORSANYWHERE_WHITELIST | | If set, requests whose origin is not listed are blocked.<br>If this list is empty, all origins are allowed.<br>Comma separated. Example: `https://good.example.com,http://good.example.com`
CORSANYWHERE_RATELIMIT | | Format: `<max requests per period> <period in minutes> <non-ratelimited hosts>`<br>For example, to blacklist abuse.example.com and rate-limit everything to 50 requests per 3 minutes, except for my.example.com and my2.example.com (which may be unlimited), use:<br>`50 3 my.example.com my2.example.com`


### Putting cors-anywhere behind NGINX Proxy

[See original details here](https://github.com/Rob--W/cors-anywhere/issues/143#issuecomment-452468128)

```
 location /cors/ {
      if ($request_uri ~ ^/cors/(.*) ) {
        set $cors_request_uri $1;
      }

      proxy_pass http://127.0.0.1:8080/$cors_request_uri;
      proxy_buffering off;
    }
```


## LICENSE

This repository is licensed under [MIT](LICENSE).

[cors-anywhere](https://github.com/Rob--W/cors-anywhere#license) is `Copyright (C) 2013 - 2016 Rob Wu rob@robwu.nl`
