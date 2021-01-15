# arris_cable_modem_stats

Fork of https://github.com/andrewfraley/arris_cable_modem_stats with influxdb/grafana bits removed.

This is a Python script to scrape stats from the Arris cable modem web interface, and emit as a json object. This currently only works with the Arris SB8200.


## Authentication
In late Oct 2020, Comcast deployed firmware updates to the SB8200 which now require authenticating against the modem.  If your modem requires authentication (you get a login page when browsing to https://192.168.100.1/), then you must edit your config.ini file and set ```modem_auth_required``` to ```True```, and set ```modem_password``` appropriately.  By default, your modem's password is the last eight characters of the serial number, located on a sticker on the bottom of the modem.

## Run Locally

- Install [pipenv](https://github.com/pypa/pipenv). On a Mac with Homebrew, ```brew install pipenv```
- Install pip dependencies (run from the script directory of this repo): ```pipenv install```
- Edit config.ini and change [INFLUXDB] host to your influxdb server
- ```pipenv run python3 arris_stats.py```

### Debugging
```pipenv run python3 arris_stats.py --debug```

## Docker
Run in a Docker container with:

    docker build -t arris_stats .
    docker run arris_stats
