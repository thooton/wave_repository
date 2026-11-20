# Wave's default source

This repository is the built-in package source for [Wave](https://github.com/thooton/wave)
on the Sonim XP3800. If you need to add it manually, enter:

```text
https://github.com/thooton/wave_repository
```

Only manifests and icons live here. A manifest points to an immutable HTTPS
release asset; Wave verifies the file before installing it. Do not edit
package manifests by hand. The build repositories publish versioned APKs;
a maintainer mirrors the release assets here using Wave’s publishing tool.
Automatic mirroring from CI is optional.

Wave and List are featured once published. The old Sonim `latest` release
replaces files in place, so this repository does not point to it.

To host your own source, see the [format](https://github.com/thooton/wave/blob/master/docs/source-format.md)
and [publishing guide](https://github.com/thooton/wave/blob/master/docs/publishing.md).

## Maintainer setup

Use `master` as the default branch. Restrict direct writes to the maintainers
and publishing identity, and disallow deletion and force pushes. Give the
publishing identity Contents read/write on this repository. Do not require a
pull request or a status check before the publisher's direct commit: the lint
workflow runs **after** the push. Install an explicit bypass for the publisher
if the organization requires pull requests or checks. Do not add any secrets
here for linting: the source and the versioned release assets are public.
