[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)

# stat-toolbox container

Extended docker image of `rocker/geospatial`. It includes:

- Additional R packages
- Additional LaTeX packages
- Tmux, neovim and Nvim-R for text editor
- bash-it for additional bash commands
- Python3

I use this image for my research on developing statistical methods and analysis.

# How to use it


- You can use it with Rstudio interface:

```bash
docker run --rm -p 8787:8787 -e PASSWORD=yourpassword erickchacon/stat-toolbox:3.6.0
```

- You can use with bash:

```bash
docker run --rm --user rstudio -it erickchacon/stat-toolbox:3.6.0 bash
```

- You can use with bash and x11 support:

```bash
  XSOCK=/tmp/.X11-unix && \
  XAUTH=/tmp/.docker.xauth && \
  xauth nlist :0 | sed -e "s/^..../ffff/" | xauth -f $XAUTH nmerge - && \
  docker run --user rstudio  \
  -v $XSOCK:$XSOCK -v $XAUTH:$XAUTH \
  -e XAUTHORITY=$XAUTH  -e DISPLAY=$DISPLAY -e "TERM=xterm-256color-italic" \
  --rm -it erickchacon/stat-toolbox:3.6.0 bash
```

- Remember to load the desired volumes by adding something similar to

```bash
-v $HOME/Documents/:/home/rstudio/Documents
```

- You can also add the option `-d` after run to detach the container, an later interact with the container using `docker exec -it {container-name} bash` 


