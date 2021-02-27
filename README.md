# pkgconfig2apt
Small utility to translate pkgconfig names to APT name, based on ubuntu repositories

# How it works?
1. Using `sed`replace any `+`character with URL encoded `%2B` 
2. Search on https://packages.ubuntu.com/ using `wget` with folowing parameters:
- [x] mode=exactfilename
- [x] suite=[The Ubuntu release]
- [x] section=all
- [x] arch=any
- [x] keywords=[Searched pkgconfig package].pc
- [x] searchon=contents

3. Using `grep` and `cut` filter HTML output and extract debian package name
4. Finally display the apt-friendly package name

# How to install?

Simply:

```
sudo wget -c "https://raw.githubusercontent.com/sudo-give-me-coffee/pkgconfig2apt/main/pkgconfig2apt" -O "/usr/bin/pkgconfig2apt"
sudo chmod +x "/usr/bin/pkgconfig2apt"
```
# How to uninstall?

Simply:

```
sudo rm "/usr/bin/pkgconfig2apt"
```
# How to use?

Simply:

```
pkgconfig2apt [package]
```

# How to use on Debian and other directly derivated of it?

Export the variable `UBUNTU_RELEASE` with **Ubuntu** equivalent codename of desired Debian version, examples:

* Stretch (9)
```
UBUNTU_RELEASE=xenial pkgconfig2apt [package]
```
* Bullseye (10)
```
UBUNTU_RELEASE=focal pkgconfig2apt [package]
```


In general you can compare the bold names in https://wiki.ubuntu.com/Releases with names with a release date in https://wiki.debian.org/DebianReleases
