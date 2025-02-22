---

title: Deploy
layout: col-document
tags: threatdragon
author:
contributors:
document: Threat Dragon version 2.0
order: 38
permalink: /docs-2/deploy/

---

{% include breadcrumb.html %}
# GitHub Actions

[GitHub Actions](https://docs.github.com/en/actions/reference) are used to test, build and deploy Threat Dragon.
These actions live in the `.github/workflows` directory.

## Deploy

The deploy action is run on any "push" to the main branch (this includes merged pull requests),
and serves as Threat Dragon's continuous delivery pipeline.

### Build
This workflow builds and pushes the Docker image with the `latest` tag.
The `latest` tag is not consider stable, and may be broken at times.
While we do our best to maintain a fully functioning main branch, mistakes will happen.
Additionally, the full end to end test suite is only run once per day, so errors may not be immediately available.

### Deploy
The latest image is deployed to [https://www.threatdragon.com/](https://www.threatdragon.com/).

### Smokes
Smoke tests are run against the deployed image to ensure the deployment succeeded.

### Rollback
If the smokes fail, the deployment is rolled back.
