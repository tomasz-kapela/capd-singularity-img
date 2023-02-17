CAPD Singularity image 
======================

Project contains scripts that create Singularity image with [CAPD library](http://capd.ii.uj.edu.pl/) installed in `/usr/local` directory.
The image is available through oficial Singularity library or can be created locally from scripts.

[Singularity](https://sylabs.io/) is a virtualization software based on containers. Follow [Quick Start](https://docs.sylabs.io/guides/3.11/user-guide/quick_start.html) for install and basic use instructions.

## Image from the library

Visit [https://cloud.sylabs.io/library/capdnet](https://cloud.sylabs.io/library/capdnet) for the list of available CAPD singularity images 

The latest capd image can be run by

```bash
singularity shell library://capdnet/capd/capd  
```

To download image to local storage before running invoke

```bash
singularity pull library://capdnet/capd/capd  
```

## Local image

This option is recommended if 

* you need the latest gcc or the latest capd 
* specific version of gcc or capd (in that case you have to modify *.def scripts)

First download or checkout capd-singularity-img project. Then
local image can be created and run with commands

```bash
sudo singularity build capd.sif capd-all.def
singularity shell capd.sif
```

## Updating image in the library

First you have to:  

* create an account at [https://cloud.sylabs.io](https://cloud.sylabs.io)
* create an [Access Token](https://cloud.sylabs.io/tokens) and login with it `singularity remote login`
* create a key pair for image signing (see `singularity help key newpair`)

Then you can build, sign and upload capd images to the library (replace path with path to your projects)

```
sudo singularity build capd-dev.sif capd-dev.def
singularity sign capd-dev.sif
singularity push capd-dev.sif library://capdnet/capd/capd-dev:latest

sudo singularity build capd.sif capd.def
singularity sign capd.sif
singularity push capd.sif library://capdnet/capd/capd:latest
```
