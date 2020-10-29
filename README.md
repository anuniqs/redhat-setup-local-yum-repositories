# Set Up and Configure Yum Repositories on CentOS

In Linux, a repository is a central database of software. Linux distributions have a central repository for system and commonly-used software.  Often administrators may have a need for a specialized software package, or to manage network bandwidth. For these reasons, they need to set up a new custom local repository.  Yum is a local repository for RPM package files. These packages compress available software for Linux distributions. With the repository, you can download, install and hold packages on a local disk or remotely.


[root@localhost ~]# nano /etc/yum.repos.d/redhat.repo

[root@localhost ~]# nano /etc/yum.repos.d/redhat_repo.repo

[InstallMedia]
name=Red Hat Enterprise Linux 7.8
mediaid=1582647234.022611
metadata_expire=-1
gpgcheck=1
cost=500
enabled=1
baseurl=file:///Packages/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

[root@localhost ~]# rpm -ivh deltarpm-3.6-3.el7.x86_64.rpm createrepo-0.9.9-28.el7.noarch.rpm python-deltarpm-3.6-3.el7.x86_64.rpm

[root@localhost ~]# createrepo -v /Packages (Keep all the rpm packages inside this directory)

[root@localhost ~]# yum clean all

[root@localhost ~]# yum repolist
