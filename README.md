# Alex' Ansible Roles Repository

This repository contains Ansible roles that are targeted for Debian
GNU/Linux version 7 (Wheezy) systems.


## Available Roles


### ansible-base

Configure the target system to be managed by Ansible, update *logcheck(8)*
configuration, for example.


### apache2-php5

Default Apache 2.x setup with PHP 5.x.

#### Depends on / Pulls in

 - debian-base

#### Installed Packages

 - apache2-mpm-prefork
 - apache2-utils
 - apachetop
 - libapache2-mod-php5
 - php-apc
 - php5
 - php5-cli
 - php5-mysql


### autofs

NFS "automounter" (autofs) setup including `/net/hostname` pseudo
directory hierarchy.

#### Depends on / Pulls in

 - debian-base

#### Installed Packages

 - autofs


### debian-base

Basic Debian setup, including APT and Debconf configuration as well as a
set of standard packages.

#### Installed Packages

 - bash-completion
 - busybox-static
 - ca-certificates
 - curl
 - debconf-utils
 - etckeeper
 - git
 - htop
 - less
 - linux-image-amd64
 - lsb-base
 - lsb-release
 - psmisc
 - net-tools
 - screen
 - sudo
 - telnet-ssl
 - vim


### git-backup-script

Local "BackupScript" installation from the GIT repository of Alex
(see https://arthur.barton.de/cgi-bin/gitweb.cgi?p=backup-script.git).

#### Depends on / Pulls in

 - debian-base

#### Installed Packages

 - rsync


### git-configscripts

Local "ConfigScripts" installation from the GIT repository of Alex
(see https://arthur.barton.de/cgi-bin/gitweb.cgi?p=ConfigScripts.git).

#### Depends on / Pulls in

 - debian-base

#### Variables

 - `git_configscripts_users`: List of existing users to update.


### git-nagcollect

Local "NagCollect" client installation from the GIT repository of Alex
(see https://arthur.barton.de/cgi-bin/gitweb.cgi?p=nagcollect.git).

#### Depends on / Pulls in

 - debian-base

#### Variables

 - `nagcollect_server_url`: Server URL.
 - `nagcollect_client_key`: Client key ("password").
 - `nagcollect_client_id`: Client (host) identifier.


### lcmc-cluster-node

Setup for Linux clusters running DRBD, Pacemaker, and Corosync using the
"Linux Cluster Management Console" (LCMC, see http://lcmc.sourceforge.net).

#### Depends on / Pulls in

 - debian-base
 - sshd
 - ntpd

#### Installed Packages

 - drbd8-utils
 - pacemaker
 - corosync


### mysql-server

MySQL Server setup, including a separate LVM data partition, if desired.

#### Depends on / Pulls in

 - debian-base

#### Variables

 - `mysql_server_vg`: LVM volume group name.
 - `mysql_server_ansible_user`: MySQL management user. Default "ansible".
 - `mysql_server_ansible_password`: Password of management user. Default "ansible".
 - `mysql_server_root_host`: Hostname for MySQL "root" user. Default "localhost".
 - `mysql_server_root_password`: Password for the MySQL "root" user.

#### Installed Packages

 - mysql-client
 - mysql-server
 - mysqltuner
 - python-mysqldb


### net-base

Basic networking configuration, including the target hostname which is set
to the Ansible inventory hostname.


### nfs-client

NFS client setup.

#### Depends on / Pulls in

 - debian-base

#### Variables

 - `nfs_client_domain`: NFSv4 client domain. Default: `ansible_domain`.

#### Installed Packages

 - nfs-common


### ntpd

Local *ntpd(8)* setup.

#### Depends on / Pulls in

 - debian-base

#### Installed Packages

 - ntpdate
 - ntp


### postfix

Postfix SMTP server setup.

#### Depends on / Pulls in

 - debian-base

#### Installed Packages

 - postfix


### sshd

SSH daemon setup.

Please note that this role always updates the SSH packages to the latest
version and not only makes sure that a "ssh" package is installed, like most
other roles in this repository.

#### Depends on / Pulls in

 - debian-base

#### Installed Packages

 - openssh-blacklist-extra
 - ssh
