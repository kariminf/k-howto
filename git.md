# Set up git

After installing your system, you want to set up git

## Install

### Debian-based linux systems

```sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

### Red Hat-based linux systems

```sh
sudo yum upgrade
sudo yum install git
```

### Mac

[Install HomeBrew](http://brew.sh/)

Then:

```sh
brew install git
```

### Windows

[Download and install](https://gitforwindows.org)

## Configure

This is the step I need the most after installing git.

### Setting username and email

Your username and commit email address

```sh
git config --global user.name "<your username>"
git config --global user.email "email@example.com"
```

### Caching your GitHub password

#### Linux

To set the cache time to the default (**15mn**)

```sh
git config --global credential.helper cache
```

With number of seconds (12 hours is good for me):

```sh
git config --global credential.helper 'cache --timeout=43200'
```

#### Windows

```bat
git config --global credential.helper wincred
```
#### Mac

```sh
git config --global credential.helper osxkeychain
```
