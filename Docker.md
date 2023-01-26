### Why Docker?:
Docker is a great method for any end user to use a developer's application fully pre-configured and optimized for best performance and experience. The Emby team has taken a lot of time and care to ensure we are delivering an application that will bring you lots of pleasure with minimal fuss.

### Information:
After much user feedback we have reworked our Docker images from the ground up. We are now following [Docker's best practices for writing a `Dockerfile`](https://docs.docker.com/engine/articles/dockerfile_best-practices/). Our build begins on OBS where we are using [openSUSE's Kiwi imaging system](https://doc.opensuse.org/projects/kiwi/doc/) for our new base image with `ffmpeg` and `mono` pre-installed. The new image weights in just shy of 320 MB, by comparison our Debian base image was about 850 MB. Additionally, we are now using a rolling release distribution. We felt that we needed to be on the cutting edge as much a possible so our new distro of choice is Tumbleweed. Why Tumbleweed, we hope that by using openSUSE's imaging system and distros we can support as many architectures as possible and have full control of every single binary found on the system. This is how we were able to minimize the foot print of the images. Full list of changes follows:
* Custom base image built from `SCRATCH`.
* Tubleweed
* static ffmpeg (smaller footprint)
* S6-overlay used as our process supervisor (needed for restart and no dependencies)
* new installation script
* systemd script included
* emby-server script included
* one easy command setup

### Installation:
Before installing our pre-configured and containerized application it is recommend you install Docker. You can install docker following [these directions](https://docs.docker.com/engine/installation/). Once Docker is installed proceed with the following directions. 

We recommend you install directly from the [docker hub](http://hub.docker.com). By following our [Docker directions](Docker-Getting-Started). 