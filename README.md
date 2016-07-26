sandbox for opencv experiments
comes with qtcreator and miniconda with several data processing packages

# build the docker images
# <docker_image_tag> is the image name
$ docker build -t <docker_image_tag> .

# running the container in user mode with X11 
# <volume> is the volume to be mounted
$ docker run -ti -v /tmp/.X11-unix/:/tmp/.X11-unix/ -e DISPLAY=$DISPLAY -v <volume>:<volume> -p 9000:9000 -u 1000:1000 <docker_image_tag> /bin/bash
