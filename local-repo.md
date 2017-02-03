# Local repository creation

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
