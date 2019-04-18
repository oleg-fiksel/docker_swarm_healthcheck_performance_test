# Background

Docker caused high load on my VM executing health checks.
To dig deeper I created this repo to test different kinds of healh checks.
Moby project bug: https://github.com/moby/moby/issues/39102

# Run benchmark

## Build images

```
for i in bash_hc cat_hc echo_hc stat_hc no_hc; do
	docker-compose build
done
```

## Run Docker stack

```
export FLAVOR=no_hc && \
	docker stack up -c docker-compose.yaml $FLAVOR
```

## Remove Docker stack

```
docker stack rm $FLAVOR
```

# Measurement

For measurement NetData was used running on the host

```
cd netdata && \
	docker-compose up -d && \
	docker-compose logs -f
```
