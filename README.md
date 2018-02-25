# Envoy POC

## How to play

Boot up docker compose environment:
```
docker-compose build && docker-compose up
```

Play:
```
# head into the helper container:
docker exec -it envoypoc_helper_1 bash

# nghttp one service
nghttp https://s1:5000/data

# nghttp all the services
seq 4 | xargs -I{} nghttp https://s{}:5000/data

# nghttp all the services via envoy
seq 10 | xargs -I{} nghttp http://envoy/data
```

Watch:
```
# from your mac
 watch -tde 'curl -sS "http://localhost:8001/clusters"'
```

Useful commands:
```
# get a list of admin commands ('cluster' / 'reset_counters' very helpful)
curl -sS "http://localhost:8001"
envoy admin commands:
  /certs: print certs on machine
  /clusters: upstream cluster status
  /cpuprofiler: enable/disable the CPU profiler
  /healthcheck/fail: cause the server to fail health checks
  /healthcheck/ok: cause the server to pass health checks
  /hot_restart_version: print the hot restart compatability version
  /listeners: print listener addresses
  /logging: query/change logging levels
  /quitquitquit: exit the server
  /reset_counters: reset all counters to zero
  /server_info: print server version/status information
  /stats: print server stats
