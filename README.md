# template-deploy-elixir-api-k8s

Template with kubernetes manifests for elixir api deployments.

## Install

You need to install `cookiecutter` on your local:

```shell
$ brew install cookiecutter
```

## Usage

Generate a template:

```shell
$ cookiecutter git@github.com:resuelve/template-deploy-elixir-api-k8s.git
```

This command will ask you for your project attributes, and after that
creates a directory with your project's name, for example:

```shell
$find example-api
example-api
example-api/2_service.yml
example-api/3_ingress.yml
example-api/0_namespace.yml
example-api/README.md
example-api/1_deployment.yml
```
