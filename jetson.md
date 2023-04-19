
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
3. sudo apt-get -o Dpkg::Options::="--force-overwrite" install --fix-broken
4. 

1. python3 -m pip install open3d
1. git clone https://github.com/isl-org/Open3D.git
2. util/install_deps_ubuntu.sh
3. cmake -DBUILD_GUI=ON -DBUILD_CUDA_MODULE=ON -DBUILD_LIBREALSENSE=ON ..

https://zenn.dev/ijiwarunahello/scraps/fee9925b443478

