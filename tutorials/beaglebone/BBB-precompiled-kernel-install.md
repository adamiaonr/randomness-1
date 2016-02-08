# Get a pre-compiled Debian kernel on Beaglebone Black from Robert Nelson's repository

The `/opt/scripts/tools/install_me.sh` scripts do not function anymore. Thus we use the deb repo at rcn-ee.net

Robert Nelson's repository at [http://rcn-ee.net](http://rcn-ee.net) has some versions of pre-compiled kernels directly available (which saves the effort of trying to compile your own kernel).

* add to`/etc/apt/source.list`:
```deb [arch=armhf] http://repos.rcn-ee.net/debian/ wheezy main```
Make a note of using the appropriate version of Debian.

* Add the required keys:
```wget -qO - https://repos.rcn-ee.net/debian/conf/repos.rcn-ee.net.gpg.key | sudo apt-key add -```

* `sudo apt-get install linux-headers-<version>`
You can search for the appropriate version using `apt-cache search linux-headers|grep <version>`