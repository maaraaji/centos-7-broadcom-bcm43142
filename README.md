# Things to do after Centos Minimal Installation

| Item | Description |
| --- | --- |
| Product | HP Pavilion Notebook |
| Wireless Network Controller | Broadcom 43142 |
| Bluetooth Controller | BCM43142A0 |


#### Enabling Wireless using elrepo

1. sudo yum install gcc

2. sudo yum install redhat-lsb kernel-abi-whitelists

3. sudo yum install kernel-devel-`uname -r`

4. mkdir -p ~/rpmbuild/{BUILD,RPMS,SPECS,SOURCES,SRPMS}

5. echo -e '%_topdir $(echo $HOME)/rpmbuild\n%dist .el$(lsb_release -s -r|cut -d"." -f1).local' >> ~/.rpmmacros
