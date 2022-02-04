# Manage system packages

## Major packaging system families
- Debian style (`.deb`) - Debian, Ubuntu, Linux Mint, Raspbian
- Red Hat style (`.rpm`) - Fedora, CentOs, Red Hat, OpenSUSE

## Packaging system tools
- Debian style:
  - Low level: `dpkg`
  - High level: `apt-get`, `apt`, `aptitude`
- Red Hat style:
  - Low level: `rpm`
  - High level: `yum`, `dnf`

## Finding a package in a repository
- Debian:
  - `apt-cache search <searchString>`
  - `apt search <searchString>`
- Red Hat:
  - `yum search <searchString>`

## Installing a package from a repository
- Debian:
  - `apt-get install <packageName>`
  - `apt install <packageName>`
- Red Hat:
  - `yum install <packageName>`

## Installing package from a package file
- Debian:
  - `dpkg -i <packageFile>`
- Red Hat:
  - `rpm -i <packageFile>`

## Removing a package
- Debian:
  - `apt-get remove <packageName>`
  - `apt remove <packageName>`
- Red Hat:
  - `yum erase <packageName>`

## Updating packages from a repository
- Debian:
  - `apt-get update && apt-get upgrade`
  - `apt update && apt upgrade`
- Red Hat:
  - `yum update`

## Upgrading package from a package file
- Debian:
  - `dpkg -i <packageFile>`
- Red Hat:
  - `rpm -U <packageFile>`

## Listing installed packages
- Debian:
  - `dpkg -l`
- Red Hat:
  - `rpm -qa`

## Determining whether a package is installed
- Debian:
  - `dpkg -s <packageName>`
- Red Hat:
  - `rpm -q <packageName>`

## Displaying information about an installed package
- Debian:
  - `apt-cache show <packageName>`
  - `apt show <packageName>`
- Red Hat:
  - `yum info <packageName>`

## Finding which package installed a file
- Debian:
  - `dpkg -S <file>`
- Red Hat:
  - `rpm -qf <file>`
