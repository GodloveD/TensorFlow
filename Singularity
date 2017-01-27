BootStrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum wget

%setup
    # commands to be executed on host outside container during bootstrap

%post
    # commands to be executed inside container during bootstrap

    # yum needs some tlc to work properly in container
    RELEASEVER=7
    ARCH=x86_64
    echo $RELEASEVER > /etc/yum/vars/releasever
    echo $ARCH > /etc/yum/vars/arch
    yum -y install epel-release
    # wget http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-9.noarch.rpm
    # rpm -ivh --nodeps epel-release-7-8.noarch.rpm
    yum -d 10 check-update

    # install other needed packages
    yum -y install man which tar gzip vim-minimal perl python python-dev python-pip \
	util-linux

    # create bind points for NIH HPC environment
    mkdir /gpfs /spin1 /gs2 /gs3 /gs4 /gs5 /gs6 /data /scratch /fdb /lscratch

    # download and run NIH HPC cuda for singularity installer
    wget ftp://helix.nih.gov/CUDA/cuda4singularity-dev
    chmod 755 cuda4singularity-dev 
    ./cuda4singularity-dev --verbose
    rm cuda4singularity-dev

    # install tensorflow
    pip install --upgrade pip
    pip install tensorflow-gpu

%runscript
    # commands to be executed when the container runs

%test
    # commands to be executed within container at close of bootstrap process
