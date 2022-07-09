# template-deploy-elixir-api-k8s

[![CI](https://github.com/resuelve/template-deploy-elixir-api-k8s/actions/workflows/ci.yml/badge.svg)](https://github.com/resuelve/template-deploy-elixir-api-k8s/actions/workflows/ci.yml)

This project helps Elixir developers to create all the infrastructure boilerplate that every Elixir API needs
at the beginning of the development process.

It creates kubernetes manifests for `deployments`, `services` and `ingress` resources.

## Install

You need to install `cookiecutter` on your local with another testing tools:

``` shell
$ brew install cookiecutter yamllint kubernetes-validate
```

## Usage

Generate a template:

``` shell
$ cookiecutter git@github.com:resuelve/template-deploy-elixir-api-k8s.git
```

This command will ask you for your project attributes, and after that
creates a directory with your project's name, for example:

``` shell
$ find example-api
example-api
example-api/2_service.yml
example-api/3_ingress.yml
example-api/README.md
example-api/1_deployment.yml
```

### Usage with infra-rtd

If you need to create the kubernetes manifests for a project that its manifests are hosted in the repo
`resuelve/infra-rtd` you can use something like this:

``` shell
$ git clone git@github.com:resuelve/infra-rtd.git
$ cd infra-rtd/kubernetes/sandbox
$ gcb foo.lanito/example_api_sandbox
$ cookiecutter git@github.com:resuelve/template-deploy-elixir-api-k8s.git
$ gcmsg "New deployment manifests to example-api in sandbox cluster." -a
$ gpsup
```

### Usage with resuelve-cloud-configs

If you need to create the kubernetes manifests for a project that its manifests are hosted in the repo
`resuelve-cloud-configs` you can use something like this:

``` shell
$ git clone ssh://foo.lanito@resuelve.io@source.developers.google.com:2022/p/resonant-hawk-169822/r/resuelve-cloud-configs
$ cd resuelve-cloud-configs/sandbox
$ gcb foo.lanito/example_api_sandbox
$ cookiecutter git@github.com:resuelve/template-deploy-elixir-api-k8s.git
$ gcmsg "New deployment manifests to example-api in sandbox cluster." -a
$ gpsup
```

### Contributions

I you find this useful please buy me a cofee :P, I'm just kidding, just try to use it and give feedback.

### References

Please read the follow references for more details:

* [Cookicutter home](https://github.com/cookiecutter/cookiecutter)
* [Cookicutter documentation](https://cookiecutter.readthedocs.io/en/stable/)