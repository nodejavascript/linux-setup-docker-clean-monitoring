Title: I created a self hosted droplet procedure for smart time-series analytics

Excerpt: Start your embedded journey with this recipe of 15 docker containers including nmon, netdata, portainer, dozzle, grafana, prometheus, node-exporter, mqtt-exporter, cadvisor, uptime-kuma, traefik, mysql, phpmyadmin, redis, mongodb


LICENSE: MIT

Documentation: [Project README.md](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/README.md)

```
git clone git@github.com:nodejavascript/linux-setup-docker-clean-monitoring.git
```

## Pay smarter.

#### Pay where the facts are.
<br>

- Offload `docker containers` proven to require separation from cluster
- Upgrade `instances` with CPU or memory if `factually` it's needed.

**BONUS** : Supports [Tasmota](https://tasmota.github.io/install/) metrics as seen here:

#### `grafana` monitoring `tasmota` metrics via `mqtt-exporter` and `prometheus`
![tasmota-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656438685/public/Selection_025.png_dfyaqs.png)

## Features support [r/selfhosted](https://www.reddit.com/r/selfhosted/):

[<img src="https://img.shields.io/reddit/subreddit-subscribers/selfhosted?style=for-the-badge" alt="subreddit-subscribers/selfhosted">](https://www.reddit.com/r/selfhosted/)

List of containers in [docker-compose.yml](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/docker-compose.yml)

```19999 : netdata
9000 : portainer
9999 : dozzle
3050 : grafana
9090 : prometheus
9100 : node-exporter
9001 : mqtt-exporter
8080 : cadvisor
3001 : uptime-kuma
80 : traefik
443 : traefik
3306 : mysql
8183 : phpmyadmin
6379 : redis
8081 : rediscommander
27017 : mongodb
```


#### `cadvisor` monitoring all `docker` listed in [docker-compose.yml](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/docker-compose.yml)
![docker-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656438277/public/Selection_023.png_ge9txu.png)


### The following procedure will give you:

 - Reactive time-series charts from `grafana` to find anti-patterns and anomalies.

- The `server's` 1) CPU, 2) memory, 3) network and  4) disk usage.

- Each `docker container's` 1) CPU, 2) memory, 3) network and  4) disk usage.

  - Real-time `stdout` for [all containers](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/docker-compose.yml#L1)


- [Procedures](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring#and-then-use-if-you-want-to-build-with-nodejs-on-server) to install `ssh` key, cloning repos, installing `npm` and `n`

- [Procedures](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring#and-then-traefik-will-create-acmejson) to install `treafik` with [multi-domain](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/traefik.toml#L51-L55) example.

- [Ports](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring#give-only-yourself-access-and-maybe-adjust-open-ports-on-your-host-firewall) to open on your firewall.

#### Persistent monitored data:
<br>

- Metrics history for `server` and each `docker container`

- Find what
  - led to a crash
  - what scripts are taxing your resources
  - containers hogging docker resources

## Self hosted integration.
<br>

- `ghost` blog integrated with

    - traefik, [pre-configured](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/traefik.toml#L51-L54) to server multiple domains names

    - mailgun SMTP, [pre-configured](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/ghost_myblog_config.json#L37) to add your mailgun password.

    - mysql

        - phpmyadmin, to add database for `ghost`


- `mongodb` because it's SO useful

- `redis`, [pre-configured](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/.env.example#L23-L25) with `rediscommander`.

## Real-time health monitoring

#### Essentials:

- `nmon`, the last resort command-line monitor you will need if your instance is *very unhealthy* (for example docker won't boot)

`nmon` monitoring `server`
  ![nmon-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656439066/public/Selection_027.png_f8twcl.png)

- `netdata`, real-time granular metrics for watching:
  - installs,
  - script executions or,
  - real-time services.


  `netdata` monitoring `server`
    ![netdata-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656438350/public/Selection_024.png_vkhiis.png)

- `portainer`, web interface for docker containers standard install

- `dozzle`, real-time stdout for running docker containers

`dozzle` monitoring my [MQTT Broker](https://github.com/nodejavascript/selfhosted-mqtt-broker-nodejs/blob/main/README.md)
![mqtt-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656438779/public/Selection_026.png_izlgvv.png)


- `grafana`, [pre-configured](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring#setup-grafana) setup the [dashboards](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring#add-new-dashboards-with-these-templateids) to [monitor time-series metrics with beautiful charts and features](https://www.google.com/search?q=grafana+time-series+metrics+with+beautiful+charts+and+features&tbm=vid).

#### Telemetry:

#### `node-exporter` monitoring `server`
![server-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656438102/public/Selection_022.png_fjyzxd.png)


- `prometheus`, [pre-configured](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/prometheus.yml) to send necessary metrics to Grafana for you.
    - `prometheus`, self metrics
    - `node-exporter`, provides server metrics
    - `cadvisor`, provides docker metrics
    - `mqtt-exporter`, provides embedded sensor metrics published to an [MQTT broker like mine](https://github.com/nodejavascript/selfhosted-mqtt-broker-nodejs).


#### `prometheus` can scale to many [prom-exporters](https://prometheus.io/docs/instrumenting/exporters/)
![server-snapshot](https://res.cloudinary.com/nodejavascript-com/image/upload/v1656442352/public/Selection_028.png_w5vnp0.png)

# HAVE FUN!

See [README.md](https://github.com/nodejavascript/linux-setup-docker-clean-monitoring/blob/master/README.md) for more details.

## Contact
* Home - [nodejavascript.com](https://nodejavascript.com?ref=githubContact)
* YouTube - [nodejavascript](https://www.youtube.com/channel/UCZFJHjd0c79xyj2SpB8UbJg)
* Twitter - [@nodejavascript](https://twitter.com/nodejavascript)
* LinkedIn - [@nodejavascript](https://linkedin.com/in/georgefielder)
* Email - [github@nodejavascript.com](mailto:github@nodejavascript.com)
