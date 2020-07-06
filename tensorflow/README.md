# TensorFlow on aarch64

Steps or scripts to run TensorFlow on Ampere aarch64

## Installation

1: Install Ubuntu18.04 on Ampere aarch64

2: Install nessesary lib and config Java  
   apt install -y git zip unzip openjdk-8-jdk build-essential cmake gfortran zlib1g-dev pkg-config python3-h5py python3-numpy python3-dev python3-pip python3-wheel python3-yaml python3-pil python3-scipy python3-opencv python3-matplotlib libblas-dev liblapack-dev libnuma-dev libhdf5-dev 
   vi /etc/profile  
   export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-arm64  
   export JRE_HOME=/usr/lib/jvm/java-8-openjdk-arm64/jre  
   export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH  
   export PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin  
   source /etc/profile  
   java -version  
   ln -sf /usr/bin/python3.6 /usr/bin/python  
   ln -sf /usr/bin/pip3 /usr/bin/pip  
   python --version  
   pip --version  

   

3: install bazel from src  
   wget https://github.com/bazelbuild/bazel/releases/download/3.3.0/bazel-3.3.0-dist.zip  
   mkdir bazel  
   mv bazel-*.zip bazel  
   cd bazel  
   unzip bazel-*.zip   
   env EXTRA_BAZEL_ARGS="--host_javabase=@local_jdk//:jdk" bash ./compile.sh  
   cp output/bazel /usr/bin/bazel  
   bazel --version  


4: Complie and Install TensorFlow  
   pip3 install six numpy wheel setuptools mock Cython h5py scipy keras_applications keras_preprocessing  
   git clone https://github.com/tensorflow/tensorflow.git  
   cd tensorflow  
   git checkout r2.3  
   ./configure  
   bazel build --config=opt --config=v2 --config=noaws --config=nogcp --config=nohdfs  --config=nonccl  --verbose_failures //tensorflow/tools/pip_package:build_pip_package  
   ./bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg  
   pip3 install /tmp/tensorflow_pkg/tensorflow-2.3.0rc0-cp36-cp36m-linux_aarch64.whl  

5: Verify  
   python3 test_tesorfloe.py  
