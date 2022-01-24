# ROScubeX
A guide to get started with ROS Cube X
## 1. Flash Jetpack
### Requirements:
- Host PC with Ubuntu 18.04 or 20.04
- Micro USB cable
- Two pins to press the Recovery and Reset buttons
- [Download](https://www.adlinktech.com/Products/ROS2_Solution/ROS2_Controller/ROScube-X?lang=en) the JetPack version for RQX-580 or RQX-58G.
### Procedure:
- Use the pins to press the RESET and RECOVERY buttons, then release them
![reset](https://github.com/procrastinando/ROScubeX/blob/master/reset.png)
- Connect the micro USB cable (PC host USB to ROScubeX OTG)
- Verify that the ROScubeX is in recovery mode
```Shell
lsusb
```
In recovery mode NVIDIA Corp. is found:
![recovery](https://github.com/procrastinando/ROScubeX/blob/master/recovery.png)
In normal mode L4T (Linux for tegra) is found:
![norecovery](https://github.com/procrastinando/ROScubeX/blob/master/norecovery.png)
