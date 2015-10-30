Convert RHEL 6 to Oracle Linux 6

Before we started to use Oracle Linux for running our Oracle installations on we had created a few RHEL hosts, I've been wanting to switch them from Redhat to Oracle Linux but never found the time as I imagined I would have to re-install the OS from scratch.

I discovered that this isn't the case after a bit of internet research. Oracle does tout an easy way to switch but that involves having a valid ULN support contract which we don't have, however there is a method of switching without one it's just not very well documented.

Using the notes http://public-yum.oracle.com/ as a guide I formulated the following steps :

1. Get the PGP key for ol6

wget https://public-yum.oracle.com/RPM-GPG-KEY-oracle-ol6 -O /etc/pki/rpm-gpg/RPM-GPG-KEY-oracle

2. Get the OL6 repo

cd /etc/yum.repos.d
wget https://public-yum.oracle.com/public-yum-ol6.repo

2. Rename the rhel-source.repo in /etc/yum.repos.d

mv rhel-source.repo rhel-source.repoold

3. Disable the presto and rhnplugin plugins by setting the enabled flag to 0 in :

vi /etc/yum/pluginconf.d/presto.conf
vi /etc/yum/pluginconf.d/rhnplugin.conf

4. Have to remove the libreport.x86_64 package as this will cause the process to fail, it doesn't exist on the other  OL6 hosts so should be safe to remove.

yum erase libreport

5. Test with yum list updates, it should run and return a list of packages if the changes have been successful then do a yum upgrade. If the yum list updates fails do a yum clean all to delete any existing yum information and do the yum list updates again.

6. Remove the file public-yum-ol6.repo-disabled from /etc/yum.repo.d and rename the file public-yum-ol6.repo.rpmnew to public-yum-ol6.repo

rm /etc/yum.repos.d/public-yum-ol6.repo-disabled
mv /etc/yum.repos.d/public-yum-ol6.repo.rpmnew /etc/yum.repos.d/public-yum-ol6.repo

7. Install the Unbreakable Kernel.

yum install kernel-uek kernel-uek-devel

8. Edit grub.conf to use unbreakable kernel.

vi /boot/grub/grub.conf

change default to 0

9. Reboot