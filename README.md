<!--
SPDX-FileCopyrightText: 2023 Fredrik Salomonsson <plattfot@posteo.net>

SPDX-License-Identifier: GPL-3.0-or-later
-->

# Baksnapper - backup script for snapper
Baksnapper is a script for backing up snapshots created by the program snapper using btrfs send and receive.

## Installation
Run as root:
```bash
git clone https://github.com/pavinjosdev/baksnapper.git
cd baksnapper
cp baksnapper*.sh /usr/bin
mkdir -p /etc/baksnapper
cp config/* /etc/baksnapper
```

## Initial backup
```bash
baksnapper --configfile /etc/baksnapper/root.bsconf
baksnapper --configfile /etc/baksnapper/home.bsconf
```
