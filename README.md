## TilerService Docker
A dockerized image of the [TilerService](https://github.com/maritime-web/TilerService).

# Prerequisites
* Docker
* A file called application.properties
* A license key for MapTiler Pro

# Configuration
The application.properties file must at least contain the following lines:

    dmi.server = <ftp server address>
    dmi.user = <ftp user>
    dmi.password = <ftp password>
    dmi.directory = <ftp directory>

    mapTiler.license = <license key for MapTiler Pro>
    mapTiler.arguments = <arguments for MapTiler Pro>

    tiles.hostDirectory = <the absolute path to the directory where images to be tiled are stored>



# Execution
Before you run the container you must pull the image for the MapTiler Pro container:

    docker pull klokantech/maptiler


To run the container you can do it the following way:

    docker run --name tiler-service -v /var/run/docker.sock:/var/run/docker.sock \
    -v $HOME/data:/data/tiles \
    -v <where you stored application.properties>/application.properties:/data/properties/application.properties dmadk/tiler-service

The reason why the container needs to mount the Docker socket is because it needs to be able to start MapTiler Pro in a seperate container.
