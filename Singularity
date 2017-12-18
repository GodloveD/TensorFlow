BootStrap: docker
From: nvidia/cuda:8.0-cudnn5-devel

%post

    # add universe repo and install some packages
    # sed -i '/xenial.*universe/s/^#//g' /etc/apt/sources.list
    # locale-gen en_US.UTF-8
    apt-get -y update
    apt-get -y install vim wget perl python python-pip python-dev

    # install tensorflow
    pip install --upgrade pip
    pip install tensorflow-gpu

