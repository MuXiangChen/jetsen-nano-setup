
# setup nano

- download card image:
https://developer.nvidia.com/jetson-nano-sd-card-image

- download SD card formatter:
https://www.sdcard.org/downloads/formatter_4/eula_windows/

- download flash tool:
https://www.balena.io/etcher

# increase memory

memory issue jetson nano only has 4g memory, restart and build again, cmake will continue

or increase swap size
https://ploi.io/documentation/server/change-swap-size-in-ubuntu

1. Turn off all running swap processes: swapoff -a
2. Resize swap fallocate -l 1G /swapfile (change 1G to the gigabyte size you want it to be)
3. CHMOD swap: chmod 600 /swapfile
4. Make file usable as swap mkswap /swapfile
5. Active the swap file swapon /swapfile

sudo swapoff -a
sudo fallocate -l 30G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

To verify your swap size run the following command and you will see the swap size: free -m

# clash

https://github.com/Fndroid/clash_for_windows_pkg/releases
./cfw launch

terminal proxy

export http_proxy='http://127.0.0.1:7890'    
export https_proxy='http://127.0.0.1:7890'

unset http_proxy
unset https_proxy

# vscode

https://code.visualstudio.com/docs/setup/linux
download file arm64 deb
sudo dpkg -i <file>.deb
sudo apt-get install -f 

# qq

https://im.qq.com/linuxqq/download.html
sudo dpkg -i <file>.deb

# cmake

https://askubuntu.com/questions/355565/how-do-i-install-the-latest-version-of-cmake-from-the-command-line

sudo apt remove --purge --auto-remove cmake

sudo apt update && \
sudo apt install -y software-properties-common lsb-release && \
sudo apt clean all

wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | sudo tee /etc/apt/trusted.gpg.d/kitware.gpg >/dev/null

sudo apt-add-repository "deb https://apt.kitware.com/ubuntu/ $(lsb_release -cs) main"

sudo apt update
sudo apt install kitware-archive-keyring
sudo rm /etc/apt/trusted.gpg.d/kitware.gpg

sudo apt update
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF7F09730B3F0A4

sudo apt install cmake

cmake --version

# realsense

sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE

sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo bionic main" -u

sudo apt-get install librealsense2-utils
sudo apt-get install librealsense2-dev

g++ -std=c++11 filename.cpp -lrealsense2

# cuda

export CUDA_HOME=/usr/local/cuda/${PATH:+:${PATH}}
export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

# python multiple version

python 3.6 is pre-installed
python 3.10 for Open3D v0.17.0
python 3.7 for UPS-Power-Module

https://cloudbytes.dev/snippets/upgrade-python-to-latest-version-on-ubuntu-linux

sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update

sudo apt install python3.10
sudo apt install python3.7

sudo apt-get install python-dev
sudo apt-get install python3-dev
sudo apt-get install python3.7-dev
sudo apt-get install python3.10-dev

python3 --version

sudo vim /usr/bin/gnome-terminal
change #!/usr/bin/python3 to #!/usr/bin/python3.6

sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 1
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 2
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 3

sudo update-alternatives --config python3

- Fix pip and disutils errors

sudo apt remove --purge python3-apt
sudo apt autoclean
sudo apt install python3-apt
sudo apt install python3.10-distutils
sudo apt install curl
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python3.10 get-pip.py
pip --version
sudo apt install python3.10-venv

If you have oh-my-zsh installed, you can avoid typing out python3 by running

echo "alias py=/usr/bin/python3" >> ~/.zshrc
echo "alias python=/usr/bin/python3" >> ~/.zshrc
Now you can run your files with py or python.

# path environment check

sudo vim /etc/environment

# opencv-python

sudo -H python3 -m pip install opencv-python

# open3d

git clone https://github.com/intel-isl/Open3D.git

sudo Open3D/util/install_deps_ubuntu.sh

- activate venv
jasmine@jasmine-desktop:~/Open3D$ python3 -m venv .venv
jasmine@jasmine-desktop:~/Open3D$ source .venv/bin/activate

mkdir build && cd build

cmake -DBUILD_LIBREALSENSE=ON -DBUILD_CUDA_MODULE=ON -DBUILD_GUI=ON -DBUILD_AZURE_KINECT=ON ..

make -j$(nproc)

make install
make install-pip-package
make python-package
make pip-package
python -c "import open3d"

## opencv error

from matplotlib import pyplot as plt  # for visualizing feature matching
  File "/usr/lib/python3/dist-packages/matplotlib/__init__.py", line 107, in <module>
    from collections import MutableMapping
