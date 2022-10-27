# E Corp legacy .NET applications

[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/devprofr/ecorp-legacy-aspnetmvcdemo?label=Docker)](https://hub.docker.com/r/devprofr/ecorp-legacy-aspnetmvcdemo)
[![GitLab Pipeline Status](https://gitlab.com/devpro-labs/ecorp-legacy-demo/badges/main/pipeline.svg)](https://gitlab.com/devpro-labs/ecorp-legacy-demo/-/pipelines)

## Usage

* You can try with locally the container image from the registry (Docker Hub), from a Windows terminal as an Administrator

```dos
# dowloads locally a new image
docker pull devprofr/ecorp-legacy-aspnetmvcdemo:1.0.678482630

# runs the image locally
docker -c win run -it --rm -p 9002:80 devprofr/ecorp-legacy-aspnetmvcdemo:1.0.678482630
```

* Open the local instance [localhost:9002](http://localhost:9002/)

## Local development

* Install SDKs for .NET 4.8
* Use an IDE, such as Visual Studio 2022 Community
* Open a terminal with msbuild (for example Developer Command Prompt for VS 2022)

```dos
# builds the .NET solution locally
msbuild
```

* Workaround to run Docker with Windows images (found at [Rancher Desktop with both Windows and Linux Containers](https://jason.agostoni.net/2022/01/27/rancher-desktop-with-both-windows-and-linux-containers/))
* Download and extract latest version of docker from [docs.docker.com](https://docs.docker.com/engine/install/binaries/#install-server-and-client-binaries-on-windows)
* Start Docker daemon from a terminal as an Administrator

```dos
# starts Docker
"C:\Programs\docker-20.10.19\docker\dockerd.exe" -H npipe:////./pipe/docker_windows
```

* Create Docker context from the original terminal

```dos
# create Docker context
docker context create win --docker host=npipe:////./pipe/docker_windows
```

* Build and run Docker image from another terminal as an Administrator

```dos
# builds a new image
docker -c win build . -t ecorp-legacy-aspnetmvcdemo -f src/AspNetMvcDemoWebApp/Dockerfile

# runs the image
docker -c win run -it --rm -p 9002:80 ecorp-legacy-aspnetmvcdemo
```

* Open the local instance [localhost:9002](http://localhost:9002/)
