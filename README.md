[![Travis (.org) branch](https://img.shields.io/travis/nl2go/hetzner-robot-api-mock/master)](https://travis-ci.org/nl2go/hetzner-robot-api-mock)
[![Codecov](https://img.shields.io/codecov/c/github/nl2go/hetzner-robot-api-mock)](https://codecov.io/gh/nl2go/hetzner-robot-api-mock)
[![Docker Pulls](https://img.shields.io/docker/pulls/nl2go/hetzner-robot-api-mock)](https://hub.docker.com/r/nl2go/hetzner-robot-api-mock)

# Hetzner Robot API Mock

A HTTP server based on [JSON Server](https://github.com/typicode/json-server) that mocks [Hetzner Robot API](https://robot.your-server.de/doc/webservice/en.html).

## Development

Run locally built image

    docker-compose up

Rebuild image

    docker-compose build

## Examples

### Create Firewall Template
```
curl -u user:password http://localhost:3000/firewall/template \
--data-urlencode 'name=My new template' \
--data-urlencode 'whitelist_hos=true' \
--data-urlencode 'is_default=false' \
--data-urlencode 'rules[input][0][name]=rule 1' \
--data-urlencode 'rules[input][0][ip_version]=ipv4' \
--data-urlencode 'rules[input][0][src_ip]=1.1.1.1' \
--data-urlencode 'rules[input][0][dst_port]=80' \
--data-urlencode 'rules[input][0][action]=accept'
```

### Configure Firewall
```
curl -u user:password http://localhost:3000/firewall/111.111.111.111 \
--data-urlencode 'status=disabled' \
--data-urlencode 'whitelist_hos=true' \
--data-urlencode 'rules[input][0][name]=rule 1' \
--data-urlencode 'rules[input][0][ip_version]=ipv4' \
--data-urlencode 'rules[input][0][src_ip]=1.1.1.1' \
--data-urlencode 'rules[input][0][dst_port]=80' \
--data-urlencode 'rules[input][0][action]=accept'
```

## Maintainers

- [dirkaholic](https://github.com/dirkaholic)
- [build-failure](https://github.com/build-failure)

## License

See the [LICENSE.md](LICENSE.md) file for details
