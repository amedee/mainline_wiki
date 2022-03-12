## Install libssl3

Ubuntu mainline kernel 5.15.7+ and 5.16 bump the requirement from `libssl1.1 (>= 1.1.0)` to `libssl3 (>= 3.0.0~~alpha1)`. However, package `libssl3` is *not* [available for Ubuntu 21.10 Impish Indri](https://packages.ubuntu.com/search?keywords=libssl3&searchon=names&section=all). It's only available for Ubuntu 22.04 Jammy Jellyfish, which is not yet released.

`libssl3` further depends on `libc6>=2.34` and `debconf`, which *are* available in 21.10 repositories.

`libssl3` can be installed in 2 different ways:

1. Use apt pinning (recommended method):
   * Configure the default release in the apt configuration file:
     ```
     APT::Default-Release "impish";
     ```
   * Add the Jammy repository to the apt sources:
     ```
     deb http://mirror.servers.com/ubuntu/ jammy main
     ```
   * Pin `libssl3` to the jammy version in apt preferences:
     ```
     Package: libssl3
     Pin: release n=jammy
     Pin-Priority: 900
     ```
   * Install `libssl3`:
     ```
     $ sudo apt install --yes libssl3
     ```
2. [Download](https://packages.ubuntu.com/jammy/libssl3) the `.deb` package and install it manually using `dpkg` (not recommended).
