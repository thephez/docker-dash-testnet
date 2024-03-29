# docker-dash-testnet

## Start services

Foreground: `docker-compose -p dash-testnet -f docker-compose.yml up`

Background: `docker-compose -p dash-testnet -f docker-compose.yml up -d`

## Stop services

All services: `docker-compose -p dash-testnet -f docker-compose.yml stop`

Specific service: `docker-compose -p dash-testnet -f docker-compose.yml stop dapi_core`

## Remove components created by `up`

Retain volume(s):`docker-compose -p dash-testnet -f docker-compose.yml down`

Remove volume(s): `docker-compose -p dash-testnet -f docker-compose.yml down --volume`

## View logs

All services: `docker-compose -p dash-testnet -f docker-compose.yml logs`

Specific service (e.g. `dashd_core`): `docker-compose -p dash-testnet -f docker-compose.yml logs -f dashd_core`

Last 10 lines only: `docker-compose -p dash-testnet -f docker-compose.yml logs --tail 10`

## Execute command on a service

`docker-compose -p dash-testnet -f docker-compose.yml exec dashd_core ls`

`docker-compose -p dash-testnet -f docker-compose.yml exec dashd_core dash-cli -conf=/dash.conf getinfo`

## Included services

| Service | Docker Image | Function |
| --- | --- | --- |
`dashd_core` | [dashpay/dashd](https://hub.docker.com/r/dashpay/dashd) | Dash Core Blockchain |
`dapi_core`  | [dashpay/dapi](https://hub.docker.com/r/dashpay/dapi) | HTTP API |
`insight_api` | [dashpay/insight-api](https://hub.docker.com/r/dashpay/insight-api) | Supports some DAPI API endpoints |

## Mining

If running on a devnet, it is possible to mine by configuring a cron entry to
run `docker-compose exec` as follows:

`*/2 * * * * /usr/local/bin/docker-compose -f </path/to/config>/docker-compose.yml exec -T dashd_core dash-cli -conf=/dash.conf generate 1`
