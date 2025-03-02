---
title: Build release notes
description: Release notes for Buildx
keywords: build, buildx, buildkit, release notes
toc_max: 2
---

This page contains information about the new features, improvements, and bug
fixes in [Docker Buildx](https://github.com/docker/buildx){:target="blank" rel="noopener" class=""}.

## 0.11.2

{% include release-date.html date="2023-07-18" %}

The full release note for this release is available
[on GitHub](https://github.com/docker/buildx/releases/tag/v0.11.2){:target="blank" rel="noopener"}.

### Bug fixes and enhancements

- Fix a regression that caused buildx to not read the `KUBECONFIG` path from the instance store.
  [docker/buildx#1941](https://github.com/docker/buildx/pull/1941){:target="blank" rel="noopener"}
- Fix a regression with result handle builds showing up in the build history incorrectly.
  [docker/buildx#1954](https://github.com/docker/buildx/pull/1954){:target="blank" rel="noopener"}

## 0.11.1

{% include release-date.html date="2023-07-05" %}

The full release note for this release is available
[on GitHub](https://github.com/docker/buildx/releases/tag/v0.11.1){:target="blank" rel="noopener"}.

### Bug fixes and enhancements

- Fix a regression for bake where services in profiles would not be loaded.
  [docker/buildx#1903](https://github.com/docker/buildx/pull/1903){:target="blank" rel="noopener"}
- Fix a regression where `--cgroup-parent` option had no effect during build.
  [docker/buildx#1913](https://github.com/docker/buildx/pull/1913){:target="blank" rel="noopener"}
- Fix a regression where valid docker contexts could fail buildx builder name
  validation. [docker/buildx#1879](https://github.com/docker/buildx/pull/1879){:target="blank" rel="noopener"}
- Fix a possible panic when terminal is resized during the build.
  [docker/buildx#1929](https://github.com/docker/buildx/pull/1929){:target="blank" rel="noopener"}

## 0.11.0

{% include release-date.html date="2023-06-13" %}

The full release note for this release is available
[on GitHub](https://github.com/docker/buildx/releases/tag/v0.11.0){:target="blank" rel="noopener"}.

### New

- Bake now supports [matrix builds](../build/bake/reference.md#targetmatrix).
  The new matrix field on `target` lets you create multiple similar targets to
  remove duplication in bake files. [docker/buildx#1690](https://github.com/docker/buildx/pull/1690){:target="blank" rel="noopener"}
- New experimental `--detach` flag for running builds in detached mode.
  [docker/buildx#1296](https://github.com/docker/buildx/pull/1296){:target="blank" rel="noopener"},
  [docker/buildx#1620](https://github.com/docker/buildx/pull/1620){:target="blank" rel="noopener"},
  [docker/buildx#1614](https://github.com/docker/buildx/pull/1614){:target="blank" rel="noopener"},
  [docker/buildx#1737](https://github.com/docker/buildx/pull/1737){:target="blank" rel="noopener"},
  [docker/buildx#1755](https://github.com/docker/buildx/pull/1755){:target="blank" rel="noopener"}
- New experimental [debug monitor mode](https://github.com/docker/buildx/blob/v0.11.0-rc1/docs/guides/debugging.md){:target="blank" rel="noopener"}
  that lets you start a debug session in your builds.
  [docker/buildx#1626](https://github.com/docker/buildx/pull/1626){:target="blank" rel="noopener"},
  [docker/buildx#1640](https://github.com/docker/buildx/pull/1640){:target="blank" rel="noopener"}
- New [`EXPERIMENTAL_BUILDKIT_SOURCE_POLICY` environment variable](./building/env-vars.md#buildkit_experimental_source_policy)
  for applying a BuildKit source policy file.
  [docker/buildx#1628](https://github.com/docker/buildx/pull/1628){:target="blank" rel="noopener"}

### Bug fixes and enhancements

- `--load` now supports loading multi-platform images when the containerd image
  store is enabled.
  [docker/buildx#1813](https://github.com/docker/buildx/pull/1813){:target="blank" rel="noopener"}
- Build progress output now displays the name of the builder being used.
  [docker/buildx#1177](https://github.com/docker/buildx/pull/1177){:target="blank" rel="noopener"}
- Bake now supports detecting `compose.{yml,yaml}` files.
  [docker/buildx#1752](https://github.com/docker/buildx/pull/1752){:target="blank" rel="noopener"}
- Bake now supports new compose build keys `dockerfile_inline` and `additional_contexts`.
  [docker/buildx#1784](https://github.com/docker/buildx/pull/1784){:target="blank" rel="noopener"}
- Bake now supports replace HCL function.
  [docker/buildx#1720](https://github.com/docker/buildx/pull/1720){:target="blank" rel="noopener"}
- Bake now allows merging multiple similar attestation parameters into a single
  parameter to allow overriding with a single global value.
  [docker/buildx#1699](https://github.com/docker/buildx/pull/1699){:target="blank" rel="noopener"}
- Initial support for shell completion.
  [docker/buildx#1727](https://github.com/docker/buildx/pull/1727){:target="blank" rel="noopener"}
- BuildKit versions now correctly display in `buildx ls` and `buildx inspect`
  for builders using the `docker` driver.
  [docker/buildx#1552](https://github.com/docker/buildx/pull/1552){:target="blank" rel="noopener"}
- Display additional builder node details in buildx inspect view.
  [docker/buildx#1440](https://github.com/docker/buildx/pull/1440){:target="blank" rel="noopener"},
  [docker/buildx#1854](https://github.com/docker/buildx/pull/1874){:target="blank" rel="noopener"}
- Builders using the `remote` driver allow using TLS without proving its own
  key/cert (if BuildKit remote is configured to support it)
  [docker/buildx#1693](https://github.com/docker/buildx/pull/1693){:target="blank" rel="noopener"}
- Builders using the `kubernetes` driver support a new `serviceaccount` option,
  which sets the `serviceAccountName` of the Kubernetes pod.
  [docker/buildx#1597](https://github.com/docker/buildx/pull/1597){:target="blank" rel="noopener"}
- Builders using the `kubernetes` driver support the `proxy-url` option in the
  kubeconfig file.
  [docker/buildx#1780](https://github.com/docker/buildx/pull/1780){:target="blank" rel="noopener"}
- Builders using the `kubernetes` are now automatically assigned a node name if
  no name is explicitly provided.
  [docker/buildx#1673](https://github.com/docker/buildx/pull/1673){:target="blank" rel="noopener"}
- Fix invalid path when writing certificates for `docker-container` driver on Windows.
  [docker/buildx#1831](https://github.com/docker/buildx/pull/1831){:target="blank" rel="noopener"}
- Fix bake failure when remote bake file is accessed using SSH.
  [docker/buildx#1711](https://github.com/docker/buildx/pull/1711){:target="blank" rel="noopener"},
  [docker/buildx#1734](https://github.com/docker/buildx/pull/1734){:target="blank" rel="noopener"}
- Fix bake failure when remote bake context is incorrectly resolved.
  [docker/buildx#1783](https://github.com/docker/buildx/pull/1783){:target="blank" rel="noopener"}
- Fix path resolution of `BAKE_CMD_CONTEXT` and `cwd://` paths in bake contexts.
  [docker/buildx#1840](https://github.com/docker/buildx/pull/1840){:target="blank" rel="noopener"}
- Fix mixed OCI and Docker media types when creating images using
  `buildx imagetools create`.
  [docker/buildx#1797](https://github.com/docker/buildx/pull/1797){:target="blank" rel="noopener"}
- Fix mismatched image id between `--iidfile` and `-q`.
  [docker/buildx#1844](https://github.com/docker/buildx/pull/1844){:target="blank" rel="noopener"}
- Fix AWS authentication when mixing static creds and IAM profiles.
  [docker/buildx#1816](https://github.com/docker/buildx/pull/1816){:target="blank" rel="noopener"}

## 0.10.4

{% include release-date.html date="2023-03-06" %}

{% include buildx-v0.10-disclaimer.md %}

### Bug fixes and enhancements

* Add `BUILDX_NO_DEFAULT_ATTESTATIONS` as alternative to `--provenance false`. {% include github_issue.md repo="docker/buildx" number="1645" %}
* Disable dirty Git checkout detection by default for performance. Can be enabled with `BUILDX_GIT_CHECK_DIRTY` opt-in. {% include github_issue.md repo="docker/buildx" number="1650" %}
* Strip credentials from VCS hint URL before sending to BuildKit. {% include github_issue.md repo="docker/buildx" number="1664" %}

## 0.10.3

{% include release-date.html date="2023-02-16" %}

{% include buildx-v0.10-disclaimer.md %}

### Bug fixes and enhancements

* Fix reachable commit and warnings on collecting Git provenance info. {% include github_issue.md repo="docker/buildx" number="1592" %} {% include github_issue.md repo="docker/buildx" number="1634" %}
* Fix a regression where docker context was not being validated. {% include github_issue.md repo="docker/buildx" number="1596" %}
* Fix function resolution with JSON bake definition. {% include github_issue.md repo="docker/buildx" number="1605" %}
* Fix case where original HCL bake diagnostic is discarded. {% include github_issue.md repo="docker/buildx" number="1607" %}
* Fix labels not correctly set with bake and compose file. {% include github_issue.md repo="docker/buildx" number="1631" %}

## 0.10.2

{% include release-date.html date="2023-01-30" %}

{% include buildx-v0.10-disclaimer.md %}

### Bug fixes and enhancements

* Fix preferred platforms order not taken into account in multi-node builds. {% include github_issue.md repo="docker/buildx" number="1561" %}
* Fix possible panic on handling `SOURCE_DATE_EPOCH` environment variable. {% include github_issue.md repo="docker/buildx" number="1564" %}
* Fix possible push error on multi-node manifest merge since BuildKit v0.11 on
  some registries. {% include github_issue.md repo="docker/buildx" number="1566" %}
* Improve warnings on collecting Git provenance info. {% include github_issue.md repo="docker/buildx" number="1568" %}

## 0.10.1

{% include release-date.html date="2023-01-27" %}

{% include buildx-v0.10-disclaimer.md %}

### Bug fixes and enhancements

* Fix sending the correct origin URL as `vsc:source` metadata. {% include github_issue.md repo="docker/buildx" number="1548" %}
* Fix possible panic from data-race. {% include github_issue.md repo="docker/buildx" number="1504" %}
* Fix regression with `rm --all-inactive`. {% include github_issue.md repo="docker/buildx" number="1547" %}
* Improve attestation access in `imagetools inspect` by lazily loading data. {% include github_issue.md repo="docker/buildx" number="1546" %}
* Correctly mark capabilities request as internal. {% include github_issue.md repo="docker/buildx" number="1538" %}
* Detect invalid attestation configuration. {% include github_issue.md repo="docker/buildx" number="1545" %}
* Update containerd patches to fix possible push regression affecting
  `imagetools` commands. {% include github_issue.md repo="docker/buildx" number="1559" %}

## 0.10.0

{% include release-date.html date="2023-01-10" %}

{% include buildx-v0.10-disclaimer.md %}

### New

* The `buildx build` command supports new `--attest` flag, along with
  shorthands `--sbom` and `--provenance`, for adding attestations for your
  current build. {% include github_issue.md repo="docker/buildx" number="1412" %}
  {% include github_issue.md repo="docker/buildx" number="1475" %}
    * `--attest type=sbom` or `--sbom=true` adds [SBOM attestations](attestations/sbom.md).
    * `--attest type=provenance` or `--provenance=true` adds [SLSA provenance attestation](attestations/slsa-provenance.md)
    * When creating OCI images, a minimal provenance attestation is included
      with the image by default.
* When building with BuildKit that supports provenance attestations Buildx will
  automatically share the version control information of your build context, so
  it can be shown in provenance for later debugging. Previously this only
  happened when building from a Git URL directly. To opt-out of this behavior
  you can set `BUILDX_GIT_INFO=0`. Optionally you can also automatically define
  labels with VCS info by setting `BUILDX_GIT_LABELS=1`. {% include github_issue.md repo="docker/buildx" number="1462" %}
  {% include github_issue.md repo="docker/buildx" number="1297" %} {% include github_issue.md repo="docker/buildx" number="1341" %}
  {% include github_issue.md repo="docker/buildx" number="1468" %} {% include github_issue.md repo="docker/buildx" number="1477" %}
* Named contexts with `--build-context` now support `oci-layout://` protocol
  for initializing the context with a value of a local OCI layout directory.
  E.g. `--build-context stagename=oci-layout://path/to/dir`. This feature
  requires BuildKit v0.11.0+ and Dockerfile 1.5.0+. {% include github_issue.md repo="docker/buildx" number="1456" %}
* Bake now supports [resource interpolation](bake/configuring-build.md#resource-interpolation)
  where you can reuse the values from other target definitions. {% include github_issue.md repo="docker/buildx" number="1434" %}
* Buildx will now automatically forward `SOURCE_DATE_EPOCH` environment variable
  if it is defined in your environment. This feature is meant to be used with 
  updated [reproducible builds](https://github.com/moby/buildkit/blob/master/docs/build-repro.md){:target="blank" rel="noopener" class=""}
  support in BuildKit v0.11.0+. {% include github_issue.md repo="docker/buildx" number="1482" %}
* Buildx now remembers the last activity for a builder for better organization
  of builder instances. {% include github_issue.md repo="docker/buildx" number="1439" %}
* Bake definition now supports null values for [variables](bake/reference.md#variable) and [labels](bake/reference.md#targetlabels)
  for build arguments and labels to use the defaults set in the Dockerfile {% include github_issue.md repo="docker/buildx" number="1449" %}
* The [`buildx imagetools inspect` command](../engine/reference/commandline/buildx_imagetools_inspect.md)
  now supports showing SBOM and Provenance data {% include github_issue.md repo="docker/buildx" number="1444" %}
  {% include github_issue.md repo="docker/buildx" number="1498" %}
* Increase performance of `ls` command and inspect flows {% include github_issue.md repo="docker/buildx" number="1430" %}
  {% include github_issue.md repo="docker/buildx" number="1454" %} {% include github_issue.md repo="docker/buildx" number="1455" %} 
  {% include github_issue.md repo="docker/buildx" number="1345" %}
* Adding extra hosts with [Docker driver](drivers/docker.md) now supports
  Docker-specific `host-gateway` special value {% include github_issue.md repo="docker/buildx" number="1446" %}
* [OCI exporter](exporters/oci-docker.md) now supports `tar=false` option for
  exporting OCI format directly in a directory {% include github_issue.md repo="docker/buildx" number="1420" %}

### Upgrades

* Updated the Compose Specification to 1.6.0 {% include github_issue.md repo="docker/buildx" number="1387" %}

### Bug fixes and enhancements

* `--invoke` can now load default launch environment from the image metadata {% include github_issue.md repo="docker/buildx" number="1324" %}
* Fix container driver behavior in regards to UserNS {% include github_issue.md repo="docker/buildx" number="1368" %}
* Fix possible panic in Bake when using wrong variable value type {% include github_issue.md repo="docker/buildx" number="1442" %}
* Fix possible panic in `imagetools inspect` {% include github_issue.md repo="docker/buildx" number="1441" %}
  {% include github_issue.md repo="docker/buildx" number="1406" %}
* Fix sending empty `--add-host` value to BuildKit by default {% include github_issue.md repo="docker/buildx" number="1457" %}
* Fix handling progress prefixes with progress groups {% include github_issue.md repo="docker/buildx" number="1305" %}
* Fix recursively resolving groups in Bake {% include github_issue.md repo="docker/buildx" number="1313" %}
* Fix possible wrong indentation on multi-node builder manifests {% include github_issue.md repo="docker/buildx" number="1396" %}
* Fix possible panic from missing OpenTelemetry configuration {% include github_issue.md repo="docker/buildx" number="1383" %}
* Fix `--progress=tty` behavior when TTY is not available {% include github_issue.md repo="docker/buildx" number="1371" %}
* Fix connection error conditions in `prune` and `du` commands {% include github_issue.md repo="docker/buildx" number="1307" %}

## 0.9.1

{% include release-date.html date="2022-08-18" %} 

### Bug fixes and enhancements

* The `inspect` command now displays the BuildKit version in use {% include github_issue.md repo="docker/buildx" number="1279" %}
* Fixed a regression when building Compose files that contain services without a
  build block {% include github_issue.md repo="docker/buildx" number="1277" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.9.1){:target="blank" rel="noopener" class=""}.

## 0.9.0

{% include release-date.html date="2022-08-17" %} 

### New 

* Support for new [driver `remote`](drivers/remote.md) that you can use
  to connect to any already running BuildKit instance {% include github_issue.md repo="docker/buildx" number="1078" %}
  {% include github_issue.md repo="docker/buildx" number="1093" %} {% include github_issue.md repo="docker/buildx" number="1094" %}
  {% include github_issue.md repo="docker/buildx" number="1103" %} {% include github_issue.md repo="docker/buildx" number="1134" %}
  {% include github_issue.md repo="docker/buildx" number="1204" %}
* You can now load Dockerfile from standard input even when the build context is
  coming from external Git or HTTP URL {% include github_issue.md repo="docker/buildx" number="994" %}
* Build commands now support new the build context type `oci-layout://` for loading
  [build context from local OCI layout directories](../engine/reference/commandline/buildx_build.md#source-oci-layout).
  Note that this feature depends on an unreleased BuildKit feature and builder
  instance from `moby/buildkit:master` needs to be used until BuildKit v0.11 is
  released {% include github_issue.md repo="docker/buildx" number="1173" %}
* You can now use the new `--print` flag to run helper functions supported by the
  BuildKit frontend performing the build and print their results. You can use
  this feature in Dockerfile to show the build arguments and secrets that the
  current build supports with `--print=outline` and list all available
  Dockerfile stages with `--print=targets`. This feature is experimental for
  gathering early feedback and requires enabling `BUILDX_EXPERIMENTAL=1`
  environment variable. We plan to update/extend this feature in the future
  without keeping backward compatibility {% include github_issue.md repo="docker/buildx" number="1100" %}
  {% include github_issue.md repo="docker/buildx" number="1272" %}
* You can now use the new `--invoke` flag to launch interactive containers from
  build results for an interactive debugging cycle. You can reload these
  containers with code changes or restore them to an initial state from the
  special monitor mode. This feature is experimental for gathering early
  feedback and requires enabling `BUILDX_EXPERIMENTAL=1` environment variable.
  We plan to update/extend this feature in the future without enabling backward
  compatibility {% include github_issue.md repo="docker/buildx" number="1168" %}
  {% include github_issue.md repo="docker/buildx" number="1257" %} {% include github_issue.md repo="docker/buildx" number="1259" %}
* Buildx now understands environment variable `BUILDKIT_COLORS` and `NO_COLOR`
  to customize/disable the colors of interactive build progressbar {% include github_issue.md repo="docker/buildx" number="1230" %}
  {% include github_issue.md repo="docker/buildx" number="1226" %}
* `buildx ls` command now shows the current BuildKit version of each builder
  instance {% include github_issue.md repo="docker/buildx" number="998" %}
* The `bake` command now loads `.env` file automatically when building Compose
  files for compatibility {% include github_issue.md repo="docker/buildx" number="1261" %}
* Bake now supports Compose files with `cache_to` definition {% include github_issue.md repo="docker/buildx" number="1155" %}
* Bake now supports new builtin function `timestamp()` to access current time {% include github_issue.md repo="docker/buildx" number="1214" %}
* Bake now supports Compose build secrets definition {% include github_issue.md repo="docker/buildx" number="1069" %}
* Additional build context configuration is now supported in Compose files via `x-bake` {% include github_issue.md repo="docker/buildx" number="1256" %}
* Inspecting builder now shows current driver options configuration {% include github_issue.md repo="docker/buildx" number="1003" %}
  {% include github_issue.md repo="docker/buildx" number="1066" %}

### Updates

* Updated the Compose Specification to 1.4.0 {% include github_issue.md repo="docker/buildx" number="1246" %}
  {% include github_issue.md repo="docker/buildx" number="1251" %}

### Bug fixes and enhancements

* The `buildx ls` command output has been updated with better access to errors
  from different builders {% include github_issue.md repo="docker/buildx" number="1109" %}
* The `buildx create` command now performs additional validation of builder parameters
  to avoid creating a builder instance with invalid configuration {% include github_issue.md repo="docker/buildx" number="1206" %}
* The `buildx imagetools create` command can now create new multi-platform images
  even if the source subimages are located on different repositories or
  registries {% include github_issue.md repo="docker/buildx" number="1137" %}
* You can now set the default builder config that is used when creating
  builder instances without passing custom `--config` value {% include github_issue.md repo="docker/buildx" number="1111" %}
* Docker driver can now detect if `dockerd` instance supports initially
  disabled Buildkit features like multi-platform images {% include github_issue.md repo="docker/buildx" number="1260" %}
  {% include github_issue.md repo="docker/buildx" number="1262" %}
* Compose files using targets with `.` in the name are now converted to use `_`
  so the selector keys can still be used in such targets {% include github_issue.md repo="docker/buildx" number="1011" %}
* Included an additional validation for checking valid driver configurations {% include github_issue.md repo="docker/buildx" number="1188" %}
  {% include github_issue.md repo="docker/buildx" number="1273" %}
* The `remove` command now displays the removed builder and forbids removing
  context builders {% include github_issue.md repo="docker/buildx" number="1128" %}
* Enable Azure authentication when using Kubernetes driver {% include github_issue.md repo="docker/buildx" number="974" %}
* Add tolerations handling for kubernetes driver {% include github_issue.md repo="docker/buildx" number="1045" %}
  {% include github_issue.md repo="docker/buildx" number="1053" %}
* Replace deprecated seccomp annotations with `securityContext` in kubernetes
  driver {% include github_issue.md repo="docker/buildx" number="1052" %}
* Fix panic on handling manifests with nil platform {% include github_issue.md repo="docker/buildx" number="1144" %}
* Fix using duration filter with `prune` command {% include github_issue.md repo="docker/buildx" number="1252" %}
* Fix merging multiple JSON files on Bake definition {% include github_issue.md repo="docker/buildx" number="1025" %}
* Fix issues with implicit builder created from Docker context had invalid
  configuration or dropped connection {% include github_issue.md repo="docker/buildx" number="1129" %}
* Fix conditions for showing no-output warning when using named contexts {% include github_issue.md repo="docker/buildx" number="968" %}
* Fix duplicating builders when builder instance and docker context have the
  same name {% include github_issue.md repo="docker/buildx" number="1131" %}
* Fix printing unnecessary SSH warning logs {% include github_issue.md repo="docker/buildx" number="1085" %}
* Fix possible panic when using an empty variable block with Bake JSON
  definition {% include github_issue.md repo="docker/buildx" number="1080" %}
* Fix image tools commands not handling `--builder` flag correctly {% include github_issue.md repo="docker/buildx" number="1067" %}
* Fix using custom image together with rootless option {% include github_issue.md repo="docker/buildx" number="1063" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.9.0){:target="blank" rel="noopener" class=""}.

## 0.8.2

{% include release-date.html date="2022-04-04" %} 

### Updates
* Update Compose spec used by `buildx bake` to v1.2.1 to fix parsing ports definition {% include github_issue.md repo="docker/buildx" number="1033" %}

### Bug fixes and enhancements
* Fix possible crash on handling progress streams from BuildKit v0.10 {% include github_issue.md repo="docker/buildx" number="1042" %}
* Fix parsing groups in `buildx bake` when already loaded by a parent group {% include github_issue.md repo="docker/buildx" number="1021" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.8.2){:target="blank" rel="noopener" class=""}.

## 0.8.1

{% include release-date.html date="2022-03-21" %}

### Bug fixes and enhancements

* Fix possible panic on handling build context scanning errors {% include github_issue.md repo="docker/buildx" number="1005" %}
* Allow `.` on Compose target names in `buildx bake` for backward compatibility {% include github_issue.md repo="docker/buildx" number="1018" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.8.1){:target="blank" rel="noopener" class=""}.

## 0.8.0

{% include release-date.html date="2022-03-09" %}

### New

* Build command now accepts `--build-context` flag to [define additional named build contexts](/engine/reference/commandline/buildx_build/#build-context)
  for your builds {% include github_issue.md repo="docker/buildx" number="904" %}
* Bake definitions now support [defining dependencies between targets](bake/build-contexts.md)
  and using the result of one target in another build {% include github_issue.md repo="docker/buildx" number="928" %}
  {% include github_issue.md repo="docker/buildx" number="965" %} {% include github_issue.md repo="docker/buildx" number="963" %}
  {% include github_issue.md repo="docker/buildx" number="962" %} {% include github_issue.md repo="docker/buildx" number="981" %}
* `imagetools inspect` now accepts `--format` flag allowing access to config
  and buildinfo for specific images {% include github_issue.md repo="docker/buildx" number="854" %}
  {% include github_issue.md repo="docker/buildx" number="972" %}
* New flag `--no-cache-filter` allows configuring build, so it ignores cache
  only for specified Dockerfile stages {% include github_issue.md repo="docker/buildx" number="860" %}
* Builds can now show a summary of warnings sets by the building frontend {% include github_issue.md repo="docker/buildx" number="892" %}
* The new build argument `BUILDKIT_INLINE_BUILDINFO_ATTRS` allows opting-in to embed
  building attributes to resulting image {% include github_issue.md repo="docker/buildx" number="908" %}
* The new flag `--keep-buildkitd` allows keeping BuildKit daemon running when removing a builder
  * {% include github_issue.md repo="docker/buildx" number="852" %}

### Bug fixes and enhancements

* `--metadata-file` output now supports embedded structure types {% include github_issue.md repo="docker/buildx" number="946" %}
* `buildx rm` now accepts new flag `--all-inactive` for removing all builders
  that are not currently running {% include github_issue.md repo="docker/buildx" number="885" %}
* Proxy config is now read from Docker configuration file and sent with build
  requests for backward compatibility {% include github_issue.md repo="docker/buildx" number="959" %}
* Support host networking in Compose {% include github_issue.md repo="docker/buildx" number="905" %}
  {% include github_issue.md repo="docker/buildx" number="880" %}
* Bake files can now be read from stdin with `-f -` {% include github_issue.md repo="docker/buildx" number="864" %}
* `--iidfile` now always writes the image config digest independently of the
  driver being used (use `--metadata-file` for digest) {% include github_issue.md repo="docker/buildx" number="980" %}
* Target names in Bake are now restricted to not use special characters {% include github_issue.md repo="docker/buildx" number="929" %}
* Image manifest digest can be read from metadata when pushed with `docker`
  driver {% include github_issue.md repo="docker/buildx" number="989" %}
* Fix environment file handling in Compose files {% include github_issue.md repo="docker/buildx" number="905" %}
* Show last access time in `du` command {% include github_issue.md repo="docker/buildx" number="867" %}
* Fix possible double output logs when multiple Bake targets run same build
  steps {% include github_issue.md repo="docker/buildx" number="977" %}
* Fix possible errors on multi-node builder building multiple targets with
  mixed platform {% include github_issue.md repo="docker/buildx" number="985" %}
* Fix some nested inheritance cases in Bake {% include github_issue.md repo="docker/buildx" number="914" %}
* Fix printing default group on Bake files {% include github_issue.md repo="docker/buildx" number="884" %}
* Fix `UsernsMode` when using rootless container {% include github_issue.md repo="docker/buildx" number="887" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.8.0){:target="blank" rel="noopener" class=""}.

## 0.7.1

{% include release-date.html date="2021-08-25" %}

### Fixes

* Fix issue with matching exclude rules in `.dockerignore` {% include github_issue.md repo="docker/buildx" number="858" %}
* Fix `bake --print` JSON output for current group {% include github_issue.md repo="docker/buildx" number="857" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.7.1){:target="blank" rel="noopener" class=""}.

## 0.7.0

{% include release-date.html date="2021-11-10" %}

### New features

* TLS certificates from BuildKit configuration are now transferred to build
  container with `docker-container` and `kubernetes` drivers {% include github_issue.md repo="docker/buildx" number="787" %}
* Builds support `--ulimit` flag for feature parity {% include github_issue.md repo="docker/buildx" number="800" %}
* Builds support `--shm-size` flag for feature parity {% include github_issue.md repo="docker/buildx" number="790" %}
* Builds support `--quiet` for feature parity {% include github_issue.md repo="docker/buildx" number="740" %}
* Builds support `--cgroup-parent` flag for feature parity {% include github_issue.md repo="docker/buildx" number="814" %}
* Bake supports builtin variable `BAKE_LOCAL_PLATFORM` {% include github_issue.md repo="docker/buildx" number="748" %}
* Bake supports `x-bake` extension field in Compose files {% include github_issue.md repo="docker/buildx" number="721" %}
* `kubernetes` driver now supports colon-separated `KUBECONFIG` {% include github_issue.md repo="docker/buildx" number="761" %}
* `kubernetes` driver now supports setting Buildkit config file with `--config` {% include github_issue.md repo="docker/buildx" number="682" %}
* `kubernetes` driver now supports installing QEMU emulators with driver-opt {% include github_issue.md repo="docker/buildx" number="682" %}

### Enhancements

* Allow using custom registry configuration for multi-node pushes from the
  client {% include github_issue.md repo="docker/buildx" number="825" %}
* Allow using custom registry configuration for `buildx imagetools` command {% include github_issue.md repo="docker/buildx" number="825" %}
* Allow booting builder after creating with `buildx create --bootstrap` {% include github_issue.md repo="docker/buildx" number="692" %}
* Allow `registry:insecure` output option for multi-node pushes {% include github_issue.md repo="docker/buildx" number="825" %}
* BuildKit config and TLS files are now kept in Buildx state directory and
  reused if BuildKit instance needs to be recreated {% include github_issue.md repo="docker/buildx" number="824" %}
* Ensure different projects use separate destination directories for
  incremental context transfer for better performance {% include github_issue.md repo="docker/buildx" number="817" %}
* Build containers are now placed on separate cgroup by default {% include github_issue.md repo="docker/buildx" number="782" %}
* Bake now prints the default group with `--print` {% include github_issue.md repo="docker/buildx" number="720" %}
* `docker` driver now dials build session over HTTP for better performance {% include github_issue.md repo="docker/buildx" number="804" %}

### Fixes

* Fix using `--iidfile` together with a multi-node push {% include github_issue.md repo="docker/buildx" number="826" %}
* Using `--push` in Bake does not clear other image export options in the file {% include github_issue.md repo="docker/buildx" number="773" %}
* Fix Git URL detection for `buildx bake` when `https` protocol was used {% include github_issue.md repo="docker/buildx" number="822" %}
* Fix pushing image with multiple names on multi-node builds {% include github_issue.md repo="docker/buildx" number="815" %}
* Avoid showing `--builder` flags for commands that don't use it {% include github_issue.md repo="docker/buildx" number="818" %}
* Unsupported build flags now show a warning {% include github_issue.md repo="docker/buildx" number="810" %}
* Fix reporting error details in some OpenTelemetry traces {% include github_issue.md repo="docker/buildx" number="812" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.7.0){:target="blank" rel="noopener" class=""}.

## 0.6.3

{% include release-date.html date="2021-08-30" %}

### Fixes

* Fix BuildKit state volume location for Windows clients {% include github_issue.md repo="docker/buildx" number="751" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.6.3){:target="blank" rel="noopener" class=""}.

## 0.6.2

{% include release-date.html date="2021-08-21" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.6.2){:target="blank" rel="noopener" class=""}.

### Fixes

* Fix connection error showing up in some SSH configurations {% include github_issue.md repo="docker/buildx" number="741" %}

## 0.6.1

{% include release-date.html date="2021-07-30" %}

### Enhancements

* Set `ConfigFile` to parse compose files with Bake {% include github_issue.md repo="docker/buildx" number="704" %}

### Fixes

* Duplicate progress env var {% include github_issue.md repo="docker/buildx" number="693" %}
* Should ignore nil client {% include github_issue.md repo="docker/buildx" number="686" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.6.1){:target="blank" rel="noopener" class=""}.

## 0.6.0

{% include release-date.html date="2021-07-16" %}

### New features

* Support for OpenTelemetry traces and forwarding Buildx client traces to
  BuildKit {% include github_issue.md repo="docker/buildx" number="635" %}
* Experimental GitHub Actions remote cache backend with `--cache-to type=gha`
  and `--cache-from type=gha` {% include github_issue.md repo="docker/buildx" number="535" %}
* New `--metadata-file` flag has been added to build and Bake command that
  allows saving build result metadata in JSON format {% include github_issue.md repo="docker/buildx" number="605" %}
* This is the first release supporting Windows ARM64 {% include github_issue.md repo="docker/buildx" number="654" %}
* This is the first release supporting Linux Risc-V {% include github_issue.md repo="docker/buildx" number="652" %}
* Bake now supports building from remote definition with local files or
  another remote source as context {% include github_issue.md repo="docker/buildx" number="671" %}
* Bake now allows variables to reference each other and using user functions
  in variables and vice-versa {% include github_issue.md repo="docker/buildx" number="575" %}
  {% include github_issue.md repo="docker/buildx" number="539" %} {% include github_issue.md repo="docker/buildx" number="532" %}
* Bake allows defining attributes in the global scope {% include github_issue.md repo="docker/buildx" number="541" %}
* Bake allows variables across multiple files {% include github_issue.md repo="docker/buildx" number="538" %}
* New quiet mode has been added to progress printer {% include github_issue.md repo="docker/buildx" number="558" %}
* `kubernetes` driver now supports defining resources/limits {% include github_issue.md repo="docker/buildx" number="618" %}
* Buildx binaries can now be accessed through [buildx-bin](https://hub.docker.com/r/docker/buildx-bin){:target="blank" rel="noopener" class=""}
  Docker image {% include github_issue.md repo="docker/buildx" number="656" %}

### Enhancements

* `docker-container` driver now keeps BuildKit state in volume. Enabling
  updates with keeping state {% include github_issue.md repo="docker/buildx" number="672" %}
* Compose parser is now based on new [compose-go parser](https://github.com/compose-spec/compose-go)
  fixing support for some newer syntax {% include github_issue.md repo="docker/buildx" number="669" %}
* SSH socket is now automatically forwarded when building an ssh-based git URL {% include github_issue.md repo="docker/buildx" number="581" %}
* Bake HCL parser has been rewritten {% include github_issue.md repo="docker/buildx" number="645" %}
* Extend HCL support with more functions {% include github_issue.md repo="docker/buildx" number="491" %}
  {% include github_issue.md repo="docker/buildx" number="503" %}
* Allow secrets from environment variables {% include github_issue.md repo="docker/buildx" number="488" %}
* Builds with an unsupported multi-platform and load configuration now fail fast {% include github_issue.md repo="docker/buildx" number="582" %}
* Store Kubernetes config file to make buildx builder switchable {% include github_issue.md repo="docker/buildx" number="497" %}
* Kubernetes now lists all pods as nodes on inspection {% include github_issue.md repo="docker/buildx" number="477" %}
* Default Rootless image has been set to `moby/buildkit:buildx-stable-1-rootless` {% include github_issue.md repo="docker/buildx" number="480" %}

### Fixes

* `imagetools create` command now correctly merges JSON descriptor with old one {% include github_issue.md repo="docker/buildx" number="592" %}
* Fix building with `--network=none` not requiring extra security entitlements {% include github_issue.md repo="docker/buildx" number="531" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.6.0){:target="blank" rel="noopener" class=""}.

## 0.5.1

{% include release-date.html date="2020-12-15" %}

### Fixes

* Fix regression on setting `--platform` on `buildx create` outside
  `kubernetes` driver {% include github_issue.md repo="docker/buildx" number="475" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.5.1){:target="blank" rel="noopener" class=""}.

## 0.5.0

{% include release-date.html date="2020-12-15" %}

### New features

* The `docker` driver now supports the `--push` flag {% include github_issue.md repo="docker/buildx" number="442" %}
* Bake supports inline Dockerfiles {% include github_issue.md repo="docker/buildx" number="398" %}
* Bake supports building from remote URLs and Git repositories {% include github_issue.md repo="docker/buildx" number="398" %}
* `BUILDX_CONFIG` env var allow users to have separate buildx state from
  Docker config {% include github_issue.md repo="docker/buildx" number="385" %}
* `BUILDKIT_MULTI_PLATFORM` build arg allows to force building multi-platform
  return objects even if only one `--platform` specified {% include github_issue.md repo="docker/buildx" number="467" %}

### Enhancements

* Allow `--append` to be used with `kubernetes` driver {% include github_issue.md repo="docker/buildx" number="370" %}
* Build errors show error location in source files and system stacktraces
  with `--debug` {% include github_issue.md repo="docker/buildx" number="389" %}
* Bake formats HCL errors with source definition {% include github_issue.md repo="docker/buildx" number="391" %}
* Bake allows empty string values in arrays that will be discarded {% include github_issue.md repo="docker/buildx" number="428" %}
* You can now use the Kubernetes cluster config with the `kubernetes` driver {% include github_issue.md repo="docker/buildx" number="368" %}
  {% include github_issue.md repo="docker/buildx" number="460" %}
* Creates a temporary token for pulling images instead of sharing credentials
  when possible {% include github_issue.md repo="docker/buildx" number="469" %}
* Ensure credentials are passed when pulling BuildKit container image {% include github_issue.md repo="docker/buildx" number="441" %}
  {% include github_issue.md repo="docker/buildx" number="433" %}
* Disable user namespace remapping in `docker-container` driver {% include github_issue.md repo="docker/buildx" number="462" %}
* Allow `--builder` flag to switch to default instance {% include github_issue.md repo="docker/buildx" number="425" %}
* Avoid warn on empty `BUILDX_NO_DEFAULT_LOAD` config value {% include github_issue.md repo="docker/buildx" number="390" %}
* Replace error generated by `quiet` option by a warning {% include github_issue.md repo="docker/buildx" number="403" %}
* CI has been switched to GitHub Actions {% include github_issue.md repo="docker/buildx" number="451" %}
  {% include github_issue.md repo="docker/buildx" number="463" %} {% include github_issue.md repo="docker/buildx" number="466" %}
  {% include github_issue.md repo="docker/buildx" number="468" %} {% include github_issue.md repo="docker/buildx" number="471" %}

### Fixes

* Handle lowercase Dockerfile name as a fallback for backward compatibility {% include github_issue.md repo="docker/buildx" number="444" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.5.0){:target="blank" rel="noopener" class=""}.

## 0.4.2

{% include release-date.html date="2020-08-22" %}

### New features

* Support `cacheonly` exporter {% include github_issue.md repo="docker/buildx" number="337" %}

### Enhancements

* Update `go-cty` to pull in more `stdlib` functions {% include github_issue.md repo="docker/buildx" number="277" %}
* Improve error checking on load {% include github_issue.md repo="docker/buildx" number="281" %}

### Fixes

* Fix parsing json config with HCL {% include github_issue.md repo="docker/buildx" number="280" %}
* Ensure `--builder` is wired from root options {% include github_issue.md repo="docker/buildx" number="321" %}
* Remove warning for multi-platform iidfile {% include github_issue.md repo="docker/buildx" number="351" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.4.2){:target="blank" rel="noopener" class=""}.

## 0.4.1

{% include release-date.html date="2020-05-01" %}

### Fixes

* Fix regression on flag parsing {% include github_issue.md repo="docker/buildx" number="268" %}
* Fix using pull and no-cache keys in HCL targets {% include github_issue.md repo="docker/buildx" number="268" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.4.1){:target="blank" rel="noopener" class=""}.

## 0.4.0

{% include release-date.html date="2020-04-30" %}

### New features

* Add `kubernetes` driver {% include github_issue.md repo="docker/buildx" number="167" %}
* New global `--builder` flag to override builder instance for a single command {% include github_issue.md repo="docker/buildx" number="246" %}
* New `prune` and `du` commands for managing local builder cache {% include github_issue.md repo="docker/buildx" number="249" %}
* You can now set the new `pull` and `no-cache` options for HCL targets {% include github_issue.md repo="docker/buildx" number="165" %}

### Enhancements

* Upgrade Bake to HCL2 with support for variables and functions {% include github_issue.md repo="docker/buildx" number="192" %}
* Bake now supports `--load` and `--push` {% include github_issue.md repo="docker/buildx" number="164" %}
* Bake now supports wildcard overrides for multiple targets {% include github_issue.md repo="docker/buildx" number="164" %}
* Container driver allows setting environment variables via `driver-opt` {% include github_issue.md repo="docker/buildx" number="170" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.4.0){:target="blank" rel="noopener" class=""}.

## 0.3.1

{% include release-date.html date="2019-09-27" %}

### Enhancements

* Handle copying unix sockets instead of erroring {% include github_issue.md repo="docker/buildx" number="155" %}
  {% include github_issue.md repo="moby/buildkit" number="1144" %}

### Fixes

* Running Bake with multiple Compose files now merges targets correctly {% include github_issue.md repo="docker/buildx" number="134" %} 
* Fix bug when building a Dockerfile from stdin (`build -f -`) {% include github_issue.md repo="docker/buildx" number="153" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.3.1){:target="blank" rel="noopener" class=""}.

## 0.3.0

{% include release-date.html date="2019-08-02" %}

### New features

* Custom `buildkitd` daemon flags {% include github_issue.md repo="docker/buildx" number="102" %}
* Driver-specific options on `create` {% include github_issue.md repo="docker/buildx" number="122" %}

### Enhancements

* Environment variables are used in Compose files {% include github_issue.md repo="docker/buildx" number="117" %}
* Bake now honors `--no-cache` and `--pull` {% include github_issue.md repo="docker/buildx" number="118" %}
* Custom BuildKit config file {% include github_issue.md repo="docker/buildx" number="121" %}
* Entitlements support with `build --allow` {% include github_issue.md repo="docker/buildx" number="104" %}

### Fixes

* Fix bug where `--build-arg foo` would not read `foo` from environment {% include github_issue.md repo="docker/buildx" number="116" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.3.0){:target="blank" rel="noopener" class=""}.

## 0.2.2

{% include release-date.html date="2019-05-30" %}

### Enhancements

* Change Compose file handling to require valid service specifications {% include github_issue.md repo="docker/buildx" number="87" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.2.2){:target="blank" rel="noopener" class=""}.

## 0.2.1

{% include release-date.html date="2019-05-25" %}

### New features

* Add `BUILDKIT_PROGRESS` env var {% include github_issue.md repo="docker/buildx" number="69" %}
* Add `local` platform {% include github_issue.md repo="docker/buildx" number="70" %}

### Enhancements

* Keep arm variant if one is defined in the config {% include github_issue.md repo="docker/buildx" number="68" %}
* Make dockerfile relative to context {% include github_issue.md repo="docker/buildx" number="83" %}

### Fixes

* Fix parsing target from compose files {% include github_issue.md repo="docker/buildx" number="53" %}

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.2.1){:target="blank" rel="noopener" class=""}.

## 0.2.0

{% include release-date.html date="2019-04-25" %}

### New features

* First release

For more details, see the complete release notes in the [Buildx GitHub repository](https://github.com/docker/buildx/releases/tag/v0.2.0){:target="blank" rel="noopener" class=""}.
