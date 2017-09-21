# Docker uwegerdes/baseimage-armhf

A common base image for my Dockerfiles on Raspberry Pi 3 to save some disk space and build time.

The base for this image is armhf/ubuntu but it might change in the future.

## Building with settings

If you want to build it with other settings load the Dockerfile in an empty directory, perhaps edit it to your needs.

If you have an apt-cacher-ng proxy server (try [uwegerdes/apt-cacher-ng](https://github.com/UweGerdes/docker-apt-cacher-ng)) you should check `hostname -i` or change it to an address available in your local networt (not localhost) or omit the APT_PROXY line in the command above.

There is also a timezone parameter for the baseimage-armhf, here set to `Europe/Berlin`.

Build the image with (you might change/omit the build-args, mind the dot in the last line):

```bash
$ docker build -t uwegerdes/baseimage-armhf \
	--build-arg APT_PROXY="http://192.168.1.18:3142" \
	--build-arg TZ="Europe/Berlin" \
	.
```

## Usage

Use this baseimage-armhf in other `Dockerfile`s:

```
FROM uwegerdes/baseimage-armhf
```

## Settings

The build-args are saved and used by all images depending on this image.

