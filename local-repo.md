# Local repository creation

If you want to create a local (debian/ubuntu) repository,
either to share in a local network
or to serve as a backup when you reinstall your system.

## Install needed programs

@TODO description of debmypackage

## Repository preparation

The time I'm writing this, I'm using KDE Neon based on Ubuntu

First, create a folder which serves as your repository.

* Lets say, I want my repository to be in **/home/me/repo/**;
* I want to put the different packages in **/home/me/repo/neon64**;
* I want my distribution to be referred to as **neon**.

```sh
cd /home/me/
mkdir repo/neon64
```

You can copy the packages you installed on your PC from apt cache (**/var/cache/apt/archives/**)
to your packages folder **/home/me/repo/neon64**.
Then, empty the apt cache.

```sh
cp -v /var/cache/apt/archives/*.deb /home/me/repo/neon64/
sudo apt-get clean
```

## Packages distribution

If you want to distribute the packages based on  

## Release generation

In: ~/.gnupg/gpg.conf put:

```
cert-digest-algo SHA256
digest-algo SHA256
```

```sh
apt-ftparchive release dists/xenial/ > Release
```

```sh
gpg --clearsign -o InRelease Release
```
