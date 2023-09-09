# How to setup our IT from scratch

## Platform

Create a new Hetzner VM:

* Location: ours
* OS: doesn't matter
* CPU: shared, x86
* Net: IPv4 and IPv6
* SSH key: doesn't matter
* No volumes, firewalls, backups, groups, labels or cloud config
* Name: so that the Hetzner user recognizes the VM as organization property
  (TODO: create organization-own account, migrate VM there, re-evaluate name)

## OS

Load OpenBSD 7.3 image, reboot and open the web console to setup OpenBSD.
(Paranoid poor man's OS, yes. But don't forget the FSB has an eye on us.)

### Basics

* Keyboard: "de"
* Hostname: "mx" (TODO: mail service)
* Net: just enter, but "autoconf" for IPv6
* Simple root password for now (TODO: correct later)
* sshd: "yes"
* X window, com0 and user: "no"
* root ssh login: "no"
* Timezone: confirm

### Partitioning

* Encrypt root disk: "no"
* Root disk: confirm
* Partition table: "w" (whole MBR)
* Layout: "c" (custom)
* Label editor:
  * "D" (reset)
  * "a" (new partition)
    * Confirm partition letter, offset, size and FS
    * Mount point: "/"
  * "q" (quit)
  * Write: confirm

### Misc.

* Sets location: "http"
* Proxy: "none"
* HTTP server: "?", `[Q]`, number of e.g. "ftp.fau.de", confirm
* Directory and set names: confirm
* Sets location and reboot: confirm
* Eject ISO image
* Reboot one last time

## Remote access

In the web console login as root. Create a user for the admin, e.g.:

`adduser -batch aklimov wheel 'Alexander A. Klimov' '*' -group users -v`

Then populate (e.g.) `/home/aklimov/.ssh/authorized_keys`.
