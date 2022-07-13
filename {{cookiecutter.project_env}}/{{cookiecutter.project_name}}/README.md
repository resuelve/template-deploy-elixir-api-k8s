# {{ cookiecutter.k8s_namespace }} {{ cookiecutter.project_name }} deployment manifests

## Introduction

This component stores all the k8s resources manifests required to deploy
{{ cookiecutter.project_name }} to {{ cookiecutter.k8s_namespace }}.

## Requirements

A running cluster and admin privileges to create all the resources.

## Deployment manifest

Deployment definition is at `1_deployment.yml`.

## Service manifest

Service definition is at `2_service.yml`.

## Ingress manifest

Ingress definition is at `3_ingress.yml`.

## Recommendations

For quality deployments always:

* Remember to validate your manifests before commit.
