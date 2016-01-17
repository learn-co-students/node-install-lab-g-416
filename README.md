# node-install-lab

Installing Node and npm

## Objectives

1. Install Node v5.x and npm 3.x via the website installer
1. Install Node via n, nvm or nave (optional)
1. Install Node and npm with brew (optional, Mac OS X users only)
1. Configure npm so you get the ownership (optional)
1. Check Node and npm installations and the versions

## Introduction

So you pumped up about Node? Me too. But before we can go any further, we need to install it on our system. 

## Instructions

1. Install Node v5.1.0 with one of the methods listed below
2. Install npm v2.14.15 (typically comes with Node so you rarely if ever need to install it separately)
3. Check versions 5.1.0 and 2.14.15 for Node and npm respectively 


### One-Click Installers

Firstly, let's go to the <http://nodejs.org> and download a one-click installer for your Operation System. Choose version 5.1.0. The differences between stable and long-term support (LTS) is that LTS is for enterprises.

Don't choose binaries or source code unless you know what to do with them or your OS is not present (i.e., not Windows or Mac). The installers come with Node Package Manager (npm or NPM) — important tool for dependencies manages. No need to install npm separately, but you might want to downgrade to v2.14.15 because v3.x is slower.

Note: for older Mac OS X machines, you can pick 32-bit versions.

If there's no installer for your OS, you can get source code and compile it yourself (look for the installing from a tar file section in this file). The One-Click installer options will work for most of the developers. If you need other installation recipes, proceed with this text. Otherwise, run `$ npm test` to test the versions. You will see pass or not.


### Installing npm

npm comes with Node, but if you need to change the version (we recommend 2.14.15 for this course, because versions 3+ are slower than 2.x), then use npm to update/degrage npm. For example, if you have version 3.x, you can downgrade to 2.14.15 with:

```
$ npm install --global npm@2.14.15
```

### Checking the Installation

To test your installations, run these commands in your Terminal app (command line `cmd.exe` in Windows):

```bash
$ node -v
$ npm -v
```

You should see the 5.1.0 and 2.14.15 versions of Node and NPM that you've just downloaded and installed. Alternatively, run the tests for this lessons with `$ npm test`.


### Installing with HomeBrew or MacPorts

If someone already has HomeBrew (`brew`) installed, straightforwardly run:

```
$ brew install node
$ brew install npm
```

Similarly, for MacPorts it's just:

```
$ sudo port install nodejs
```

### Installing from a Tar file

For advanced users to avoid this, there's a 30 second installation (and [many others](https://gist.github.com/isaacs/579814)) from Isaac Z. Schlueter.

Set up a folder for the latest Node:

```bash
$ echo 'export PATH=$HOME/local/bin:$PATH' >> ~/.bashrc
$ . ~/.bashrc
$ mkdir ~/local
$ mkdir ~/node-latest-install
$ cd ~/node-latest-install
```

Note: advanced users who chose to make their own builds need to have certain compilers installed first. For more information, refer to [the official documentation](https://github.com/joyent/node/wiki/Installation).

Download the tar file with CURL, and unpack it:

```
$ curl http://nodejs.org/dist/node-latest.tar.gz | tar xz --strip-components=1
$ ./configure --prefix=~/local
```

Build Node and install it:

```
$ make install
$ curl https://npmjs.org/install.sh | sh
```


Tip: If you find your self getting errors trying to install module globally via NPM (`$ npm install -g <packagename>`), re-installing Node and NPM with the solution above should eliminate the need for using `sudo` with the installation command.

### Installing Without sudo

Sometimes depending on your configuration, NPM will ask users for `sudo` — root user permissions. To avoid using `sudo`, advanced developers can use:

```
$ sudo mkdir -p /usr/local/{share/man,bin,lib/node,include/node}
$ sudo chown -R $USER /usr/local/{share/man,bin,lib/node,include/node}
```

Note: please be sure and be comfortable with what `chown` command does before running it.

And then proceed to a normal installation of Node v5.1.0:

```
$ mkdir node-install
$ curl https://nodejs.org/dist/v5.1.0/node-v5.1.0.tar.gz | tar -xzf - -C node-install
$ cd node-install/*
$ ./configure
$ make install
$ curl https://npmjs.org/install.sh | sh
```

### Installing From a Git Repo

In case someone want to use the latest core Node code, and maybe even contribute to the Node and NPM projects, it's possible to build the installation from the cloned Git repo.

Making folders and adding path:

``` 
$ mkdir ~/local
$ echo 'export PATH=$HOME/local/bin:$PATH' >> ~/.bashrc
$ . ~/.bashrc
```

Cloning original Node repo from Joyent (alternatively, someone can fork it and clone his/her own repository):

``` 
$ git clone git://github.com/joyent/node.git
$ cd node
$ ./configure --prefix=~/local
```

Making the build:

```
$ make install
$ cd ..
```

Repeat for NPM:

```
$ git clone git://github.com/isaacs/npm.git
$ cd npm
$ make install 
```

For more cutting-edge NPM version:

```
$ make link
```

### Multi-version Setup with Nave

If someone plans to run multiple versions of Node, they should use [nave](https://github.com/isaacs/nave) which is a virtual environment for Node.


Make a folder:

```bash
mkdir ~/.nave
cd ~/.nave
```

Downloading Nave and setting the link to PATH'ed folder:

```
$ wget http://github.com/isaacs/nave/raw/master/nave.sh
$ sudo ln -s $PWD/nave.sh /usr/local/bin/nave
```

This is an example of switching to Node version 5.1.0 in a virtual environment with Nave:

``` 
$ nave use 5.1.0
```

To use NPM in this particular virtual environment, someone needs to use:

```
$ curl https://npmjs.org/install.sh | sh
```

After which it's possible to install something via NPM:

```
$ npm install express 
```

And exit virtual environment with:

```
exit
```

More approaches to install Node and NPM in [gist](https://gist.github.com/isaacs/579814).


### Multi-version Setup with NVM

Another options to Nave is NVM — Node Version Manager ([GitHub](https://github.com/creationix/nvm)). You can install NVM with:

```
$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh
```

or

```
$ wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh
```

And after that, harness NVM's `install`:

```
$ nvm install 5.1.0
```

To switch that 5.1 version, simply apply the `use` command, e.g., 

```
$ nvm use 5.1.0
```

## Alternative Multi-version Systems

Alternatives to Nave and NVM include:

* [neco](https://github.com/kuno/neco)
* [n](https://github.com/visionmedia/n)



