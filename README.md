WHAT IS THIS?
=============

Linux Kernel source code for the device bq Aquaris E5 Ubuntu Edition

BUILD INSTRUCTIONS?
===================

Getting the dependencies
------------------------

Your Ubuntu environment is expected to contain a similar setup to that
used for flashing ubuntu devices (see [1], installing phablet-tools
ppa). You will need at least two other components installed:

    $ sudo apt-get install gcc-arm-linux-androideabi abootimg

If you are not using Xenial (16.04) but a more recent version of Ubuntu, the
above command will not work: just install

    $ sudo apt-get install abootimg

and get the Android ARM compiler from
[upstream](https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9).
Note that you need to pick an older version of the toolchain, as newer ones do
not contain `gcc` (they come with `clang` only). It has been verified that the
version tagged `android-6.0.1_r21` works; you can download it from [here](https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9/+archive/a0cb3720e4047bade36f8cfac84ea94715313a89.tar.gz). After unpacking it:

    $ export PATH=<where you unpacked the archive>/bin

You also need to have python2.7 as your default python interpreter; see [this
question](https://askubuntu.com/questions/1296611/how-to-create-python2-7-virtualenv-on-ubuntu-20-04)
and the related answer for a suggestion on how to set it up.

Building
--------

Specific sources are organised by branch and comments in the
commits. First, you should clone the project:

    $ git clone git@github.com:bq/aquaris-E5.git

After it, choose the branch you would like to build:

    $ cd aquaris-E5/
    $ git checkout aquaris-E5-ubuntu-master

Then, build the kernel:

    $ ./makeMtk -t vegetahd n k

You can build a flashable image with

    $ cd testboot
    $ ./mkbootimg.sh vegetahd

You can flash this with:

    $ fastboot flash boot boot.img

[1]: https://developer.ubuntu.com/en/start/ubuntu-for-devices/installing-ubuntu-for-devices/
