#1. change env /etc/profile  
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig  
export PKG_CONFIG_PATH
CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/usr/local/include/leptonica  
export CPLUS_INCLUDE_PATH
C_INCLUDE_PATH=$C_INCLUDE_PATH:/usr/local/include/leptonica  
export C_INCLUDE_PATH  
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib  
export LD_LIBRARY_PATH  
LIBRARY_PATH=$LIBRARY_PATH:/usr/local/lib  
export LIBRARY_PATH  
LIBLEPT_HEADERSDIR=/usr/local/include/leptonica  
export LIBLEPT_HEADERSDIR  
TESSDATA_PREFIX=/root/tesseract/tessdata  
export TESSDATA_PREFIX  

#2. yum install deps  
yum install automake autoconf gcc-c++ libtool pkg-config git  
yum install libtiff-devel libjpeg-devel libpng-devel openjpeg2 ImageMagick  

#3. lstm models  
git clone https://github.com/tesseract-ocr/tessdata.git  

#4. deps  
git clone https://github.com/DanBloomberg/leptonica.git  
http://www.leptonica.org/source/README.html  

#5. install g++ 5.1  
[warning:fedora]  
name=fedora  
mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=fedora-23&arch=$basearch  
enabled=1  
gpgcheck=0  
gpgkey=https://getfedora.org/static/34EC9CBA.txt  

#6. install tesseract  
git clone https://github.com/tesseract-ocr/tesseract.git 

#7. convert pdf to jpg  
convert   -density 150  ar.pdf ar.jpg  

#8. ocr it.  
tesseract ar-0.jpg result -l chi_sim --oem 1
