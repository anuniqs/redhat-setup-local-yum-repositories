### Gyan

YUM : The Yellowdog Updater, Modified is a free and open-source command-line package-management utility for computers running the Linux operating system using the RPM Package Manager.

RPM : RPM Package Manager is a free and open-source package management system. The name RPM refers to .rpm file format and the package manager program itself. RPM was intended primarily for Linux distributions; the file format is the baseline package format of the Linux Standard Base. 


### Set Up and Configure local Yum Repositories on RedHat, Using Packages from mounted .iso

-rw-rw-r--.  1 anup anup 4526702592 Nov  2 12:48 rhel-server-7.9-x86_64-dvd.iso


`[root@localhost ~]#` mkdir /dvd


`[root@localhost ~]#` mount -o loop /home/anup/rhel-server-7.9-x86_64-dvd.iso /dvd/

`[root@localhost ~]#` lsblk

or,

`[root@localhost ~]#` df -h


`[root@localhost ~]#` cp -r /dvd/Packages/ /Packages


`[root@localhost ~]#` nano /etc/yum.repos.d/redhat.repo

`[root@localhost ~]#` nano /etc/yum.repos.d/redhat_repo.repo

```
[InstallMedia]
name=Red Hat Enterprise Linux 7.8
mediaid=1582647234.022611
metadata_expire=-1
gpgcheck=1
cost=500
enabled=1
baseurl=file:///Packages/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
```


`[root@localhost ~]#` rpm -ivh deltarpm-3.6-3.el7.x86_64.rpm createrepo-0.9.9-28.el7.noarch.rpm python-deltarpm-3.6-3.el7.x86_64.rpm

`[root@localhost ~]#` createrepo -v /Packages (Keep all the rpm packages inside this directory)

`[root@localhost ~]#` yum clean all

`[root@localhost ~]#` yum repolist

