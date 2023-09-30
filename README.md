# Some handy Renovate templates

I found myself using the same configs for [Renovate](https://github.com/renovatebot/renovate) across multiple projects, so thought I'd bring them together.

A project can reference a github-hosted template with the `extends` keyword. For example:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>growse/renovate-template",
    "github>growse/renovate-template:automerge-minor-and-patch",
    "github>growse/renovate-template:automerge-github-actions"
  ]
}
```

## Default template

`"github>growse/renovate-template"`

Generic policy applied to all my projects. Probably not useful for others:

* Disables issue dashboard (I don't find it useful)
* Disables rate limiting
* Rebase's PRs
* Assigns me to the PR
* Does lockfile maintenance with automerge

## Automerge github actions

`"github>growse/renovate-template:automerge-github-actions"`

Auto-merges github actions after a cooling-off period of 7 days.

## Auto-merge Minor & Patch

`"github>growse/renovate-template:automerge-minor-and-patch"`

Auto-merges minor and patch updates, as well as pinning and digest updates.

## Docker env

`"github>growse/renovate-template:docker-env"`

Provides the ability to auto-bump versions in Dockerfiles by annotating an Dockerfile `ENV` with a specific comment. E.g.

```Dockerfile
# renovate: datasource=github-releases depName=mydep/my-dependency
ENV MYDEPENDENCY_VERSION=v1.2.3
```

Will bump the value of this variable using Github Releases as a data source, looking at the `mydep/my-dependency` repository

## Makefile version

`"github>growse/renovate-template:makefile-version"`

A bit like `docker-env`, but uses variables in makefiles.

```Makefile
# renovate: datasource=github-releases depName=mydep/my-dependency
MYDEPENDENCY_VERSION := v1.2.3
```
