# Create a debian package

You want to create a debian/ubuntu package from your project.
Here are the different steps to achieve that.

For the sake of the tutorial, we suppose the project's name is *mypack* and its version is *1.0.1*.

## Install needed packages

```sh
sudo apt-get install dh-make devscripts
```

## Create the source file

In a folder, say "release", create a folder named by your project's name followed by a hyphen (-), then the version.

```sh
mkdir mypack-1.0.1
cd mypack-1.0.1/
```
Then call this instruction:

```sh
dh_make --createorig
```

For more options:

* -e (email address)
* -c (copyright type). Types: apache, artistic, bsd, gpl, gpl2, gpl3, lgpl, lgpl2, lgpl3, mit, custom
* Package class:
  * -s : single
  * -i : arch-independent
  * -l : library
  * --python: python

This will create a file `mypack_1.0.1.orig.tar.xz` in the folder "release" (the parent folder)
Also, a folder *debian* with a lot of files (most of them I delete; I don't even know what they are for).
Add a file named *install* to specify where each file must be installed in the system (you must be familiar with Linux file system).

```sh
cd debian
rm *.ex README* *.EX *.docs
touch install
```

* Modify *control* which describes the package. The file sections are straightforward
* Modify *changelog*: recent changes first
* Modify *Copyright*: year and if your email is wrong
* Modify *install*: supposing you have a file named *exec* and you want to put it in */usr/bin/*. Then, add the line *exec /usr/bin/*

## Build the debian package

Make sure:

* You have set up a username and an email in changelog
* You have a gpg key on your PC linked to these two (the first changelog in the file, i.e. the last one made)

Return to *mypack-1.0.1* folder

```sh
cd ..
```

To upload your package on Launchpad, please refer to [Launchpad packaging tutorial](ppa-pack.md).

If you want to generate .deb file locally (on your machine), then simply type:

```sh
debuild
```
If you set up your gpg signature properly, you will be asked to afford your passkey
