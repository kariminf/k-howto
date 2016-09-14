# Create a debian package

Suppose your project name is mypack. Suppose, the version is 1.0.1.

These are steps to create a debian file:

## Install needed packages
```bash
sudo apt-get install ... <I forgot :p >
```

## Create the source file
In a folder, say "release" create a folder like this:
```
mypack-1.0.1
```
Your project name followed by a hyphen (-), then the version.
```bash
cd mypack-1.0.1/
```
Then call this instruction:
```bash
dh_make --indep --createorig
```
This will create a file `mypack_1.0.1.orig.tar.xz` in the folder "release"

%TODO complete
