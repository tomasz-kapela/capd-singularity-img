https://cloud.sylabs.io/library/capdnet



singularity help key newpair


```
sudo singularity build capd-dev.sif capd-dev.def
singularity sign capd-dev.sif
singularity push capd-dev.sif library://capdnet/capd/capd-dev:latest

sudo singularity build capd.sif capd.def
singularity sign capd.sif
singularity push capd.sif library://capdnet/capd/capd:latest
```
