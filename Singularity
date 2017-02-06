BootStrap: docker
From: nvidia/cuda:8.0-cudnn5-devel-centos7

%setup
    # commands to be executed on host outside container during bootstrap

%post
    # commands to be executed inside container during bootstrap

    # install other needed packages
    yum -d 10 check-update
    yum -y install vim-minimal
    yum -y install epel-release
    yum -y install python-pip wget which perl

    # create bind points for NIH HPC environment
    mkdir /gpfs /spin1 /gs2 /gs3 /gs4 /gs5 /gs6 /data /scratch /fdb /lscratch

    # download and run NIH HPC cuda for singularity installer
    wget ftp://helix.nih.gov/CUDA/cuda4singularity
    chmod 755 cuda4singularity 
    ./cuda4singularity --verbose
    rm cuda4singularity

    # install tensorflow
    pip install --upgrade pip
    pip install tensorflow-gpu

%runscript
    # commands to be executed when the container runs

%test
    # commands to be executed within container at close of bootstrap process
