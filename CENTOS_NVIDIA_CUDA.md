#1. Preparation  
准备x86服务器，安装GPU，我们准备的图形卡是GP102 [GeForce GTX 1080 Ti] (rev a1)  

#2. 安装操作系统
核心版本3.10.0-957.el7.x86_64  
操作系统CentOS Linux release 7.6.1810 (Core)  

#3. 安装GCC  
yum group install "Development Tools"  
yum install kernel-devel kernel-headers epel-release dkms

#4. 安装显卡驱动
##4.1 禁自带nouveau驱动  
vi /etc/default/grub Append the following to the GRUB_CMDLINE_LINUX line:modprobe.blacklist=nouveau  
##4.2 BIOS USER run this Rebuild the grub config "grub2-mkconfig -o /boot/grub2/grub.cfg"  
##4.3 安装NVIDIA驱动  
驱动下载地址：https://www.nvidia.com/Download/index.aspx?lang=en-us  
bash NVIDIA-Linux-x86_64-430.34.run --kernel-source-path=/usr/src/kernels/3.10.0-957.21.3.el7.x86_64 -k $(uname -r)  

#5. 安装CUDA  
CUDA下载地址：https://developer.nvidia.com/cuda-downloads  
安装CUDA：  
rpm -ivh cuda-repo-rhel7-10-0-local-10.0.130-410.48-1.0-1.x86_64.rpm

#6. 安装cuDNN  
cuDNN下载地址：  
https://developer.download.nvidia.cn/compute/machine-learning/cudnn/secure/v7.6.1.34/prod/10.0_20190620/cudnn-10.0-linux-x64-v7.6.1.34.tgz?4iENE3dJjKqAzonaYt1dMgc8_YAvmnJ8X8-jIGflt7wZqW7U1_ZxuLNrY4fp61h1Qa3fx0nSnUm8p8a-whCwWLvhBJRI1FdbkrQ5mj0pBzDZEqVYEwQ3SD9qTn_YK_EH75Tuv7sTTGZ6HhpJ7UXmK9yIp5P5QTPh8AB4zn0JAU5hijez5bY9dXFVvZ-Pf6BYwj1iIGbfav_DfSxJE0CPpx4ByfQ  
安装cudnn-10.0-linux-x64-v7.6.1.34.tgz  
解压cudnn-10.0-linux-x64-v7.6.1.34.tgz  
cp cuda/include/cudnn.h /usr/local/include/  
cp cuda/lib64/libcudnn* /usr/local/lib64/  
chmod a+r /usr/local/include/cudnn.h /usr/local/lib64/libcudnn*  