ImportError: cannot import name 'MutableMapping' from 'collections' (/usr/lib/python3.10/collections/__init__.py)

fix: 

If you don't want to modify the matplotlib library code, you can try using an older version of the library that is compatible with your version of Python.

For example, if you are using Python 3.10, you can try installing an older version of matplotlib that does not use MutableMapping.

To do this, you can use the following command in your terminal or command prompt:

sudo -H python3 -m pip install matplotlib==3.4.3

## joblib problem

ValueError: setting an array element with a sequence. The requested array would exceed the maximum number of dimension of 1.




## opsource project
https://www.hackster.io/devshank/jetscan-16a521

## if can't find CUDA
add cuda to path

## if can't download sth
use VPN

## freeze problem
need large memory
set swap memory

## previous encontered problems

/*

https://www.hackster.io/devshank/jetscan-16a521

pythone version 3.7 3.8 3.9 3.10

sudo apt-get update -y

sudo apt-get install -y ccache apt-utils build-essential git xorg-dev libglu1-mesa-dev libblas-dev liblapack-dev liblapacke-dev libsdl2-dev libc++-7-dev libc++abi-7-dev libxi-dev clang-7

git clone https://github.com/intel-isl/Open3D.git

util/install_deps_ubuntu.sh

mkdir build
cd build

### python path problem
import sys
print(sys.path)

### 100 errors detected in the compilation of "/tmp/tmpxft_00000289_00000000-6_ParallelFor.cpp1.ii".
https://github.com/isl-org/Open3D/issues/4516
 caused by eigen using wrong version of cuda
 https://www.hackster.io/devshank/jetscan-16a521
- uninstall eigen3
sudo apt-get uninstall eigen3
- install eigen3 ver - 3.3.7
https://apolo-docs.readthedocs.io/en/latest/software/scientific_libraries/eigen/eigen-3.3.7/index.html

$ wget https://gitlab.com/libeigen/eigen/-/archive/3.3.7/eigen-3.3.7.tar.gz
$ tar -xzvf eigen-3.3.7.tar.gz

$ cd eigen-3.3.7
$ mkdir build
$ cd build

$ cmake ..

$ sudo make -j$(nproc) install

add this line
cmake -DUSE_SYSTEM_EIGEN3=ON..

### cpp/open3d/core/CMakeFiles/core.dir/build.make:999: recipe for target 'cpp/open3d/core/CMakeFiles/core.dir/kernel/BinaryEWCUDA.cu.o' failed
[ 45%] Building CXX object cpp/open3d/core/CMakeFiles/core.dir/linalg/InverseCUDA.cpp.o
Killed
cpp/open3d/core/CMakeFiles/core.dir/build.make:999: recipe for target 'cpp/open3d/core/CMakeFiles/core.dir/kernel/BinaryEWCUDA.cu.o' failed

by chatgpt:

The error message you provided suggests that the build process was terminated unexpectedly during the compilation of a CUDA file named "BinaryEWCUDA.cu".

The message "Killed" usually indicates that the process was terminated by the Linux kernel due to lack of system resources, such as memory or CPU time.

Here are some steps you can take to resolve the issue:

1. Check if there is enough free memory and CPU time available on the system. You can use the free and top commands to check the current memory usage and CPU usage, respectively. If the system is low on memory, you may need to close other memory-intensive applications or increase the amount of available memory on the system. If the system is low on CPU time, you may need to wait for other processes to complete or reduce the number of running processes.
2. Try reducing the number of parallel build jobs by specifying a lower value for the -j option of the make command. For example, you can try running make -j2 instead of make -j$(nproc). This will reduce the amount of system resources used by the build process and may prevent the "Killed" error.
3. Check if the build settings or source code are causing excessive memory usage during the compilation process. This can happen if the code is using large data structures or making frequent allocations. If this is the case, you may need to optimize the code or modify the build settings to reduce memory usage.
4. If the issue persists, you can try running the build process on a system with more memory or CPU resources.
Once you have resolved the issue, you can retry the build process.

### freeze problem

memory issue jetson nano only has 4g memory, restart and build again, cmake will continue

or increase swap size
https://ploi.io/documentation/server/change-swap-size-in-ubuntu

1. Turn off all running swap processes: swapoff -a
2. Resize swap fallocate -l 1G /swapfile (change 1G to the gigabyte size you want it to be)
3. CHMOD swap: chmod 600 /swapfile
4. Make file usable as swap mkswap /swapfile
5. Active the swap file swapon /swapfile

To verify your swap size run the following command and you will see the swap size: free -m

## Open3D/cpp/open3d/geometry/Line3D.h:117:9: error: ‘transform’ was not declared in this scope
https://github.com/isl-org/Open3D/issues/2487

eigen version problem change the code and fix the problem

-DUSE_SYSTEM_EIGEN3=ON and change this->transform(t) to this->Transform(t)

### fmt error
https://github.com/isl-org/Open3D/issues/5205
https://github.com/isl-org/Open3D/pull/5303
could you check -DUSE_SYSTEM_FMT=ON configuration? I do see build error when libfmt being shared library. cf #5622 (comment)

This PR updates the fmt::formatter specialization as documented in the fmtlib documentation for fmtlib >= 7, and fixes the build errors with fmtlib >= 8.

-DUSE_SYSTEM_FMT=ON


- manual install fmt latest version

https://fmt.dev/latest/usage.html#building-the-library

git clone https://github.com/fmtlib/fmt.git
git checkout 8.0.1
mkdir build 
cd build
cmake -DBUILD_SHARED_LIBS=TRUE -DCMAKE_POSITION_INDEPENDENT_CODE=TRUE ..  
sudo make install

wrong version

- uninstall fmt

cat install_manifest.txt | sudo xargs rm
cat install_manifest.txt | xargs -L1 dirname | sudo xargs rmdir -p


### final cmake command

cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DBUILD_LIBREALSENSE=ON -DBUILD_CUDA_MODULE=ON -DBUILD_GUI=ON -DBUILD_TENSORFLOW_OPS=OFF -DBUILD_PYTORCH_OPS=OFF -DBUILD_UNIT_TESTS=ON -DCMAKE_INSTALL_PREFIX=~/open3d_install -DPYTHON_EXECUTABLE=$(which python3) -DPYTHON_LIBRARY=/usr/lib/python3.10 -DPYTHON_INCLUDE_DIR=/usr/include/python3.10 -DPYTHON_EXECUTABLE:FILEPATH=/usr/bin/python3.10 -DUSE_SYSTEM_EIGEN3=ON -DUSE_SYSTEM_FMT=ON ..

still won't work

cmake ..

make -j$(nproc)

make install
make install-pip-package
make python-package
make pip-package
python -c "import open3d"



# waveshare UPS-Power-Module with OLED display

sudo pip3 uninstall Pillow
sudo -H pip3 install Pillow
sudo -H pip3 install smbus

1. DOCS  https://www.waveshare.com/wiki/UPS_Power_Module
2. git clone https://github.com/waveshare/UPS-Power-Module
cd UPS-Power-Module
sudo ./install.sh
3. manual install


# custum jetson nano image

https://askubuntu.com/questions/227924/sd-card-cloning-using-the-dd-command

Insert the original SD card and check the name of the device (usually mmcblkX or sdcX):

sudo fdisk -l
You might see:

Device         Boot   Start      End  Sectors  Size Id Type
/dev/mmcblk0p1 *       2048  2099199  2097152    1G  c W95 FAT32 (LBA)
/dev/mmcblk0p2      2099200 31116287 29017088 13.9G 83 Linux
In my case the SD card is /dev/mmcblk0 (the *p1 and *p2 are the partitions).

Now you have to unmount the device:

sudo umount /dev/mmcblk0
Now to create an image of the device:

sudo dd if=/dev/mmcblk0 of=~/sd-card-copy.img bs=1M status=progress
This will take a while.

Once it's finished, insert the empty SD card. If the device is different (USB or other type of SD card reader) verify its name and be sure to unmount it:

sudo fdisk -l
sudo umount /dev/mmcblk0
Write the image to the device:

sudo dd if=~/sd-card-copy.img of=/dev/mmcblk0 bs=1M status=progress
The write operation is much slower than before.

https://raspberrytips.com/create-image-sd-card/

– On Windows, use Win32 Disk Imager.
https://sourceforge.net/projects/win32diskimager/

1. Insert your SD card in your computer.

2. Find the partition letter corresponding to your SD card

3. Open Win 32 Disk Imager.

4. Start by choosing an image location and name for your image:



# install specific package version

https://itsfoss.com/apt-install-specific-version/

apt list --all-versions package_name
sudo apt install package_name=package_version


# remove apt update source

sudo nano /etc/apt/sources.list

# remove app

https://www.howtogeek.com/229699/how-to-uninstall-software-using-the-command-line-in-linux/

dpkg -l | grep qq
sudo apt-get remove linuxqq


# system monitor
sudo apt-get install gnome-system-monitor
