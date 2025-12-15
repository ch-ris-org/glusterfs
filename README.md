### The following apt-get command will install all the build requirements on Ubuntu
```
sudo apt-get install make automake autoconf libtool flex bison  \
  pkg-config libssl-dev libxml2-dev python2-dev libaio-dev       \
  libibverbs-dev librdmacm-dev libreadline-dev liblvm2-dev      \
  libglib2.0-dev liburcu-dev libcmocka-dev libsqlite3-dev       \
  libacl1-dev liburing-dev google-perftools
```

### Building from Source
This section describes how to build GlusterFS from source. It is assumed you have a copy of the GlusterFS source (either from a released tarball or a git clone). All the commands below are to be run with the source directory as the working directory.

1. Run autogen to generate the configure script.
```
./autogen.sh
```

2. Once autogen completes successfully a configure script is generated. Run the configure script to generate the makefiles.
```
./configure
```
3. Once configured, GlusterFS can be built with a simple make command.
```
make
```
 > To speed up the build process on a multicore machine, add a '-jN' flag, where N is the number of parallel jobs.

### Installing
Run 'make install' to install GlusterFS. By default, GlusterFS will be installed into '/usr/local' prefix. To change the install prefix, give the appropriate option to configure. If installing into the default prefix, you might need to use 'sudo' or 'su -c' to install.
```
sudo make install
```

### Running GlusterFS
GlusterFS can be only run as root, so the following commands will need to be run as root. If you've installed into the default '/usr/local' prefix, add '/usr/local/sbin' and '/usr/local/bin' to your PATH before running the below commands.

A source install will generally not install any init scripts. So you will need to start glusterd manually. To manually start glusterd just run,
```
systemctl daemon-reload
systemctl start glusterd
```
This will start glusterd and fork it into the background as a daemon process. You now run 'gluster' commands and make use of GlusterFS.
