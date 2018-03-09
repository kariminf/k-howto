# Put a package on launchpad

* Create a launchpad account
* Create a new ppa

when you create the package, use:

* `debuild -S -sd` (to not upload .orig.tar.gz file, in case the source code is the same as an early uploaded package)
* `debuild -S -sa` (to a fresh upload)

Then:

```sh
cd ../
dput ppa:account-name/ppa-name package_version-..._source.changes
```
