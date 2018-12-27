## Running Drupal in Docker

If you don't want to set up a Xampp/Lampp stack on your development machine, you can also run Drupal in a Docker container. There are several advantages to this approach:

* You don't pollute your development machine 
* You avoid conflicts with other servers on your development machine.
* You can easily wipe the installation and start over if something went wrong.
* It's requires fewer resources and maintenance than running Drupal in virtual machine.

### Install docker
Go to https://docs.docker.com/install/ and install Docker for your system. It is convenient to configure docker so that you can run ``docker`` as a normal user and don't have to use ``sudo`` every time.

### Prepare local directory
To develop h5p libraries in the docker container you need to be able to modify files inside the running container. The way docker does this is to mount "volumes" to paths in your file system. You can think of a volume as a symlink between a directory in your local file system and a directory in the container.

The local directory must be write-accessible to the user ``www-data`` of the Drupal container and you must still be able write its contents from your development user account.

Note: You can use the username ``www-data`` only if it is known to your local system. Alternatively, you can use ``33:33``, which is the user id of ``www-data`` inside the container.

```
mkdir files
sudo chown www-data:www-data files
sudo chmod -R 777 files
```

### Fetch and run container
Navigate to the directory in which you've created the ``files`` directory and execute this command:
```
sudo docker run --name drupaldev -d -p 8080:80 -v `pwd`/files:/var/www/sites/default/files -t wadmiraal/drupal:7
```

This will get the container from the Docker Hub and execute it. We don't use the official Drupal 7 image, because mounting a volume to the path ``/var/www/sites/default/files`` causes permission issues when using it. (The path is created as root user before Drupal is installed and is thus not write-accessible for the www-data user.)

### Access the container and configure H5P.
You can access drupal at http://localhost:8080 (username: admin, password: admin)

Now it's time to setup H5P as you normally would.

### Develop in the files directory
You can now develop your libraries in the directory ``files/h5p/development`` on your local machine. All changes will be automatically synced to the docker container.

### Stop the container
```
sudo docker stop drupaldev
```
This command will stop the container and remove it from memory, but not from disk. If you restart it later, its execution state will be restored.

### Restart the stopped container
``` 
sudo docker restart drupaldev
```

### Completely remove the container
If you want to wipe the whole Drupal container:
```
sudo docker rm drupaldev
```
This will not remove the files in the ``files`` directory, as docker volumes are designed to be persistent independent of container lifetime.
