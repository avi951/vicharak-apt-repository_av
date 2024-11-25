<<<<<<< HEAD
# Vicharak Debian/Ubuntu APT Repository

This repository contains the Linux packages for Vicharak Debian and
Ubuntu based systems.

## Installation

To install Vicharak APT onto your ARM64 Debian/Ubuntu distro, run the following
commands:

```bash
wget -qO - http://apt.vicharak.in/pgp-key.public | sudo apt-key add -
```

or

```bash
curl -sSL http://apt.vicharak.in/pgp-key.public | sudo apt-key add -
```

Then add the apt repository to your `/etc/apt/sources.list` file:

```bash
echo "deb http://apt.vicharak.in stable main" | sudo tee -a /etc/apt/sources.list
```

Then run the following commands:

```bash
sudo apt update
```

## Packages

The following packages are available in this repository:

* [vicharak-config](http://github.com/vicharak-in/vicharak-config)
* [vicharak-firmware](http://github.com/vicharak-in/vicharak-firmware)
* [vicharak-kernel-image](http://github.com/vicharak-in/linux-kernel)
* [vicharak-kernel-headers](http://github.com/vicharak-in/linux-kernel)
* [vicharak-kernel-libc](http://github.com/vicharak-in/linux-kernel)
* [vicharak-u-boot](http://github.com/vicharak-in/u-boot-vicharak)

## License

The packages in this repository are licensed under the [MIT License](LICENSE).
=======
# Guide to Adding Debian Packages to the Repository

This guide explains how to add Debian packages to an existing APT repository using `reprepro`. Ensure that the required directory structure and configuration files (`distributions` and others) are already set up.

---

## Steps to Add Debian Packages

### Step 1: Clone the Repository

Start by cloning the APT repository from GitHub to your local machine:
```bash
git clone https://github.com/Pratiksha0102/vicharak-apt-repository.git
cd vicharak-apt-repository
```

### Step 2: Addthe packages to the Repository.

Run the reprepro command to add the .deb package to the desired distribution.

- To add common packages for axon and vaaman
```bash
reprepro -b /path/to/vicharak-apt-repository includedeb stable /path/to/<package.deb>
```

- To add axon specific packages
```bash
reprepro -b /path/to/vicharak-apt-repository includedeb stable-axon /path/to/<package.deb>
```

- To add vaaman specific packages
```bash
reprepro -b /path/to/vicharak-apt-repository includedeb stable-vaaman /path/to/<package.deb>
```

### Step 3: Verify the Package Addition

Check if the package has been successfully added to the repository by listing all packages in a specific distribution:

```bash
reprepro -b /path/to/vicharak-apt-repository list <codename>
```

Where:
- `<codename>`: The codename for the distribution (e.g., `stable`, `stable-axon`, `stable-vaaman`).
- `<package.deb>`: The name of the Debian package file.

# Steps to Remove Debian Packages from Repository

---

### Step 1: Identify the Package to Remove

First, identify the exact package name and version you wish to remove from the repository. You can list all packages in a specific distribution:

```bash
reprepro -b /path/to/vicharak-apt-repository list <codename>
```

### Step 2: Remove the Package from the Repository

Once you have identified the package, use the remove command to remove it from the repository.

```bash
reprepro -b /path/to/vicharak-apt-repository remove <codename> <package-name>
```

Where:
- `<codename>`: The codename for the distribution (e.g., `stable`, `stable-axon`, `stable-vaaman`).
- `<package.deb>`: The name of the Debian package file.
>>>>>>> c4c9672 (vicharak-apt: updated vicharak-apt-repository to use reprepro.)
