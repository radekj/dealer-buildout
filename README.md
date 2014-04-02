Buildout for dealer
===================

Pre requirements
----------------

Compile and install Python 3.4 in `/opt`:

```
sudo apt-get update
sudo apt-get -y install build-essential zlib1g-dev libbz2-dev \
    libncurses5-dev libreadline-gplv2-dev libsqlite3-dev \
    libssl-dev libgdbm-dev

sudo mkdir -p /opt/python/3.4.0

cd /tmp
wget https://www.python.org/ftp/python/3.4.0/Python-3.4.0.tar.xz
tar -xJf Python-3.4.0.tar.xz
cd Python-3.4.0
./configure --prefix=/opt/python/3.4.0
make
sudo make install
```

Installation
------------

```
git clone git@github.com:radekj/dealer-buildout.git
cd dealer-buildout
/opt/python/3.4.0/bin/python3 bootstrap.py
./bin/buildout -vN
```

If you want to develop dealer app you have to fork
[dealer repo](https://github.com/radekj/dealer) and than create `local.cfg`
file:

```
[buildout]
extends = buildout.cfg

[sources]
dealer = git git@github.com:username/dealer.git
```

and rebuild environment:

```
./bin/buildout -vNc local.cfg
```

Usage
-----

Run dev server:

```
./bin/pserve src/dealer/development.ini
```

Check tests:

```
./bin/test
```