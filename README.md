# jupyterlab-scipy
Jupyter Lab base Docker container recipe based on [Jupyter datascience-notebook](https://hub.docker.com/r/jupyter/datascience-notebook) for [CyVerse VICE](https://cyverse-visual-interactive-computing-environment.readthedocs-hosted.com/en/latest/index.html). VICE requires additional configuration files to be compatible with our Condor and Kubernetes orchestration. 

[![CircleCI](https://circleci.com/gh/cyverse-vice/jupyterlab-scipy.svg?style=svg)](https://circleci.com/gh/cyverse-vice/jupyterlab-scipy)[![license](https://img.shields.io/badge/license-GPLv3-blue.svg)](https://opensource.org/licenses/GPL-3.0)
[![Project Supported by CyVerse](https://img.shields.io/badge/Supported%20by-CyVerse-blue.svg)](https://www.cyverse.org) [![Project Status: WIP – Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)

image | tag | size | metrics | build | status |  
----- | --- | ---- | ------- | ------|--------|
[![DockerHub](https://img.shields.io/badge/DockerHub-brightgreen.svg?style=popout&logo=Docker)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy) | latest | [![](https://images.microbadger.com/badges/image/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy) | [![](https://img.shields.io/docker/pulls/cyversevice/jupyterlab-scipy.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)  |  [![](https://img.shields.io/docker/automated/cyversevice/jupyterlab-scipy.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy/builds) | ![](https://img.shields.io/docker/build/cyversevice/jupyterlab-scipy.svg)

image | tag | size | metrics | build |
----- | ----| ---- | ------- | ------|
[![VICE](https://img.shields.io/badge/CyVerse-VICE-blue.svg?style=popout&logo=Docker&color=#1488C6)]()| latest | [![](https://images.microbadger.com/badges/image/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy/latest) | [![](https://img.shields.io/docker/pulls/cyversevice/jupyterlab-scipy.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)  |  [![](https://img.shields.io/docker/automated/cyversevice/jupyterlab-scipy.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)
[![VICE](https://img.shields.io/badge/CyVerse-VICE-blue.svg?style=popout&logo=Docker&color=#1488C6)]()| EarthLab | [![](https://images.microbadger.com/badges/image/cyversevice/jupyterlab-scipy.svg)](https://microbadger.com/images/cyversevice/jupyterlab-scipy/earthlab-latest) | [![](https://img.shields.io/docker/pulls/cyversevice/jupyterlab-scipy.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)  |  [![](https://img.shields.io/docker/automated/cyversevice/jupyterlab-scipy.svg)](https://hub.docker.com/r/cyversevice/jupyterlab-scipy)

# Instructions

## Run Docker locally or on a Virtual Machine

To run the RStudio container, you must first pull them from DockerHub, or activate a [CyVerse Account](https://user.cyverse.org/services/mine).

A Docker container for running RStudio is hosted on DockerHub.

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
