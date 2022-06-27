# {{ kubernetes_namespace }} {{ project_name }} deployment manifests

[![Deploy {{ project_name }} Sandbox](https://github.com/resuelve/infra-rtd/actions/workflows/deploy-{{ project_name }}-{{ kubernetes_namespace }}.yml/badge.svg)](https://github.com/resuelve/infra-rtd/actions/workflows/deploy-{{ project_name }}-{{ kubernetes_namespace }}.yml)

## Introduction

This component stores all the kubernetes manifests required to deploy {{ project_name }} to {{ kubernetes_namespace }}.

## Requirements

To be able to push the container artifact to dockerhub we need to define access by setting up
`DOCKER_USERNAME` and `DOCKER_PASSWORD` secrets.

To be able to automate deployment to kubernetes cluster, you need to define `K8S_CONFIG` by
setting up `RTD_K8S_CONFIG_SANDBOX` secret with `base64` encoded `KUBECONFIG`.

## Namespace manifest

Namespace definition is at `0_namespace.yml`.

## Secrets

All the application configuration are stored in a kubernetes secret called `{{ project_name }}-secret`, this one is a
secret multi key which is referenced from the deployment.

Secrets are created by people using a dot-env file:

```
$ vim app.env
SECRET_KEY_BASE=*****
PG_DB_URL=*****
```

**IMPORTANT:** Replace `*****` with correct values.

**IMPORTANT:** Be sure not to leave blank characters at the beginning or the end of lines.

Then you need to convert it to base64 format:

```
$ base64 app.env
```
**IMPORTANT:** The character available from create one secret is A-Z, a-z, 0-9 and "_".

Copy the content and paste it in the Github Repository Secret called `CONFIG_APP_SANDBOX`.

Where **_APP_** is the name of you project. Use `_` only to separate each word.

**IMPORTANT:** After you made local change to the dot-env file, update it in the corresponding keeper secret.

## Deployment manifest

Deployment definition is at `1_deployment.yml`.

**WARNING:** Don't apply before creating deployment secrets.

## Service manifest

Service definition is at `2_service.yml`.

## Ingress manifest

Ingress definition is at `3_ingress.yml`.

## Workflow

To automate the creation and update of kubernetes resources we have included a github action workflow called:
`.github/workflows/deploy-{{ project_name }}-{{ kubernetes_namespace }}.yml`.

## Recommendations

For quality deployments always:

 * Remember to validate your manifests before commit.
 * Remember to change the value of vars in the file `app.env` in `Keeper`.
 * Remember don't push credentials.
