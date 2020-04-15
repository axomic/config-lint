# config-lint Installation

There are three main ways that you can install `config-lint`

* homebrew
* docker
* manually

## Homebrew

You can use [Homebrew](https://brew.sh/) to install the latest version:

``` bash
brew tap stelligent/tap
brew install config-lint
```

## Docker

You can pull the latest image from [DockerHub](https://hub.docker.com/r/stelligent/config-lint):

``` bash
docker pull stelligent/config-lint
```

Note that if you choose to install and run via `docker` then you will need mount a directory to the running container so that it has access to your configuration files.

``` bash
cd /path/to/your/configs/
docker run -v $(pwd):/foobar stelligent/config-lint -terraform /foobar/foo.tf
--- or ---
docker run --mount src="$(pwd)",target=/foobar,type=bind stelligent/config-lint -terraform /foobar/foo.tf
```

If wishing to test Kubernetes configuration, you will need to put the example Kubernetes rules into your local path and reference it accordingly, or you can have your own set of rules that you want to validate against.

For example:
```
docker run -v $(pwd):/foobar stelligent/config-lint -rules /foobar/path/to/my/rules/kubernetes.yml /foobar/path/to/my/configs
```
If you don't have your own set of custom rules that you want to run against your Kubernetes file then feel free to copy or download the example set from [example-files/rules/kubernetes.yml](example-files/rules/kubernetes.yml).

## Manually

You can install latest and pre-releases manually from [releases](https://github.com/stelligent/config-lint/releases).