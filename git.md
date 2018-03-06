# Set up git

After installing your system, you want to set up git

## Install

### Debian-based linux systems

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

### Red Hat-based linux systems

```bash
sudo yum upgrade
sudo yum install git
```

### Mac

[Install HomeBrew](http://brew.sh/)

Then:
```
brew install git
```

### Windows

[Download and install](https://gitforwindows.org)

## Configure

This is the step I need the most after installing git.

### Setting username and email
Your username
```
git config --global user.name "<your username>"

```
Your commit email address
```
git config --global user.email "email@example.com"

```

### Caching your GitHub password

#### Linux
Default: 15mn
```
git config --global credential.helper cache
```
With number of seconds (12 hours is good for me):
```
git config --global credential.helper 'cache --timeout=43200'
```

#### Windows
```
git config --global credential.helper wincred
```
#### Mac
```
git config --global credential.helper osxkeychain
```
