![bro-logo](https://github.com/blacktop/docker-zeek/raw/master/docs/logo.png)

# docker-zeek

[![CircleCI](https://circleci.com/gh/blacktop/docker-zeek.png?style=shield)](https://circleci.com/gh/blacktop/docker-zeek) [![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org) [![Docker Stars](https://img.shields.io/docker/stars/blacktop/zeek.svg)](https://hub.docker.com/r/blacktop/zeek/) [![Docker Pulls](https://img.shields.io/docker/pulls/blacktop/zeek.svg)](https://hub.docker.com/r/blacktop/zeek/) [![Docker Image](https://img.shields.io/badge/docker%20image-40.1MB-blue.svg)](https://hub.docker.com/r/blacktop/zeek/)

> [Zeek Network Security Monitor](https://github.com/zeek/zeek) Dockerfile

---

**Table of Contents**

- [Dependencies](#dependencies)
- [Image Tags](#image-tags)
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [Issues](#issues)
- [CHANGELOG](#changelog)
- [Contributing](#contributing)
- [License](#license)

## Dependencies

- [alpine:3.8](https://hub.docker.com/_/alpine/)

## Image Tags

```bash
$ docker images

REPOSITORY           TAG          SIZE
blacktop/zeek        latest       40.1MB
blacktop/zeek        2.6          40.1MB
blacktop/zeek        elastic      101MB
blacktop/zeek        kafka        43.4MB
blacktop/zeek        broctl       84MB
```

## Installation

1. Install [Docker](https://docs.docker.com).
2. Download [trusted build](https://hub.docker.com/r/blacktop/zeek/) from public [Docker Registry](https://hub.docker.com): `docker pull blacktop/zeek`

## Getting Started

```bash
$ wget https://github.com/blacktop/docker-zeek/raw/master/pcap/heartbleed.pcap
$ wget https://github.com/blacktop/docker-zeek/raw/master/scripts/local.bro
$ docker run --rm \
         -v `pwd`:/pcap \
         -v `pwd`/local.bro:/usr/local/bro/share/bro/site/local.bro \  # All default modules loaded
         blacktop/zeek -r heartbleed.pcap local "Site::local_nets += { 192.168.11.0/24 }"
```

```bash
$ ls -l

-rw-r--r--  1 blacktop  staff   635B Jul 30 12:11 conn.log
-rw-r--r--  1 blacktop  staff   754B Jul 30 12:11 files.log
-rw-r--r--  1 blacktop  staff   384B Jul 30 12:11 known_certs.log
-rw-r--r--  1 blacktop  staff   239B Jul 30 12:11 known_hosts.log
-rw-r--r--  1 blacktop  staff   271B Jul 30 12:11 known_services.log
-rw-r--r--  1 blacktop  staff    17K Jul 30 12:11 loaded_scripts.log
-rw-r--r--  1 blacktop  staff   1.9K Jul 30 12:11 notice.log <====== NOTICE
-rw-r--r--  1 blacktop  staff   253B Jul 30 12:11 packet_filter.log
-rw-r--r--  1 blacktop  staff   1.2K Jul 30 12:11 ssl.log
-rw-r--r--  1 blacktop  staff   901B Jul 30 12:11 x509.log
```

```bash
$ cat notice.log | awk '{ print $11 }' | tail -n4

Heartbleed::SSL_Heartbeat_Attack
Heartbleed::SSL_Heartbeat_Odd_Length
Heartbleed::SSL_Heartbeat_Attack_Success
```

## Documentation

- [Usage](https://github.com/blacktop/docker-zeek/blob/master/docs/usage.md)
- [Integrate with the Elasticsearch](https://github.com/blacktop/docker-zeek/blob/master/docs/elastic.md)
- [Integrate with Kafka](https://github.com/blacktop/docker-zeek/blob/master/docs/kafka.md)
- [Tips and Tricks](https://github.com/blacktop/docker-zeek/blob/master/docs/tips-and-tricks.md)

## Issues

Find a bug? Want more features? Find something missing in the documentation? Let me know! Please don't hesitate to [file an issue](https://github.com/blacktop/docker-zeek/issues/new) and I'll get right on it.

## CHANGELOG

See [`CHANGELOG.md`](https://github.com/blacktop/docker-zeek/blob/master/CHANGELOG.md)

## Contributing

[See all contributors on GitHub](https://github.com/blacktop/docker-zeek/graphs/contributors).

Please update the [CHANGELOG.md](https://github.com/blacktop/docker-zeek/blob/master/CHANGELOG.md) and submit a [Pull Request on GitHub](https://help.github.com/articles/using-pull-requests/).

## License

MIT Copyright (c) 2018 **blacktop**
