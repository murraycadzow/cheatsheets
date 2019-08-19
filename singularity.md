Grab container from a docker repo
e.g. 
```
# pull latest gatk docker image
singularity pull docker://broadinstitute/gatk
```

## Build container

Build a container from def file ([docs](https://sylabs.io/guides/3.2/user-guide/build_a_container.html))
1. create build file

```
Bootstrap: docker
From: ubuntu:16.04

%post
    apt-get -y update
    apt-get -y install fortune cowsay lolcat

%environment
    export LC_ALL=C
    export PATH=/usr/games:$PATH

%runscript
    fortune | cowsay | lolcat
```

2. build container

```
sudo singularity build lolcow.sif lolcow.def
```
