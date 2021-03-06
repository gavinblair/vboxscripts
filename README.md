vboxscripts
===========

commands to help me manage my virtual machine

Requires: VirtualBox. Tested on Mac OSX 10.9.

Installation
------------

Get the name of your virtual machine:

```
$ VBoxManage list vms
"Apache - Centos PHP 5.3" {a5438d86-c153-4d58-a8c1-ad7326336707}
"Apache - Centos PHP 5.3 Experimental" {3d3a787a-15c9-4668-8a1a-e39cb3af0d2d}
```

Copy the name (between the quotes) of the machine you wish to control.

Edit the scripts and replace `"Apache - Centos 5.3"` with your virtual machine name. Put your name at the bottom of `vboxwait`.

***Note: `vboxip` gives you the IP address of the first VM in the list. I guess it should be updated to use the name instead.***

Copy to your bin folder:
```
$ sudo chmod +x vbox*
$ sudo cp vbox* /usr/bin
```

On the Mac you may need to close the terminal and reopen in order for the commands to be available.


Usage
-----

Get the IP address of your vm:
```
$ vboxip
```

Get the IP address of your host machine (Tested on a Mac) :
```
$ hostip
```

Copy the IP address of your vm (at least on the Mac). Note that this could include a newline after the IP address.
```
$ vboxip | pbcopy
```

Start your vm in headless mode
```
$ vboxstart
```

Restart your vm
```
$ vboxreset
```

You may want to restart your VM if you want a new IP. Restarting can take a few minutes, so you can use `vboxwait` to alert you when it's ready. Mac only:
```
$ vboxwait
```

You can grab a screenshot of your VM to see what's going on. This command will create a file called `screenshot.png` in the current directory.
```
$ vboxscreen
```

If you have the QuickLook `ql` command installed (Mac only) you can use it to quickly view the screenshot:
```
$ vboxscreen; ql screenshot.png
```

If you want to monitor your vm's apache error log file, you can use the following command. Note that your error log must be somewhere that your host machine can access (I keep mine in /websites/logs). You can change where Apache keeps its error log in `httpd.conf`. The `say` command is Mac OSX only. For other operating systems you can have it play back an audio file or emit a system beep.
```
$ errorwatch
```

If you want to do more with your virtualbox from the command line use `VBoxManage`. Here are some common commands:

List VMs:
```
$ VBoxManage list vms
```

Reset:
```
$ VBoxManage controlvm "Your VM Name" reset
```

Poweroff:
```
$ VBoxManage controlvm "Your VM Name" poweroff
```
Save State:
```
$ VBoxManage controlvm "Your VM Name" savestate
```
