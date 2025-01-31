---
id: getting-started
sidebar_position: 4
title: Getting Started
---

:::caution

Please make sure you've reviewed the various [installation methods](installation) before getting
started here.

:::

Recyclarr requires one or more YAML configuration files in order to work. The main configuration
file, by default, is named `recyclarr.yml` and lives in your [application data directory][appdata],
which varies depending on your chosen platform.

Choose the section below representing your chosen installation method and run those steps if you
want to get started with a minimal configuration file.

<details><summary>
Docker
</summary>

[Installation Instructions](installation/docker.md)

The steps below assume you are using Docker Compose with a service named `recyclarr`. You are
responsible for translating these steps appropriately for other solutions like Docker Swarm,
Kubernetes, raw Docker, etc.

:::danger

Do **not** use `docker exec`. Read more [here](installation/docker.md#docker-exec).

:::

1. Run `docker compose run --rm recyclarr create-config` to create a starter `recyclarr.yml` file in
   the [application data directory][appdata] (for Docker, this will be in `/config/recyclarr.yml`).
1. Open the generated YAML file from the previous step. At a minimum you must update the `base_url`
   and `api_key` properties for each service that you want to use. Use the configuration [reference]
   and [examples] pages to assist you in understanding an editing other parts of the file as you see
   fit.

If you're using [Cron Mode](installation/docker.md#cron-mode), your work ends here. If you want to
verify the behavior by [running manually](installation/docker.md#manual-mode), then you can execute
`docker compose run --rm recyclarr sonarr` and/or `docker compose run --rm recyclarr radarr` as
needed to update those instances using the configuration provided in the previous step.

</details>

<details><summary>
Manual Installation
</summary>

[Installation Instructions](installation/manual-install.md)

1. Run `recyclarr create-config` to create a starter `recyclarr.yml` file in the [application data
   directory][appdata].
1. Open the generated YAML file from the previous step. At a minimum you must update the `base_url`
   and `api_key` properties for each service that you want to use. Use the configuration [reference]
   and [examples] pages to assist you in understanding an editing other parts of the file as you see
   fit.
1. Run `recyclarr sonarr` and/or `recyclarr radarr` as needed to update those instances using the
   configuration provided in the previous step.

</details>

Each subcommand supports printing help on the command line. Simply run `recyclarr --help` for the
main help output and a list of subcommands. You can then see the help for each subcommand by running
`recyclarr [subcommand] --help`, where `[subcommand]` is one of those subcommands (e.g. `sonarr`).
You can also visit the [CLI Reference](/reference/cli-reference.md) page for detailed documentation
as well.

:::tip

If you want to organize your configuration into multiple YAML files, learn about [how YAML files are
loaded](file-structure.md#default-yaml) and look at [examples of how to split your
files](reference/configuration-examples.md)

:::

[appdata]: /file-structure.md#appdata-directory
[reference]: /reference/config-yml-reference.md
[examples]: /reference/configuration-examples.md
