# 4L LightScribe for Flatpak

## Building

This version uses `extra-data` to fetch the (proprietary-licensed) RPMs as
install-time, so the RPMs do not need to be fetched prior to building.

### Install the build environment

```shell
flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install --user org.freedesktop.Platform//23.08 org.freedesktop.Platform.Compat.i386//23.08 org.freedesktop.Sdk//23.08 org.freedesktop.Sdk.Compat.i386//23.08 org.flatpak.Builder
```

### Build

To build and install in one operation:

```shell
flatpak run org.flatpak.Builder --user --install --force-clean build uk.lukeross.flatpak.lightscribe.yml
```

To build and push to a repository called `repo`:

```shell
flatpak run org.flatpak.Builder --gpg-sign=keyid --repo=repo --force-clean build uk.lukeross.flatpak.lightscribe.yml
```

Building a bundle does not work as bundles currently cannot reference external data; see
[this ticket](https://github.com/flatpak/flatpak/issues/1334) for details and to track the problem.

<!--
To build a bundle:

```shell
# Build
flatpak run org.flatpak.Builder --force-clean build uk.lukeross.flatpak.lightscribe.yml
flatpak build-export export build
flatpak build-bundle export uk.lukeross.flatpak.lightscribe.flatpak uk.lukeross.flatpak.lightscribe

# Install built bundle
flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install --user org.freedesktop.Platform.Compat.i386//23.08
flatpak install --user uk.lukeross.flatpak.lightscribe.flatpak
```
-->

## Running

- You should find a desktop entry for the GUI tool
- Alternatively, run the GUI tool with `flatpak run uk.lukeross.flatpak.lightscribe`
- Run the CLI tool with `flatpak run uk.lukeross.flatpak.lightscribe 4L-cli --help`
- Adjust the contrast with `flatpak run uk.lukeross.flatpak.lightscribe elcu.sh`

## Files

Some files are stored in the Flatpak data directory, and will be configured on first run:

- `/etc/lightscribe.rc` can be edited at `~/.var/app/uk.lukeross.flatpak.lightscribe/config/lightscribe.rc`
- PDF manual, disc templates and borders can be found at `~/.var/app/uk.lukeross.flatpak.lightscribe/data`
