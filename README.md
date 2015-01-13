# remote_syslog2.deb

Packaging of https://github.com/papertrail/remote_syslog2

## How to

```sh
vagrant up
vagrant ssh

# inside vagrant box
sudo apt-get install dpkg-dev debhelper

VERSION="0.13"
DEB_VERSION="$VERSION.v20140724"
PACKAGE="remote-syslog_$DEB_VERSION"

mkdir /tmp/$PACKAGE
cd /tmp/$PACKAGE

wget https://github.com/papertrail/remote_syslog2/releases/download/v$VERSION/remote_syslog_linux_amd64.tar.gz -O $PACKAGE.orig.tar.gz

tar --extract --file $PACKAGE.orig.tar.gz
cp --recursive /vagrant/debian/ remote_syslog/
cd remote_syslog

dpkg-buildpackage -rfakeroot -uc -us

# figure out signing & ppa uploading
```
