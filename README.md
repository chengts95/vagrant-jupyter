# Jupyter Notebook with Python3, Scala and PySpark

This is a Vagrant machine with Jupyter Notebook (v4) installed.
The kernels installed are: Python 3, Apache Spark 1.5.1 with Scala 2.10.4 and PySpark (1.5.1).
The notebook folder is: /home/vagrant.

### Requirements
You have to install:

1. VirtualBox 5 or later (this was tested on VirtualBox 5.0.6) - https://www.virtualbox.org/wiki/Downloads
2. VirtualBox Oracle VM VirtualBox Extension Pack

### Installation
Copy the entire folder on your machine, enter in the Jupyter folder and then:

```
vagrant up
```

When the Vagrant provisioning/start-up processes are completed you can point your browser to:

```
http://localhost:8888
```
> Provisioning will take at least 20minutes!


### Install Vagrant machine behind proxy:

Add the following lines **on top of provisioning.sh** bash script:

```
export PROXYADDR=user:password@proxy-address:port
export http_proxy=http://$PROXYADDR
export https_proxy=http://$PROXYADDR
export ftp_proxy=http://$PROXYADDR
export all_proxy=http://$PROXYADDR
export HTTP_PROXY=http://$PROXYADDR
export HTTPS_PROXY=http://$PROXYADDR
export FTP_PROXY=http://$PROXYADDR
export ALL_PROXY=http://$PROXYADDR
export no_proxy=localhost,127.0.0.0/8,::1
export NO_PROXY=localhost,127.0.0.0/8,::1
echo "Acquire::http::Proxy \""$http_proxy"\";" > /etc/apt/apt.conf
echo "Acquire::https::Proxy \""$http_proxy"\";" >> /etc/apt/apt.conf
```

and the following ones **after Git is installed** (provisioning.sh script, after line 25)

```
git config --global http.proxy $http_proxy
git config --global https.proxy $http_proxy
```
