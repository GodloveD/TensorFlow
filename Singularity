BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://us.archive.ubuntu.com/ubuntu/

%setup
    # commands to be executed on host outside container during bootstrap

%post
    # commands to be executed inside container during bootstrap

    # add universe repo to apt sources and install some packages
    sed -i 's/$/ universe/' /etc/apt/sources.list
    locale-gen en_US.UTF-8
    apt-get -y update
    apt-get -y install vim wget python python-pip

    # create bind points for NIH HPC environment
    mkdir /gpfs /spin1 /gs2 /gs3 /gs4 /gs5 /gs6 /data /scratch /fdb /lscratch

    # install tensorflow
    pip install --upgrade pip
    pip install tensorflow

%runscript
    # commands to be executed when the container runs

%test
    # commands to be executed within container at close of bootstrap process

