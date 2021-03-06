---
title: Ubuntu Bare-metal Installation
---

# Ubuntu Bare-metal Installation

[[toc]]

The Ubuntu bare-metal installation method (also known as the "traditional" installation method) is an advanced option available for those who want more complex customization options or are running on very limited hardware that can't handle the minor overhead of the Docker installation method.

Currently, the following operating systems are supported:

- Ubuntu 16.04 "Xenial" LTS
- Ubuntu 18.04 "Bionic" LTS

::: tip
Some web hosts offer custom versions of Ubuntu that include different software repositories. These may cause compatibility issues with AzuraCast. Many VPS providers are known to work out of the box with AzuraCast (OVH, DigitalOcean, Vultr, etc), and are thus highly recommended if you plan to use the Bare-metal installer.
:::

AzuraCast is optimized for speed and performance, and can run on very inexpensive hardware, from the Raspberry Pi 3 to the lowest-level VPSes offered by most providers.

Since AzuraCast installs its own radio tools, databases and web servers, you should always install AzuraCast on a "clean" server instance with no other web or radio software installed previously.

## Installing

Execute these commands **as a user with sudo permissions (or root)** to set up your AzuraCast server:

```bash
sudo apt-get update
sudo apt-get install -q -y git

sudo mkdir -p /var/azuracast/www
cd /var/azuracast/www
sudo git clone https://github.com/AzuraCast/AzuraCast.git .

sudo chmod a+x install.sh
./install.sh
```

The installation process will take between 5 and 15 minutes, depending on your Internet connection. If you encounter an error, let us know in the [Issues section](https://github.com/AzuraCast/AzuraCast/issues).

Once the terminal-based installation is complete, you can visit your server's public IP address (`http://ip.of.your.server/`) to finish the web-based setup.

## Updating

AzuraCast also includes a handy updater script that pulls down the latest copy of the codebase from Git, flushes the site caches and makes any necessary database updates. Run these commands as any user with `sudo` permissions:

```bash
cd /var/azuracast/www

sudo chmod a+x update.sh
sudo ./update.sh
```
