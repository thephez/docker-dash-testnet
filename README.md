# docker-dash-testnet

## Start services

Foreground: `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml up`

Background: `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml up -d`

## Stop services

All services: `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml stop`

Specific service: `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml stop dapi_core`

## Remove components created by `up`

Retain volume(s):`docker-compose -p dash-testnet -f testnet-dashd_dapi.yml down`

Remove volume(s): `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml down --volume`

## View logs

All services: `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml logs`

Specific service (e.g. `dashd_core`): `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml logs -f dashd_core`

Last 10 lines only: `docker-compose -p dash-testnet -f testnet-dashd_dapi.yml logs --tail 10`

## Execute command on a service

`docker-compose -p dash-testnet -f testnet-dashd_dapi.yml exec dashd_core ls`

`docker-compose -p dash-testnet -f testnet-dashd_dapi.yml exec dashd_core dash-cli -conf=/dash.conf getinfo`

## Included services

| Service | Docker Image | Function |
| --- | --- | --- |
`dashd_core` | [dashpay/dashd](https://hub.docker.com/r/dashpay/dashd) | Dash Core Blockchain |
`dapi_core`  | [dashpay/dapi](https://hub.docker.com/r/dashpay/dapi) | HTTP API |
`insight_api` | [dashpay/insight-api](https://hub.docker.com/r/dashpay/insight-api) | |
