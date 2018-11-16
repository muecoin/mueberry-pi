# MUE Stakebox rPi2+ image generator

This Ansible playbook will generate an image for your Raspberry Pi 2 (and up). The image includes the MonetaryUnit (MUE) wallet and some useful files to run it.

It's based on the latest Raspbian Stretch With Desktop image.

The image is altered as little as possible. All added files are fetched from their upstream sources and their SHA256 checksums verified.

## Usage

Make sure you have plenty of free space available, around 10 GB at least.

You also need to have [Ansible 2.6 or later installed](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

The Ansible playbook will run locally, and requires your user to have `sudo` access. I admit this can be dangerous, so read through the playbook first.

```
git clone https://github.com/muecoin/mueberry-pi.git
cd mueberry-pi
ansible-playbook mueberry-pi.yml -v -K

```

This will take a while, because it will
* download the 1.4 GB Raspbian image
* extract it (3.9 GB)
* add the MUE wallet and supporting files
* create a compressed image [you can write to SD](https://www.raspberrypi.org/documentation/installation/installing-images/)


## Configuration

The entire config is done in the `vars` section of the `mueberry-pi.yml` file.

The most useful settings are:

* `stakebox_image_name`: the filename of the resulting image. It will be suffixed with the current date.
* `stakebox_image_compression`: the compression method that will be used on the resulting image. This is a list, so you can specify more than one and you will have several archives. The more methods you specify, the more time and space (around 1.4 GB per archive) it will take.
*  `work_dir`: the directory that will be used. It needs to have around 10 GB of free space.

