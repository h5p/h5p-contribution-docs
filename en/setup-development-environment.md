## Setting up a development environment

There's a brief overview at [https://h5p.org/development-environment](https://h5p.org/development-environment),
if you feel confident. Here you will find links to software that you need or may be helpful. Please note, that using this
documentation will require you to have some knowledge about how webservers work. There's always room for improvement :-)

### Webserver
There is a rudimentary webserver that's useful if you want to create a content type only. It's included in [https://github.com/h5p/h5p-cli](https://github.com/h5p/h5p-cli).
Here we will use a different approach as it better mirrors cases with upgrading existing content types, etc.

One of the easiest ways to get a webserver onto your machine is to get Xampp/Lampp.
Please see [https://www.apachefriends.org/index.html](https://www.apachefriends.org/index.html)

When you have a webserver installed, you need to create a database, a database user that can write to this database, and
a user password, of course. If you're using Xampp/Lampp, you can [use phpmyadmin](https://www.phpmyadmin.net/docs/) that's part of the bundle.

### The host system: Drupal 7 (in words: seven).
Please install the latest version of Drupal 7 on the webserver that you have installed. It's not the latest Drupal version, but its H5P plugin has some development features that we need: [https://www.drupal.org/docs/7/install](https://www.drupal.org/docs/7/install
).

### Alternative: Docker webserver
As an alternative to the Xampp/Lampp installation above, you can read about running Drupal 7 in a docker container [here](docker-webserver.md).

### The H5P plugin
Go to the _module configuration page_ of your freshly installed Drupal instance and install the latest version of the H5P plugin found at:
[https://www.drupal.org/project/h5p](https://www.drupal.org/project/h5p).

Afterwards, can enable the plugin (actually it has two componente, the view and the editor). Then you can access the plugin's _Settings_ via the _module configuration page_.
- Check "Enable H5P development mode"
- Check "Enable library development directory"

This should create a library _/sites/default/files/h5p/development_ which you can use to store new content types. When
"Enable library development directory" is checked, H5P will always look for libraries there first before trying to look
in the regular _libraries_ folder. This allows you to install and modify (copies of) libraries there without touching the
regular version. If you feel like something got messed up, deleting the contents of the development folder should still
leave you with a working system. There are some exceptions to this rule, but those should be covered elsewhere.

### An editor
You can basically develop content with any text editor that you like, but it it pretty helpful to use one that
was designed for this purpose. We think that atom is a good choice.
[https://atom.io/](https://atom.io/)

### A linter
A linter is a tool that can check you're code for certain flaws while you're typing. We recommend to use one very much!
You should consider to use _eslint_ (linter-eslint package for atom) and use our configuration file for it. This way, you can make sure to adhere to
our [coding conventions](https://h5p.org/documentation/for-developers/coding-guidelines). Please [get the configuration file from github](https://github.com/h5p/h5p-dev-tools).

### git and github
At some point you will most likely have to use github and git. There's an extensive [video playlist on both by Udacity](https://www.youtube.com/watch?v=Ytux4IOAR_s&list=PLAwxTw4SYaPk8_-6IGxJtD3i2QAu5_s_p).

### node.js
Some content types/libraries use npm to install library dependencies or to start a building process, so you will want to
[install node.js](http://nodejs.org/download/). Also, if you want to create a new content type, we recommend to get it. This way, you'll be able to use
our boilerplate template to get started quickly.

### h5p-cli
The h5p-cli tool offers some nice features for working with git, with translations and for packing libraries. You can easily
install it using _npm_ from the previous step ```npm -g install h5p```
