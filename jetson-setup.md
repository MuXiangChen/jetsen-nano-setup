
# custum jetson nano image

# remove apt update source

sudo nano /etc/apt/sources.list

# remove app

https://www.howtogeek.com/229699/how-to-uninstall-software-using-the-command-line-in-linux/

dpkg -l | grep qq
sudo apt-get remove linuxqq


# system monitor
sudo apt-get install gnome-system-monitor


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
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF7F09730B3F0A4
sudo apt update
sudo apt install cmake

cmake --version

# realsense

sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE

sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo bionic main" -u

sudo apt-get install librealsense2-utils
sudo apt-get install librealsense2-dev

g++ -std=c++11 filename.cpp -lrealsense2

# cuda

export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64\
                         ${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

# python multiple version

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

# path environment

sudo vim /etc/environment

# open3d

https://www.hackster.io/devshank/jetscan-16a521

pythone version 3.7 3.8 3.9 3.10

sudo apt-get update -y

sudo apt-get install -y apt-utils build-essential git xorg-dev libglu1-mesa-dev libblas-dev liblapack-dev liblapacke-dev libsdl2-dev libc++-7-dev libc++abi-7-dev libxi-dev clang-7

git clone https://github.com/intel-isl/Open3d.git

util/install_deps_ubuntu.sh

mkdir build
cd build

cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON -DBUILD_LIBREALSENSE=ON -DBUILD_CUDA_MODULE=ON -DBUILD_GUI=ON -DBUILD_TENSORFLOW_OPS=OFF -DBUILD_PYTORCH_OPS=OFF -DBUILD_UNIT_TESTS=ON -DCMAKE_INSTALL_PREFIX=~/open3d_install -DPYTHON_EXECUTABLE=$(which python3) ..

make -j$(nproc)

make install
make install-pip-package
make python-package
make pip-package
python -c "import open3d"


# waveshare

sudo pip3 uninstall Pillow
sudo -H pip3 install Pillow
sudo -H pip3 install smbus

1. DOCS  https://www.waveshare.com/wiki/UPS_Power_Module
2. git clone https://github.com/waveshare/UPS-Power-Module
cd UPS-Power-Module
sudo ./install.sh
3. manual install
