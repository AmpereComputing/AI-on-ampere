# Pytorch on aarch64

Steps or scripts to run Pytorch on Ampere aarch64

## Installation

1: Install Ubuntu18.04 on Ampere aarch64

2: Install GUI  
   apt install ubuntu-mate-core ubuntu-mate-desktop  
   or  
   tasksel , and select gnome or mate

3: Install VNC or just use graphic card  
   apt install -y vnc4server

4: Install nessesary lib  
   apt install -y git zip python3-numpy python3-dev python3-pip python3-wheel build-essential cmake libnuma-dev python3-yaml python3-pillow python3-scipy python3-opencv python3-matplotlib  
   apt install -y libssl-dev libffi-dev libxml2 libxml2-dev libxslt1-dev zlib1g-dev  
   apt install -y freeglut3-dev libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev
   
5: Install CUDA  
   Download CUDA from <https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=sbsa>  
   Refer to <https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#abstract> for detail

6: Install NCCL  
   Download NCCL from <https://developer.nvidia.com/nccl/nccl-download>  
   refer to <https://docs.nvidia.com/deeplearning/sdk/nccl-install-guide/index.html> for detail

7: Install torch and torchvision  
   pip3 install *.whl


## Compile
   git clone https://github.com/pytorch/pytorch.git  
   cd pytorch  
   git checkout -b my-v1.5.0 v1.5.0  
   git submodule sync  
   git submodule update --init --recursive  
   (apply pytorch_aarch64.patch)  
   export NO_CUDA=1  (if no graphic card)  
   export USE_NCCL=0  (if no graphic card)  
   python3 setup.py install  
   python3 setup.py bdist_wheel  


   git clone https://github.com/pytorch/vision.git  
   cd vision  
   git checkout -b my-v0.6.0 v0.6.0  
   python3 setup.py install  
   python3 setup.py bdist_wheel  



