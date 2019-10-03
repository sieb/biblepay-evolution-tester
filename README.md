BiblePay Clone staging tree 0.13.0
===============================


For information on the original project read README_original.md

The purpose of this biblepay project clone is to provide basic instructions for building a raspberry pi 3, OS Raspbian stretch (lite-headless). 
I used this great [tutorial](https://www.reddit.com/r/BiblePay/comments/7qnbp4/bbp_miner_on_pi/) and other [information](https://bitcointalk.org/index.php?topic=2388064) as a base of information but I had to create some things to make it work.
I also make the compiled binaries available in src2 directory (if you're not afraid to do so!).

***

## Install dependencies

`$ sudo apt-get install curl build-essential libtool autotools-dev automake pkg-config python3 bsdmainutils cmake`
 
 * Download Latest Release here and untar/unzip
 
 `https://github.com/biblepay/biblepay-evolution/releases/tag/1.4.4.8`

 Change for depends dir into biblepay-evolution:

 `$ cd depends`

 and

 `$ make HOST=arm-linux-gnueabihf -j4`

  and too

 `./configure --prefix=`pwd`/depends/arm-linux-gnueabihf`

## Building BiblePay Core

`cd ..` go back to biblepay-evolution dir.

`$ ./autogen.sh`

`$ ./configure --prefix `pwd`/depends/arm-linux-gnueabihf`

`$ make`

After many hours (use screen to move from terminal in the meantime) and only then enter src folder and start daemon:

`pi@raspberrypi:~/biblepay-evolution/src $ ./biblepayd -daemon`

Wait for the entire blockchain to load (no larger than 1.4Gb) and add this file (biblepay.conf) to the hidden directory that was created .biblepaycore or .biblepayevolution (if there are both added in both)

## Mining and poll

Create account in http://pool.biblepay.org/ and create a [worker set to funded, 1](https://whitewalr.us/2019/pobh-funded-mining.html).

Create `biblepay.conf` 

```
addnode=node.biblepay-explorer.org
gen=1
genproclimit=4
poolport=80
pool=https://pool.biblepay.org
workerid=yourworkername
workeridfunded=yourworkername
```
To know the commands:

`./biblepay-cli help`

***
If you like and want to send me some bbp feel free to. 
My address is `BNPA5qQ6729vHtZsiUtYtpAJ65y5MgxpJh`
