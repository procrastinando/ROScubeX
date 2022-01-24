# ROScubeX
A guide to get started with ROS Cube X
## 1. Flash Jetpack
### Requirements:
- Host PC with Ubuntu 18.04 or 20.04
- Micro USB cable
- Two pins to press the Recovery and Reset buttons
- [Download](https://www.adlinktech.com/Products/ROS2_Solution/ROS2_Controller/ROScube-X?lang=en) the JetPack version for RQX-580 or RQX-58G
### Procedure:
- Use the pins to press the RESET and RECOVERY buttons, then release them
- ![](https://github.com/procrastinando/ROScubeX/blob/main/docs/reset.png)
- Connect the micro USB cable (PC host USB to ROScubeX OTG)
- Verify that the ROScubeX is in recovery mode
```Shell
lsusb
```
- In recovery mode NVIDIA Corp. is found:
- ![](https://github.com/procrastinando/ROScubeX/blob/main/docs/recovery.png)
- In normal mode L4T (Linux for tegra) is found:
- ![](https://github.com/procrastinando/ROScubeX/blob/main/docs/norecovery.png)
- Once is in recovery mode, run the next commands in the Host PC:
```Shell
sudo apt install python qemu-user-static
tar xvf mfi_rqx580_nvidia-ubuntu-rootfs-bionic_L4T-32-4-3-Kernel-1-0-7.tbz2
cd mfi_rqx_580
sudo ./nvmflash.sh
```
## 2. Initial setup:
- Once the initial setup is complete, proceed to update the system using the default update application
- Reboot
- Run the next commands:
```Shell
sudo apt install nvidia-jetpack
sudo apt install python-pip python-dev build-essential
sudo pip install --upgrade pip
sudo pip install jetson-stats
```
- Reboot
## 3. Install OpenCV CUDA
- [This](https://github.com/Hexerpowers/Install-OpenCV-Jetson-Xavier) repository contains the scripts to install OpenCV 4.5 with CUDA
- Run the commands (this procedure will take about 5 hours):
```Shell
sudo chmod 755 ./OpenCV-4-5-4.sh
./OpenCV-4-5-4.sh
```
## 4. Install Pytorch 1.10
- [This](https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-10-now-available/72048) forum link contains the latest versions
- Run the folowing commands:
```Shell
wget https://nvidia.box.com/shared/static/fjtbno0vpo676a25cgvuqc1wty0fkkg6.whl -O torch-1.10.0-cp36-cp36m-linux_aarch64.whl
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev
pip3 install Cython
pip3 install numpy torch-1.10.0-cp36-cp36m-linux_aarch64.whl
```
- Install TorchVision:
```Shell
sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
git clone --branch v0.11.1 https://github.com/pytorch/vision torchvision
cd torchvision
export BUILD_VERSION=0.11.1
python3 setup.py install --user
cd ../
```
## 5. oToCAM drivers:
- Install the debian package
```Shell
sudo apt install ./otocam-imx390isp-gmsl-v0.01.01.deb
```
- After rebooting run the next commands to find the connected cameras, for example: ```1. oToCAM IMX390ISP GMSL Kmod```
```Shell
sudo python3 /opt/nvidia/jetson-io/conﬁg-by-hardware.py -l
sudo python3 /opt/nvidia/jetson-io/conﬁg-by-hardware.py -n "oToCAM IMX390ISP GMSL Kmod"
```
- Reboot
- Try the camera and OpenCV
```Shell
python3 runcamera.py
```
