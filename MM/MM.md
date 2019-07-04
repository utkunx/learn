# MM

| links                                                        | desp                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| http://www.akitaonrails.com/2017/01/17/optimizing-linux-for-slow-computers | Optimizing Linux for Slow Computers                          |
| https://github.com/ajaybhatia/Arch-Linux-personal-tweaks-collection |                                                              |
| https://wiki.archlinux.org/index.php/makepkg#Parallel_compilation | parallel                                                     |
| https://wiki.archlinux.org/index.php/General_recommendations |                                                              |
| https://www.cheatography.com/misterrabinhalder/cheat-sheets/arch-linux/ | Arch Linux Cheat Sheet by [misterrabinhalder](http://www.cheatography.com/misterrabinhalder/) |
| https://gist.github.com/yufengwng/9cff3fc82403e3f3052d       | Arch Linux Commands Cheatsheet                               |
| https://gist.github.com/vvilp/7006187                        | [**my Arch Linux cheat-sheet**](https://gist.github.com/vvilp/7083895#file-my-arch-linux-cheat-sheet) |
| https://wiki.archlinux.org/index.php/Improving_performance/Boot_process | nice                                                         |
|                                                              |                                                              |

## direct rendering

```bash
sudo pacman -S mesa-demos
glxinfo | grep direct
```

* ``direct rendering: Yes``  you must see,otherwise, this means you're not compositing through the GPU and you're wasting CPU cycles rendering your screen!

## `vm.swappiness=1`

* So you want to configure the OS to more aggressively keep your application state in RAM, and this is how you do it:

* ```bash
    sudo tee -a /etc/sysctl.d/99-sysctl.conf <<-EOF
    vm.swappiness=1
    vm.vfs_cache_pressure=50
    EOF
    ```
  ```
  
  ```

## `sysctl`

* `sysctl`,  location `/etc/sysctl.conf`
	* `-a , --all` 
		* display all variables
	* `-w, --write`
		* 	enable writing a value to variable

---

|`sysctl`|`[options]`|`[variable[=value] ...]`|
| ---- | :--: | :--: |
|      |      |      |

## I/O Scheduler
* You can check which I/O Scheduler you're running like this:
	* ```bash
	  $ cat /sys/block/sda/queue/scheduler
	  noop deadline cfq [bfq] 
	  ```

## speed-up boot time

### `systemd-analyze plot > plot.svg `

### `NetworkManager-wait-online.service`

* For most users 10 to 15 seconds can be sliced off the parallel boot time by using:
	* `sudo systemctl disable NetworkManager-wait-online.service`



