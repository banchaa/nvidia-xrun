# nvidia-xrun
These utility scripts aim to make the life easier for nvidia cards users. It
started with a revelation that bumblebee in current state offers very poor
performance. This solution offers a bit more complicated procedure but offers a
full GPU utilization(in terms of linux drivers).

This is a fork for use with Debian testing/sid and bumblebee. It has not been
tested to work with all configurations. It also assumes you have multiarch, and
might spuriously fail if you don't, though this has not been tested.

Please note that if you are using tmux, you will have to either close your
session and start a new one when you login with nvidia-xrun, or re-import your
enviornment variables (`DISPLAY and LD_LIBRARY_PATH`) to your tmux session when
you log in. You will need the nvidia directories as specified in your
`LD_LIBRARY_PATH` in order to run command-line programs using the nvidia card
(such as `glxinfo`). I'm not sure why debian is so finnicky about keeping these
environment variables preserved; ymmv.

## Installation:

An installation script (`sudo make install`) is a work-in-progress.

  1) install `xserver-xorg-legacy` (necessary to call `startx` as root). For
  best compatibility, make sure you have `bumblebee-nvidia` and
  `multiarch-support` installed too. 
  2) copy `./nvidia-xrun` to somewhere in your `$PATH` (e.g.
  `/usr/bin/nvidia-xrun`)
  3) copy `./nvidia-xinitrc` to `/etc/x11/xinit/nvidia-xinitrc`
  4) copy `./nvidia-xorg.conf` to `/etc/x11/nvidia-xorg.conf`

## Usage: 

  1) switch to free tty
  2) login
  3) run `nvidia-xrun app`
  4) enjoy
  
  
  Currently sudo is required as the script needs to wake up GPU, modprobe the
  nvidia driver and perform cleanup afterwards. For this we use bbswitch.
  
## Packages
Use the original version of this repo from Witko to obtain the aur package.
There is no debian package as of this time. This is a completely unofficial and
untested (except on my machine) fork of the original project, aimed at providing
a stepping stone for Debian/bumblebee users, and that may eventually turn into a
more universally usable fork.

Issue and pull requests are welcome. Please go on the nvidia forums and tell
them to support PRIME render offloading! That will make this utility obsolete
and bring true Optimus functionality to Linux.

https://devtalk.nvidia.com/default/topic/957981/linux/prime-render-offloading-on-nvidia-optimus/
