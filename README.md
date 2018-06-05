# mimg (Image Mounter / Partitioner)
[![benOSShield-Official](https://img.shields.io/badge/benOS-Native-brightgreen.svg)](https://github.com/benchOS/benOS)[![benOSShield-Utils](https://img.shields.io/badge/benOS-Utils-brightgreen.svg)](https://github.com/benchOS/benOS)[![build status](http://img.shields.io/travis/benchOS/mimg.svg?style=flat)](http://travis-ci.org/benchOS/mimg)[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
[![benOSRepoHeader](https://raw.githubusercontent.com/benchOS/benchOS-design/master/repo-headers/benos-mimg-header.png)](https://github.com/benchOS/mimg)
<br>
benOS Native Executable For Mounting and Partitioning Images.


## Table of Contents

- [Background](#background)
- [Installation](#installation)
- [Usage](#usage)
- [API](#api)
- [Related Projects](#related-projects)
- [Why Decentralized Internet](#why-the-internet-must-have-a-decentralized-alternative)
- [Bench On The dWeb](#bench-on-the-dweb)
- [License](#license)
- [Copyright](#license)

## Background
benOS Native Executable For Mounting and Partitioning Images.
[![mimgTerminalScreen](https://raw.githubusercontent.com/benchOS/benchOS-design/master/terminal-screens/mimg.png)](https://github.com/benchOS/mimg)

### With NPM
```
npm install -g mimg
```

### With YARN
```
yarn add global mimg
```

### Download Executable Directly
```
curl -fs https://raw.githubusercontent.com/benchOS/mimg/master/install | sh
```

## Usage

### CLI Menu
```
benOS Image Mounter & Partitioner
Usage: mimg <image> <mnt> [options]

 --partition, -p [partition-number]
 --force, -f     (force mount)
 --read-only, -r (read-only mount)
```

### Basic Usage

Use it just as you would mount but instead of passing a `/dev` device
pass a disk image file.

``` sh
mimg ubuntu.img mnt
```

To mount an OS image to a specific partition, use the `-p` parameter.

``` sh
# mount partition 5
mimg ubuntu.img mnt -p 5
```

### Creating IMG Files

To create raw image files you can use `fallocate`

``` sh
# make a ~1gb image
fallocate ubuntu-16-04.img -l 1000000000
```

Then using `fdisk` you can make a partition table

``` sh
# to simply make a single partition, follow this
fdisk ubuntu-16-04.img
n<enter>
<enter>
<enter>
<enter>
w<enter>
```


### Tips For Creating IMG Files

- You can always make more than one partition and use one to for the OS itself and boot.
- Always use [ext4](https://en.wikipedia.org/wiki/Ext4) for partition formatting.

#### Finalizing & Mounting
You can prepare the image for mounting and then mount this image using `mimg`

``` sh
fdisk -l ubuntu-16-04.img
mkfs.ext4 -F -E offset=$((2048 * 512)) ubuntu-16-04.img
```

``` sh
mimg ubuntu-16-04.img mnt
```


## Related Projects
- [benOS](https://github.com/benchOS/benOS) - benOS Decentralized Operating System
- [benny](https://github.com/benchOS/dpack-logger) - benOS Native Container Builder
- [gospawn](https://github.com/distributedweb/gospawn) - Bootstrap Spawner For Benny
- [bennyfile](https://github.com/distributedweb/bennyfile) - Build File Library For Benny Containers
- [thinbit](https://github.com/distributedweb/buffgap) - BitField Library For Benny

## Why The Internet Must Have A Decentralized Alternative
Today, the internet is more censored than ever and it's only getting worse. Our mission with the [dWeb Protocol](https://github.com/distributedweb/dweb) was to create a truly powerful P2P protocol, around [benOS](https://github.com/benchOS/benos), [dBrowser](https://github.com/benchOS/dbrowser) and many of benOS' underlying libraries to bring the most powerful P2P products to life. In the last few months, by rebuilding P2P technologies that have existed since the early 2000s, we have built a powerful suite of decentralized libraries for benOS and the Bench Network, that will only improve over time. But we also brought new ideas to life, like:

- [dDrive](https://github.com/distributedweb/ddrive)
- [dExplorer](https://github.com/distributedweb/dexplorer)
- [dDatabase](https://github.com/distributedweb/ddatabase)
- [dSites](https://github.com/distributedweb/dsites)
- [dPack](https://github.com/distributedweb/dpack)
- [benFS](https://github.com/benchOS/benfs)
- [DCDN](https://github.com/distributedweb/dcdn)
- [Rocketainer](https://github.com/distributedweb/rocketainer)
- [RocketOS](https://github.com/distributedweb/rocketos)
- [dNames](https://github.com/distributedweb/dnames)
- [P2PDNS](https://github.com/distributedweb/p2pdns)
- [dWebFS](https://github.com/distributedweb/dwebfs)
- [dWebDB](https://github.com/distributedweb/dwebdb)
- [MeteorIDE](https://github.com/distributedweb/meteorIDE)
- [Kepler](https://github.com/benchlab/kepler)
- [Neutron](https://github.com/benchlab/neutron)
- [Designate](https://github.com/benchlab/designate)
- [Nova](https://github.com/benchlab/nova)

and more! These were the protocols and libraries that we needed to create a completely decentralized operating system, where everything was distributed, protected and people were once again in control of their data. benOS is made up of over 1100+ different libraries that we are releasing on a day-by-day basis as we move them to a stable/production state. While financial support is great for this open source project, we need developers who want to be some of the first to build the `dApps` and `dSites` of the future. We have to take back what our forefathers originally designed for freedom, by making our code the law, instead of releasing weak and highly centralized applications where law cannot be applied because the code lacks the foundation to implement a legal framework for itself. Join us for a truly historic journey on the [BenchLabs Telegram](https://t.me/benchlabs). See you there.

### Bench On The dWeb
[dweb://bench.dnames.io](dweb://bench.dnames.io) // dNames Short Link
[dweb://3EDAE09848B77401445B7739CAFCE442DDE1752AED63025A1F94E6A86D7E9F04](dweb://3EDAE09848B77401445B7739CAFCE442DDE1752AED63025A1F94E6A86D7E9F04) // dWeb Key Link

In order to make the links above clickable or to view these links period, you will need [dBrowser](https://github.com/benchOS/dbrowser) (Available for Mac OSX, Linux, Windows and soon to be available on iOS/Android)

#### "The Code Is The Law" - Stan Larimer - Godfather of BitShares.

## License
[MIT](LICENSE.md)
<br><br>
[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)
<br>
[![forthebadge](https://forthebadge.com/images/badges/made-with-javascript.svg)](https://js.distributedwebs.org)
<br>
[![dWebShield](https://github.com/benchlab/dweb-shields/blob/master/shields/dweb-protocol-shield.svg)](https://github.com/distributedweb/dweb)

## Copyright
Copyright (c) 2018 Bench Open Systems. All rights reserved.
