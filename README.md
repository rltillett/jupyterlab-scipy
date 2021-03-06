# jupyterlab-scipy
Jupyter Lab base Docker container recipe based on [Jupyter datascience-notebook](https://hub.docker.com/r/jupyter/scipy-notebook) for [CyVerse VICE](https://cyverse-visual-interactive-computing-environment.readthedocs-hosted.com/en/latest/index.html). VICE requires additional configuration files to be compatible with our Condor and Kubernetes orchestration. 

[![CircleCI](https://circleci.com/gh/cyverse-vice/jupyterlab-scipy.svg?style=svg)](https://circleci.com/gh/cyverse-vice/jupyterlab-scipy) [![license](https://img.shields.io/badge/license-GPLv3-blue.svg)](https://opensource.org/licenses/GPL-3.0) [![Project Supported by CyVerse](https://img.shields.io/badge/Supported%20by-CyVerse-blue.svg)](https://www.cyverse.org) [![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3246934.svg)](https://doi.org/10.5281/zenodo.3246934)


image | tag | size | metrics | build | 
----- | --- | ---- | ------- | ------|
[![DockerHub](https://img.shields.io/badge/DockerHub-brightgreen.svg?style=popout&logo=Docker)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy) | [![](https://images.microbadger.com/badges/version/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy "latest") |  [![](https://images.microbadger.com/badges/image/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy "latest") | [![](https://img.shields.io/docker/pulls/cyversevice/jupyterlab-scipy.svg?label=pulls&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)  |  [![](https://img.shields.io/docker/cloud/automated/cyversevice/jupyterlab-scipy.svg?label=build&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy/builds) 

image | tag | size | metrics | build |
----- | ----| ---- | ------- | ------|
[![VICE](https://img.shields.io/badge/CyVerse-VICE-blue.svg?style=popout&logo=Docker&color=#1488C6)]()| [![](https://images.microbadger.com/badges/version/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy "latest") | [![](https://images.microbadger.com/badges/image/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy) | [![](https://img.shields.io/docker/pulls/cyversevice/jupyterlab-scipy.svg?label=pulls&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)    | [![](https://img.shields.io/docker/cloud/automated/cyversevice/jupyterlab-scipy.svg?label=build&logo=docker&logoColor=white)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy/builds) 
[![VICE](https://img.shields.io/badge/CyVerse-VICE-blue.svg?style=popout&logo=Docker&color=#1488C6)]()|[![](https://images.microbadger.com/badges/version/cyversevice/jupyterlab-scipy:earthlab-latest.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy:earthlab-latest "earthlab-latest") | [![](https://images.microbadger.com/badges/image/cyversevice/jupyterlab-scipy:earthlab-latest.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy:earthlab-latest "earthlab-latest")| [![](https://img.shields.io/docker/pulls/cyversevice/jupyterlab-scipy/earthlab-latest.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy/earthlab-latest)  |  [![](https://img.shields.io/docker/automated/cyversevice/jupyterlab-scipy/earthlab-latest.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy/earthlab-latest)

# Instructions

## Run Docker locally or on a Virtual Machine

To run the JupyterLab, you must first `pull` from DockerHub, or activate a [CyVerse Account](https://user.cyverse.org/services/mine) and launch in the Discovery Environment VICE.

The container for running JupyterLab is hosted on DockerHub and can be started locally:

```
docker pull cyversevice/jupyterlab-scipy:latest
```

```
docker run -it --rm -d cyversevice/jupyterlab-scipy:latest
```

The default username is `jovyan`

## Run Docker container in CyVerse VICE

Unless you plan on making changes to this container, you should just use the existing launch button above. 

###### Developer notes

To test the container locally:

```
docker run -it --rm -v /$HOME:/app --workdir /app -p 8888:8888 -e REDIRECT_URL=http://localhost:8888 cyversevice/jupyterlab-scipy:latest
```

To test **The autobuild** container locally:

```
docker pull rltillett/jupyterlab-scipy:auto
docker images
docker run -it --rm -v /$HOME:/app --workdir /app -p 8888:8888 \
-e REDIRECT_URL=http://localhost:8888 \
--name autolab rltillett/jupyterlab-scipy:auto
```

Then use a web browser to navigate to [http://localhost:8888](http://localhost:8888) 
and see if notebooks, the jupyter terminal, and most imporantly, test that `lolcat` works.

To test lolcat, open up the jupyter terminal and run a command such as

```
grep --help | lolcat
```

#### Manual building of this image on your machine

1. Fork this repo on your own github account
2. Run the code below, but replace all `rltillett` with your github user name

```
git clone https://github.com/rltillett/jupyterlab-scipy.git
cd jupyterlab-scipy/
docker images # check that nothing with the following build tag already exists
docker build --no-cache --tag rltillett/jupyterlab-scipy:manual .
docker images # see that this new one exists and can run

docker run -it --rm -v /$HOME:/app --workdir /app -p 8888:8888 -e REDIRECT_URL=http://localhost:8888 \
--name jupman rltillett/jupyterlab-scipy:manual
```

#### Auto-built (at my dockerhub) testing instructions
To test **The autobuild** container locally:

```
docker pull rltillett/jupytests:jupylol
docker images
docker run -it --rm -v /$HOME:/app --workdir /app -p 8888:8888 \
-e REDIRECT_URL=http://localhost:8888 \
--name autolol rltillett/jupyterlab-scipy:auto
```

Then use a web browser to navigate to [http://localhost:8888](http://localhost:8888)
and see if notebooks, the jupyter terminal, and most imporantly, test that `lolcat` works.

To test lolcat, open up the jupyter terminal and run a command such as

```
grep --help | lolcat
```
