# Docker uwegerdes/baseimage-arm32v7

A common base image for my Dockerfiles on Raspberry Pi 3 to save some disk space and build time.

The base for this image is arm32v7/ubuntu but it might change in the future. For Raspberry Pi 3 you should use this baseimage for my other projects, for others architectures (arm64v8, arm32v6 and arm32v5) there are images too - replace it in the `Dockerfile` before build. Check `uname -m` for a hint.

## Building with settings

If you want to build it with other settings load the Dockerfile in an empty directory, perhaps edit it to your needs.

If you have an apt-cacher-ng proxy server (try [uwegerdes/apt-cacher-ng](https://github.com/UweGerdes/docker-apt-cacher-ng)) you should check `hostname -i` or change it to an address available in your local network (not localhost) or omit the APT_PROXY line in the command above.

There is also a timezone parameter for the baseimage-arm32v7, here set to `Europe/Berlin`.

Build the image with (you might change/omit the build-args, mind the dot in the last line):

```bash
$ docker build -t uwegerdes/baseimage \
	--build-arg APT_PROXY="http://192.168.1.18:3142" \
	--build-arg TZ="Europe/Berlin" \
	.
```

## Usage

Use this baseimage in other `Dockerfile`s, they should work with this arm32v7 version or my [default baseimage](https://github.com/UweGerdes/docker-baseimage):

```
FROM uwegerdes/baseimage
```

## Settings

The build-args are saved and used by all images depending on this image.

