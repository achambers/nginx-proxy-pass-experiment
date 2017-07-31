# Nginx `proxy_pass` experiment

This repo is a short experiment to verify if nginx could use `proxy_pass` to
forward the request for an asset to S3. To test this, do the following:

Clone this repo:

```
$ git clone git@github.com:achambers/nginx-proxy-pass-experiment.git
```

Build the Docker image:

```
$ docker build -t nginx-experiment .
```

Run the Docker container:

```
$ docker run --rm -P nginx-experiment
```

Find the forwarded port:

```
$ docker ps

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                   NAMES
1ef2b8cc6f53        nginx-experiment    "nginx -g 'daemon ..."   13 seconds ago      Up 12 seconds       0.0.0.0:32785->80/tcp   serene_jang
```

Request the asset:

```
curl http://localhost:32785/ftdeploy/manifest.txt
```
