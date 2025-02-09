# Tailscale package for QNAP NAS

This repository includes build scripts for building Tailscale client QPKG for
use in QNAP NAS devices.

## Build

The build depends on Docker and `make`. All other build dependencies are
downloaded in the Docker containers. To invoke the build, run `make pkg`.
This builds Tailscale QPKG for different platforms and stores them in
**out/pkg**.

To configure the release number from what is in the Makefile,
set the environment variable `TSTAG` to the release number, e.g.
`TRACK=unstable TSTAG=1.33.161 make pkg`.

## Installation

1. Manually install Tailscale package in QNAP App Center.
2. Open the Tailscale app and proceed with login.


##CLI/SSH for configuration and set up after instalation of qpkg (Use this if on older firmware [e.g. 5.0.0.1986] or if you prefer cli)

1. Login to your qnap with ssh
2. Use the command `getcfg SHARE_DEF defVolMP -f /etc/config/def_share.info` to know where you have installed the app. (Its output should look like `/share/CACHEDEV1_DATA/` or `/share/CACHEDEV1_DATA/`)
3. Go to Tailscale package directory: `cd /share/CACHEDEV1_DATA/.qpkg/Tailscale`
4. Authorize your client: `./tailscale up`

##Notes
If the command won't run with `./tailscale` only, put `-socket var/run/tailscale/tailscaled.sock` argument after `./tailscale` (e.g. `./tailscale --socket var/run/tailscale/tailscaled.sock status`)

To get an https certificate run the command `./tailscale cert` this would act the same way as `sudo tailscale cert` in linux distributions

## Credits

Thanks to [@ivokub](https://github.com/ivokub/) for creating this
project and transferring it to Tailscale's GitHub org.
