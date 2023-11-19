# ISO For EndeavourOS

[![Maintenance](https://img.shields.io/maintenance/yes/2022.svg)]()  [![Downloads](https://img.shields.io/github/downloads/endeavouros-team/ISO/total)]()

[![autobuild](https://img.shields.io/github/v/release/endeavouros-team/ISO?logo=github)]()

**We do not use this Repository for ISO Releases anymore up from the Release of Galileo ISO,  please use one of the mirror links from the official Downloadpage:**

[EndeavourOS download page](https://endeavouros.com/latest-release)

[Release archive](https://github.com/endeavouros-team/ISO/releases/tag/1-EndeavourOS-ISO-releases-archive) // not used anymore up from Galileo ISO Relase

![Live-Session-Screenshot](https://raw.githubusercontent.com/endeavouros-team/screenshots/master/eos-installer-iso-nov-2021.png)

---


**How to handle ISO releases:**

import private key:  (if changed machine or new install)
`gpg --import private_key.gpg`

sign the iso-file:

`gpg --default-key yourname@endeavouros.com --output isoname.iso.sig --detach-sig isoname.iso`

verify:

for check:
`gpg  --recv CB23504F`

`gpg --verify isoname.iso.sig`

sha512sum creation:

`sha512sum endeavouros-2021.02.02-x86_64.iso > endeavouros-2021.02.02-x86_64.iso.sha512sum`


## Create torrent:(run command in same folder with the iso)

`mktorrent --announce=udp://tracker.openbittorrent.com:80 -a udp://tracker.torrent.eu.org:451/announce -a udp://thetracker.org:80/announce -a udp://tracker.dutchtracking.com:6969/announce -a udp://tracker.opentrackr.org:1337/announce -c endeavouros-2021.02.02-x86_64.iso -n endeavouros-2021.02.02-x86_64.iso -o endeavouros-2021.02.02-x86_64.iso.torrent -v endeavouros-2021.02.02-x86_64.iso -w https://mirror.alpix.eu/endeavouros/iso/endeavouros-2021.02.02-x86_64.iso` 

// -p, --private                 : set the private flag  --->  removed private flag from mktorrent command //

## save virtualbox ova to rebuild packages for HotFix:

Make VM image smaller is to erase empty space inside the VM:

`sudo dd if=/dev/zero of=/emptyspace`

`sudo rm -rf /emptyspace`

power down the VM.

use vmbox tool to compact the vm-disk:

`VBoxManage modifyhd --compact nameofthedisk.vdi`

and now create the ova image from virtualbox-manager.
