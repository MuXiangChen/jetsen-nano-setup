
# clash

https://github.com/Fndroid/clash_for_windows_pkg/releases
./cfw launch


# vscode

https://code.visualstudio.com/docs/setup/linux
download file arm64 deb
sudo dpkg -i <file>.deb
sudo apt-get install -f 

# qq

https://im.qq.com/linuxqq/download.html
sudo dpkg -i <file>.deb

# cmake

sudo apt update
sudo apt install build-essential libtool autoconf unzip wget

Downloading cmake3.14 from ‘Download | CMake 467’
https://cmake.org/download/

A-1. Uninstall the default version provided by Ubuntu's package manager and configuration by using:

sudo apt remove --purge --auto-remove cmake

B-2. Go to the official CMake webpage, then download and extract the latest version. Update the version and build variables in the following command to get the desired version:

B-3. Install the extracted source by running:

./bootstrap
make -j$(nproc)
sudo make install

B-4. Test your new cmake version.

cmake --version


# cuda

https://jfrog.com/connect/post/installing-cuda-on-nvidia-jetson-nano/

https://dev.to/ajeetraina/install-cuda-on-jetson-nano-2b06

wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/sbsa/cuda-ubuntu1804.pin
sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.3.1/local_installers/cuda-repo-ubuntu1804-11-3-local_11.3.1-465.19.01-1_arm64.deb
sudo dpkg -i cuda-repo-ubuntu1804-11-3-local_11.3.1-465.19.01-1_arm64.deb
sudo apt-key add /var/cuda-repo-ubuntu1804-11-3-local/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda

sudo apt-get -o dpkg::Options::="--force-overwrite" install --fix-broken

dpkg -l | grep cuda

cd /usr/local/cuda
cuda/      cuda-10/   cuda-10.2/ cuda-11/   cuda-11.0/ cuda-11.3/

export PATH=/usr/local/cuda-12.0/bin${PATH:+:${PATH}}


# open3d

sudo apt-get update -y
sudo apt-get install -y apt-utils build-essential git cmake
sudo apt-get install -y python3 python3-dev python3-pip
sudo apt-get install -y xorg-dev libglu1-mesa-dev
sudo apt-get install -y libblas-dev liblapack-dev liblapacke-dev
sudo apt-get install -y libsdl2-dev libc++-7-dev libc++abi-7-dev libxi-dev
sudo apt-get install -y clang-7

git clone https://github.com/intel-isl/Open3d.git

util/install_deps_ubuntu.sh

cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DBUILD_LIBREALSENSE=ON -DBUILD_CUDA_MODULE=ON -DBUILD_GUI=ON -DBUILD_TENSORFLOW_OPS=OFF -DBUILD_PYTORCH_OPS=OFF -DBUILD_UNIT_TESTS=ON -DCMAKE_INSTALL_PREFIX=~/open3d_install -DPYTHON_EXECUTABLE=$(which python3) ..

make -j$(nproc)


# python multiple version

https://cloudbytes.dev/snippets/upgrade-python-to-latest-version-on-ubuntu-linux

# waveshare

7. install python 3.7 for waveshare UPS
8. update-alternative select 3.7 manual
9. install python header files
sudo apt-get install python-dev
sudo apt-get install python3-dev
sudo apt-get install python3.7-dev
10. fix turminal cant open
ctrl+alt+F3
sudo vim /usr/bin/gnome-terminal
Change #!/usr/bin/python3 to #!/usr/bin/python3.6.
11. chagne python
sudo update-alternatives --config python3
12. install pip
https://linuxize.com/post/how-to-install-pip-on-ubuntu-18.04/
13. update setuptools
http://rolk.github.io/2018/10/25/setuptools
python3 -m pip install --upgrade setuptools
sudo apt-get install python3-setuptools
sudo apt-get install python-setuptools
python3 -m pip install --upgrade pip setuptools wheel
1. DOCS  https://www.waveshare.com/wiki/UPS_Power_Module
2. git clone https://github.com/waveshare/UPS-Power-Module
cd UPS-Power-Module
sudo ./install.sh
3. manual install

set -e

password=$1

- enable i2c permissions
echo $password | sudo -S usermod -aG i2c $USER

- install pip and some apt dependencies
echo $password | sudo -S apt-get update
echo $password | sudo -S apt install -y python3-pip python3-pil python3-smbus
echo $password | sudo -S pip3 install flask

- install ups_display
echo $password | sudo -S python3 setup.py install

- install UPS_Power_Module display service
python3 -m ups_display.create_display_service
echo $password | sudo -S mv ups_display.service /etc/systemd/system/ups_display.service
echo $password | sudo -S systemctl enable ups_display
echo $password | sudo -S systemctl start ups_display

!!!!!!!!!!!!!!! sudo -H pip3 install flask
!!!!!!!!!!!!!!! pip install flask
!!!!!!!!!!!!!!! systemctl status ups_display
!!!!!!!!!!!!!!! sudo -H pip3 install Pillow
!!!!!!!!!!!!!!! sudo -H pip3 install markupsafe==1.0
!!!!!!!!!!!!!!! sudo -H pip3 install smbus

move ups_display folder to home

finished !!!!!!