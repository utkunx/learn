
---
* Q- How to give new UUID to a partition on disk procedure ? 
	* `e2fsck -f /dev/nvme1n1p7` first run it check filesystem (mantetory for tune2fs to work)
	* `tune2fs -U $(uuidgen) /dev/nvme1n1p7` then run it give new UUID to that partition...
---
* `blkid` list all partitions labels and UUID's
	* `/dev/nvme0n1: PTUUID="c3901cef-7db3-6843-a8e2-1166aa043855" PTTYPE="gpt"`
---
* `fstab(5)` fstab filesystem mount points manager
	* `/etc/fstab` where the the file stored.
---



----
----
----










| `commands`  | extra param  | into |
| :------------ |:---------------:| -----:|
| `e2fsck`      | -f /dev/nvme1n1p7 | it must be runned to `tune2fs` work later... |
| `tune2fs`      | -U $(uuidgen) /dev/nvme1n1p7        |   $12 |
| zebra stripes | are neat        |    $1 |
