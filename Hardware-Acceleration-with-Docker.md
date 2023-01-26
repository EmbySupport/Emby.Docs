
### VA API in Docker

Docker usage on unraid as sample

```
\flash\config\go

#enable module for iGPU and perms for the render device
modprobe i915
chown -R nobody:users /dev/dri
chmod -R 777 /dev/dri

docker run command extra parameter

--device /dev/dri:/dev/dri/dri:/dev/dri`
```

thats it


***


i can only speak for intel here, but latest 3 gens i6, i7, i8 ... its for the end user side all there is ...
enable intel on the host vie the go file, give the docker access ... eith via the extra parameter in docker run OR by priviledged access.
thats it to get all features running with vaapi, decoding all formats from the site, encoding to h264
quicksync ...another story wich i dont really know (not needed in any way here cause vaapi does the job).
when i remember there are no special drivers or so needed on most NAS system on intel base like freenas, unraid, etc ...
also the boxes like synology etc are ready out of the box.

AMD or Nvidia are rather different cause there is always a driver issue somewhere ... i also tried to get nvidia working
with my plex docker before and ended up in switching (take the intel for host and use for dockers, pass the nvidia for my VM).

so in the end, its those 2 steps up there ... may someone with a synology or so can tell if its even just a click in the webui ...

***

### NVIDIA in Docker
#### Tested with P2000 on Debian 9 (stretch)

- Install nvidia drivers
    - https://www.nvidia.com/Download/driverResults.aspx/140135/en-us for latest
    - To test drivers run `nvidia-smi`
        - Expected output:
        ```
        > nvidia-smi
        $Date
        +-----------------------------------------------------------------------------+
        | NVIDIA-SMI 410.66       Driver Version: 410.66       CUDA Version: 10.0     |
        |-------------------------------+----------------------+----------------------+
        | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
        | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
        |===============================+======================+======================|
        |   0  Quadro P2000        Off  | 00000000:83:00.0 Off |                  N/A |
        | 68%   40C    P0    19W /  75W |      0MiB /  5059MiB |      0%      Default |
        +-------------------------------+----------------------+----------------------+

        +-----------------------------------------------------------------------------+
        | Processes:                                                       GPU Memory |
        |  GPU       PID   Type   Process name                             Usage      |
        |=============================================================================|
        |  No running processes found                                                 |
        +-----------------------------------------------------------------------------+

        ```
- Install `nvidia-docker2`
    - https://github.com/NVIDIA/nvidia-docker
- Either edit docker daemon or set runtime arg
    - My docker daemon: `/etc/docker/daemon.json`
    ```    
    "runtimes": {
        "nvidia": {
            "path": "nvidia-container-runtime",
            "runtimeArgs": []
        }
    },
        "default-runtime": "nvidia"
    }
    ```

- Required Docker environment variables
    - NVIDIA_VISIBLE_DEVICES=all         
    - NVIDIA_DRIVER_CAPABILITIES=compute,utility,video

#### Further Reading
[Transcoding with Nvidia in Docker](https://www.funkypenguin.co.nz/note/gpu-transcoding-with-emby-plex-using-docker-nvidia)

