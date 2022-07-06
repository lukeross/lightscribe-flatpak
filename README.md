# 4L LightScribe for Flatpak

## Building

This version uses `extra-data` to fetch the (proprietary-licensed) RPMs as
install-time, so the RPMs do not need to be fetched prior to building.

### Install the build environment

```
flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install --user org.freedesktop.Platform//21.08 org.freedesktop.Platform.Compat.i386//21.08 org.freedesktop.Sdk//21.08 org.freedesktop.Sdk.Compat.i386//21.08 org.flatpak.Builder
```

### Build

To build and install in one operation:

```
flatpak-builder --user --install --force-clean build uk.lukeross.flatpak.lightscribe.yml
```

To build and push to a repository called `repo`:

```
flatpak-builder --gpg-sign=keyid --repo=repo --force-clean build uk.lukeross.flatpak.lightscribe.yml
```

## Running

- You should find a desktop entry for the GUI tool
- Alternatively, run the GUI tool with `flatpak run uk.lukeross.flatpak.lightscribe`
- Run the CLI tool with `flatpak run uk.lukeross.flatpak.lightscribe 4L-cli --help`
- Adjust the contrast with `flatpak run uk.lukeross.flatpak.lightscribe elcu.sh`

## Files

Some files are stored in the Flatpak data directory, and will be configured on first run:

- `/etc/lightscribe.rc` can be edited at `~/.var/app/uk.lukeross.flatpak.lightscribe/config/lightscribe.rc`
- PDF manual, disc templates and borders can be found at `~/.var/app/uk.lukeross.flatpak.lightscribe/data`
