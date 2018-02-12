# Things to do after Centos Minimal Installation

| Item | Description |
| --- | --- |
| Product | HP Pavilion Notebook |
| Wireless Network Controller | Broadcom 43142 |
| Bluetooth Controller | BCM43142A0 |


#### Enabling Wireless using elrepo - Reference Link : (http://elrepo.org/tiki/wl-kmod)

1. sudo yum install gcc

2. sudo yum install redhat-lsb kernel-abi-whitelists

3. sudo yum install kernel-devel-`uname -r`

4. mkdir -p ~/rpmbuild/{BUILD,RPMS,SPECS,SOURCES,SRPMS}

5. echo -e '%_topdir $(echo $HOME)/rpmbuild\n%dist .el$(lsb_release -s -r|cut -d"." -f1).local' >> ~/.rpmmacros

6. mkdir ~/Downloads/bcm43142 && cd ~/Downloads/bcm43142

7. Download the specific 64bit linux driver from Broadcom website -  http://www.broadcom.com/support/802.11 (external link) (scroll down to "Linux® STA 32-bit (or 64-bit) drivers") to the Downloads Folder

  1. You cannot download through wget as it needs agreement acceptance before download.
  2. Best way is to download from different machine to external USB, mount the USB to /media/ and copy it from there to below mentioned destination.

8. cp ~/Downloads/bcm43142/hybrid-v35_64-nodebug-pcoem-6_30_223_271.tar.gz ~/rpmbuild/SOURCES

9. rpmbuild --rebuild --define 'packager anonymous' ~/wl-kmod-6_30_223_271-4.el7.elrepo.nosrc.rpm

10. yum remove \*ndiswrapper\*
