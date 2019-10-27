## Running Drupal in Docker

If you don't want to set up a Xampp/Lampp stack on your development machine, you can also run Drupal in a Docker container. There are several advantages to this approach:

* You don't pollute your development machine 
* You avoid conflicts with other servers on your development machine.
* You can easily wipe the installation and start over if something went wrong.
* It's requires fewer resources and maintenance than running Drupal in virtual machine.


### Installing docker
Go to https://docs.docker.com/install/ and install Docker for your system. It is convenient to configure docker so that you can run ``docker`` as a normal user and don't have to use ``sudo`` every time.

### Preparing the local data directory
To develop H5P libraries in the Docker container you need to be able to modify files inside the running container. The way Docker does this is to mount "volumes" to paths in your file system. You can think of a volume as a symlink between a directory in your local file system and a directory in the container. Drupal stores all H5P data (content and libraries) in ```/var/www/html/sites/default/files```. You have to mount this path to a local directory. **The local directory must be write-accessible** to the user ``www-data`` of the Drupal container and **you must still be able write its contents from your development user account.** To achieve this execute the following from the command line:

```
mkdir files
sudo chmod -R 777 files
```

### Running the container
Navigate to the directory in which you've created the ``files`` directory and execute this command to fetch the container from the Docker Hub and execute it:
```
sudo docker run --name drupaldev -d -p 8080:80 -v `pwd`/files:/var/www/html/sites/default/files -t sr258/drupal-h5p-docker
```

### Accessing the container and configure H5P.
You can access drupal at http://localhost:8080 (username: admin, password: admin)

Your first step should be to enable the "H5P development mode" and "library development directory" in the settings (see http://localhost:8080/node#overlay=admin/config/system/h5p).

## Developing H5P libraries
You can now develop your libraries in the directory ``files/h5p/development`` on your local machine. All changes will be automatically synced to the docker container.

### Stopping the container
To stop the container and remove it from memory, execute the command below. If you restart it later, its execution state will be restored.
```
sudo docker stop drupaldev
```

### Restarting the stopped container
To restart a stopped container execute this command:
``` 
sudo docker restart drupaldev
```

### Completely removing the container
If you want to wipe the whole Drupal container (and all data inside), execute:
```
sudo docker rm drupaldev
```
This will not remove the files in the ``files`` directory, as Docker volumes are designed to be persistent independent of container lifetime.
