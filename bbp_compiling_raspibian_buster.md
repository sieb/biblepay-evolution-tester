# Biblepay Raspbian Buster compiling

__Device__: Raspbery pi 3

__system information__
Distributor ID:	Raspbian
Description:	Raspbian GNU/Linux 10 (buster)
Release:	10
Codename:	buster
triplet: arm-linux-gnueabihf

#### workflow
_(look all outputs on 'bbp_compiling_raspibian_buster_LOG.md' file)_

reference: https://github.com/biblepay/biblepay/blob/master/BuildBiblePay.txt

__installing Ubuntu dependencies:__


```sh
sudo apt-get install autoconf libevent-dev libtool libssl-dev libboost-all-dev libminiupnpc-dev git

sudo apt-get install build-essential autotools-dev automake pkg-config bsdmainutils

sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev

sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler

sudo apt-get install curl build-essential libtool autotools-dev automake pkg-config python3 bsdmainutils cmake

```

__Building Daemon and QT__

```sh
git clone http://github.com/biblepay/biblepay
```

__RandomX Part__

```sh
cd biblepay/src/crypto/RandomX
mkdir build && cd build
cmake -DARCH=native ..
make
cd ../../../..
```

```sh
prefix=arm-linux-gnueabihf
cd depends
make -j 4
cd ..
./autogen.sh
./configure --prefix `pwd`/depends/arm-linux-gnueabihf
```
## ERROR alfa

```sh
checking whether bswap_64 is declared... yes
checking for MSG_NOSIGNAL... yes
checking for mallopt M_ARENA_MAX... yes
checking for visibility attribute... yes
checking for Linux getrandom syscall... yes
checking for getentropy... yes
checking for sysctl KERN_ARND... no
checking for Berkeley DB C++ headers... no
configure: error: libdb_cxx headers missing, BiblePay Core requires this library for wallet functionality (--disable-wallet to disable wallet functionality)

```
