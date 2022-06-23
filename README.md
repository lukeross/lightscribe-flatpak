# 4L LightScribe for Flatpak

## Building

### Copy the LightScribe RPMs into the working directory

- `4L-1.0-r6.i586.rpm`
- `lightscribeApplications-1.18.15.1-linux-2.6-intel.rpm`
- `lightscribe-1.18.27.10-linux-2.6-intel.rpm`

### Install the build environment

```
flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install --user org.freedesktop.Platform//21.08 org.freedesktop.Platform.Compat.i386//21.08 org.freedesktop.Sdk//21.08 org.freedesktop.Sdk.Compat.i386//21.08 org.flatpak.Builder
```

### Build

To build to a bundle:

```
flatpak run org.flatpak.Builder --force-clean build uk.lukeross.flatpak.lightscribe.yml
flatpak build-export export build
flatpak build-bundle export uk.lukeross.flatpak.lightscribe.flatpak uk.lukeross.flatpak.lightscribe
```

To build and push to a repository:

```
flatpak-builder --gpg-sign=keyid --repo=repo --force-clean build uk.lukeross.flatpak.lightscribe.yml
```

## Installing from a bundle

```
flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install --user org.freedesktop.Platform.Compat.i386//21.08
flatpak install --user uk.lukeross.flatpak.lightscribe.flatpak
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
