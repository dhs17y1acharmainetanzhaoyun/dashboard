# Dashboard [![GitHub version](https://badge.fury.io/gh/bblfsh%2Fdashboard.svg)](https://github.com/bblfsh/dashboard/releases) [![Build Status](https://travis-ci.org/bblfsh/dashboard.svg?branch=master)](https://travis-ci.org/bblfsh/dashboard)


## Installation

The easiest way to deploy **dashboard** is using *Docker*.

```sh
docker run -p 8080:80 bblfsh/dashboard -bblfsh-addr <bblfsh-server-addr>
```

If you don't have a bblfsh server running you can execute the dashboard and the server using the following command:

```sh
docker run --privileged -d -p 9432:9432 --name bblfsh bblfsh/bblfshd
docker run -p 8080:80 --link bblfsh bblfsh/dashboard -bblfsh-addr bblfsh:9432
```

Please read the [getting started](https://doc.bblf.sh/user/getting-started.html) guide, to learn more about how to use and deploy a bblfsh server, install drivers, etc.

If don't want to run **dashboard** using our *Docker* image you can download a binary from [releases](https://github.com/bblfsh/dashboard/releases) page.

## Development

The dashboard is a Golang application, so in order for all further insturctions to work please make sure it's under `$GOPATH` in your filesystem.

### Dependencies

 - Golang 1.9
 - Node 8.x
 - Yarn 1.x

The dashboard consits of a web server, serving static assets and an intermediate API that connects to the bblfsh server.

Every time you change any assets in `./public` or `./src`, you needed to regenerate the `server/asset/asset.go` containing all static files of the frontend.

It can be done with:
```sh
make assets
```

### Access the dashboard locally

To run it locally you can run:
```sh
make serve
```
It will take care of re-generateing the assets file, building dashboard api, and to serving the updated dashboard itself.

Dashboard will be available on http://localhost:9999

## License

GPLv3, see [LICENSE](LICENSE)
