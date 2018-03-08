# Local repository creation

If you want to create a local (debian/ubuntu) repository,
either to share in a local network
or to serve as a backup when you reinstall your system

## Repository preparation

The time I'm writing this, I'm using KDE neon based on Ubuntu

First, create a folder which is your repository 



## Release file

```bash
apt-ftparchive release dists/xenial/ > Release
```

```bash
gpg --clearsign -o InRelease Release
```

In: ~/.gnupg/gpg.conf put:
```bash
cert-digest-algo SHA256
digest-algo SHA256
```
