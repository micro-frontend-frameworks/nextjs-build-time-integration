<p align="center">
  <img alt="micro-frontend-frameworks logo" src="https://raw.githubusercontent.com/micro-frontend-frameworks/docs/main/assets/logo.png" height="200" width="200" />
  <h3 align="center">NextJS microfrontend framework with build-time integration approach</h3>
</p>

---

- [Packages](#packages)
- [Strenghts](#strenghts)
- [Weaknesses](#weaknesses)
- [Playing with the POC](#playing-with-the-poc)
- [Architecture](#architecture)
  - [Interaction Overview](#interaction-overview)

## Packages

| Package                                                                               | Description                                                                       |
| ------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [`@mfe-frameworks/builder`](https://github.com/micro-frontend-frameworks/builder)     | Service responsible for patching tenants with new apps                            |
| [`@mfe-frameworks/cli`](https://github.com/micro-frontend-frameworks/cli)             | CLI that interfaces with the registry and the builder services to develop MF apps |
| [`@mfe-frameworks/container`](./packages/container)                                   | Container application                                                             |
| [`@mfe-frameworks/config`](https://github.com/micro-frontend-frameworks/config)       | Configuration interface to fit a MF app into the container of a tenant            |
| [`@mfe-frameworks/registry`](https://github.com/micro-frontend-frameworks/registry)   | Service that acts as a wrapper for Firestore                                      |
| [`@mfe-frameworks/templates`](https://github.com/micro-frontend-frameworks/templates) | Getting started templates                                                         |

## Strenghts

- Native performance from NextJS
- Benefits from all features from NextJS (through the container application)
- Built-in UX consistency
- Automated CHANGELOG for each tenant.
- Code deduplication.
- Acceptable workflow for **small teams** or **lonely wolves** that doesn't deal with thousands of tenants or microfrontend apps changes at a fast pace.

## Weaknesses

- Lockstep release process.
  - > If the concepts presented here are applied smartly, it is possible to skip the lockstep release process.
- Difficult to scale. How to orchestrate updates in thousands of tenants and hundreds of apps, often simultaneously? Good luck with that.
- Dependencies synchronization is very tricky at scale.

## Playing with the POC

```bash
# Install the CLI
yarn global add @mfe-frameworks/cli

# Go through CLI prompt...
mfe create

# Jump into the created apps' root folder if you haven't already
cd <app-name>

# Publishes to Firestore
mfe publish

# Installs app on the default tenant: glowing-fiesta
mfe install # it will output a link to a PR with the inclusion of the app on the tenant
```

## Architecture

### Interaction Overview

![Microfrontend Framework](https://raw.githubusercontent.com/micro-frontend-frameworks/docs/main/assets/nbti.svg)
