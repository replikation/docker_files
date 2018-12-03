# docker_files
![](https://img.shields.io/badge/uses-docker-blue.svg)

* various tools I use as docker


**Example:**
* using a ``<toolname>`` (e.g. `porechop`)
  * example for a fictive input `-i` and output `-o` is given to understand docker pathing
* `${WORKDIRPATH}` could be `pwd` or `$PWD` - your current working dir
* `${WORKDIRNAME}` its the location in the docker, the mountpoint
  * its important for your in- and output, but choose name freely

````bash
docker run --rm -it -v ${WORKDIRPATH}:/${WORKDIRNAME} <imagename> \
<toolname> -i /${WORKDIRNAME}/<input> -o /${WORKDIRNAME}/<output>
````
