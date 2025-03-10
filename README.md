# Baksnapper - backup script for snapper
Baksnapper is a script for backing up snapshots created by the program snapper using btrfs send and receive.
This is a lite-version with many of the extra fluff removed.

## Installation
Run as root:
```bash
git clone https://github.com/pavinjosdev/baksnapper.git
cd baksnapper
cp baksnapper.sh /usr/bin/baksnapper
cp baksnapperd.sh /usr/bin/baksnapperd
mkdir -p /etc/baksnapper
cp config/* /etc/baksnapper
```

## Initial backup
```bash
baksnapper --configfile /etc/baksnapper/root.bsconf
baksnapper --configfile /etc/baksnapper/home.bsconf
```

## Setup crontab

Create file `/etc/cron.d/baksnapper` with the following contents:

```
0 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/root.bsconf
1 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/home.bsconf
2 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/var.bsconf
3 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/opt.bsconf
4 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/srv.bsconf
5 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/root-user.bsconf
6 * * * * root /usr/bin/baksnapper --configfile /etc/baksnapper/usr-local.bsconf
```

Secure cron file:

```
chmod 600 /etc/cron.d/baksnapper
```
