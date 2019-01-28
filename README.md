# docker_files
![](https://img.shields.io/badge/uses-docker-blue.svg)

* various tools I use as docker


**Example:**
* using ``toolname`` (e.g. `porechop` or `canu` etc.)
  * example for a fictive input `-i` and output `-o` is given to understand docker pathing
* `${WORKDIRPATH}` could be `$PWD` - your current working dir
* `${WORKDIRNAME}` its the location in the docker, the mountpoint
  * its important for your in- and output, but choose name freely

````bash
docker run --rm -it -v ${WORKDIRPATH}:/${WORKDIRNAME} replikation/toolname \
toolname -i /${WORKDIRNAME}/input -o /${WORKDIRNAME}/output
````

* some of the docker have entrypoints, like unicycler or guppy
* docker with more than one executable usually dont have entrypoints
* if you need another script (e.g. "other_script.sh") overwrite the entrypoint like this: ``docker run --entrypoint other_script.sh``
