
- sharevpn
1. openhotspot
2. open clash
3. hotspotshare
4. proxy set computer ip & port
5. etc/apt/apt.conf  change https to http

- jetson setup
1. format sd card
2. flash firmware
3. start
4. proxy set computer ip & port
5. etc-apt-apt.conf.d -proxy.conf  change https to http
6. update python
https://cloudbytes.dev/snippets/upgrade-python-to-latest-version-on-ubuntu-linux
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


- waveshare UPS POWER MODULE
1. DOCS  https://www.waveshare.com/wiki/UPS_Power_Module
2. git clone https://github.com/waveshare/UPS-Power-Module
cd UPS-Power-Module
sudo ./install.sh

3. manual install

set -e

password=$1

# enable i2c permissions
echo $password | sudo -S usermod -aG i2c $USER

# install pip and some apt dependencies
echo $password | sudo -S apt-get update
echo $password | sudo -S apt install -y python3-pip python3-pil python3-smbus
echo $password | sudo -S pip3 install flask

# install ups_display
echo $password | sudo -S python3 setup.py install

# install UPS_Power_Module display service
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


- VSCODE
1. https://code.visualstudio.com/docs/setup/linux
2. download file arm64 deb
3. sudo dpkg -i <file>.deb
sudo apt-get install -f 

# If you're on an older Linux distribution, you will need to run this instead:
# sudo dpkg -i <file>.deb
# sudo apt-get install -f 



- clash for windows setup
https://github.com/Fndroid/clash_for_windows_pkg/releases
1.download linux cfw
2. ./cfw launch
3. settings
3. network
4. network proxy
5. 127.0.0.1  7890
6. clash set port 7890


- realsense setup

- open3d setup
1. util/install_deps_ubuntu.sh
2. install CUDA https://jfrog.com/connect/post/installing-cuda-on-nvidia-jetson-nano/

https://dev.to/ajeetraina/install-cuda-on-jetson-nano-2b06

export PATH=/usr/local/cuda-12.0/bin${PATH:+:${PATH}}
3. update cmake

sudo apt remove --purge cmake
sudo apt autoremove

Downloading cmake3.14 from ‘Download | CMake 467’
https://cmake.org/download/
tar zxcf cmake-3.14.0.tar.gz
cd cmake-3.14.0
sudo ./bootstrap //20 mimutes
sudo make
sudo make install
cmake --version //return the version of cmake

./bootstrap --system-curl
make -j3
sudo make install

4. 
3. cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DBUILD_LIBREALSENSE=ON -DBUILD_CUDA_MODULE=ON -DBUILD_GUI=ON -DBUILD_TENSORFLOW_OPS=OFF -DBUILD_PYTORCH_OPS=OFF -DBUILD_UNIT_TESTS=ON -DCMAKE_INSTALL_PREFIX=~/open3d_install -DPYTHON_EXECUTABLE=$(which python3) ..
4. make -j$(nproc)
5. 



sudo apt-get update -y
sudo apt-get install -y apt-utils build-essential git cmake
sudo apt-get install -y python3 python3-dev python3-pip
sudo apt-get install -y xorg-dev libglu1-mesa-dev
sudo apt-get install -y libblas-dev liblapack-dev liblapacke-dev
sudo apt-get install -y libsdl2-dev libc++-7-dev libc++abi-7-dev libxi-dev
sudo apt-get install -y clang-7


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

$ cmake --version



https://zenn.dev/ijiwarunahello/scraps/fee9925b443478

