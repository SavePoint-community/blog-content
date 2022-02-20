---
author: Yahia Cherif mehdi
title: Creating your own Ubuntu distro 
date: 2022-02-14
description: Custom dwm build for ubuntu server minimal install
math: false
thumbnail: https://hashnode.com/post/make-your-custom-linux-distribution-ckznar3ax07g2o2s183dv7aw6
---


---
author: Souhil Zaida
title: Data Warehouse
date: 2022-01-08
description: Why we need data warehouse
math: false
thumbnail: https://cdn.hashnode.com/res/hashnode/image/upload/v1641641507119/6NxNJhO7S.png?w=1600&h=840
---

# Creating your own custom distro 


instead of having to wait til someone creates the perfect linux distro for you , maybe you want to customize your own 


generally for this , people may take KDE and start tweaking it , like i was doing , and i enjoyed it a lot


but i wasn't completly satisfied 
i wanted something more unique , something where i understand how it is working ( at least most of what's running)
and then i decided to make my own distro , starting from ubuntu server that comes with no desktop environement , just the TTY 

#ubuntu server image
#tty image


first , we have to complete the installation of the basic **ubuntu server**


to draw anything on the screen , you need a display server
the most comon one is Xorg or X server 
to install it you can just type

```
sudo apt install xorg
```
>for ubuntu maybe you need to edd the --no-install-recommends flag
>else , ubuntu will automatically install gnome with it




insteat of using a regular desktop env , idecided to try a window manager , so i used DWM that stands for dynamic window manager

created by a team called "suckless" that aims to create linux tools that are minimal and fully functional (and thet are doing it in my opinion)


also we have to install some packages that are essential to let us build what we want 

```
sudo apt install libx11-dev build-essential libxinerama-dev libxfc-dev 
```

**DWM**

```
git clone https://git.suckless.org/st
cd dmenu
sudo make clean install
```


after choosing a window manager , i started looking for a menu system and a terminal emulator , 
i ended up using tools created by the same team 

**dmenu**


```
git clone https://git.suckless.org/dmenu
cd dmenu
sudo make clean install
```

#image

and **stterm**

```
git clone https://git.suckless.org/st
cd dmenu
sudo make clean install
```

#video



Xorg does not work without configuration
and the config file is generally under the **/home/<username/.xinitrc**
file



we need also another file to make all this run and it's  the **.bash_profile**
located in the same directory
basically , one of them start xorg , and the otherone start all the gui and background elements






to make my life easier customising the top panel , i used also dwmblocks.
**dwmblocks**

```
git clone https://git.suckless.org/dwmblocks
cd dmenu
sudo make clean install
```


> all those tools can be configured (if you know some coding with C)
> by modifying the **config.h** for every folder 

#image

here , we have to use scripts to get te value that we want 

here is the script to get the date


the battery level (for laptops)

and the ram usage 



to get the icons , i used font awesome 

```
sudo apt install fonts-font-awesome 
```

to configure my background i used **feh** 


``` 
sudo apt install feh 
```

simple usage 

``` 
feh --bg-scale <your image.png>
```

each time you run this , you update a file **/home/username/.fehbg**
and you need to call


at this point everything is up and running 

i needed just a text editor : vim 
to configure it , you need to create a **.vimrc** file in the user directory 
(maybe i will need to create a separate blog about it)


a web browser : falkon ( or firefox)

and a file manager : pcmanfm (or thuar)

to spice my desktop a littlebit , i added a compsitor that lets me add transparency to my st terminal emulator
for this i used **compton**

this is the final result

#img


the beauty of this is that all this is working with only 200-ish mb of ram and all of the rest is for you to run your programs


if you want my own build of the dwm
you can download all the tools from my github

```
git clone https://github.com/SAVE-POlNT/fdwm
```

and for my config (dot files)

```
git clone https://github.com/SAVE-POlNT/newdistroscripts

```

---
# Conslusion


i did not do this just for getting a minimalist and good looking distro , i did it to lear more about linux

and i ended up learning a lot especially about how to connect to wifi & ethernet without any packages or gui tool

it is a little bit harder than what it sould be imo , bit its good to know (take a look at wpa_supplicant and wpa_passphrase)

i ended up using nmcli and nmtui for connecting to the wifi ( comes in the network-manager package)


and learned more about what packages manages the sound , basically you need alsa and pulseaudio in your system







But still alll the efforts of the biggest desktop env are conciderable and worth trying 
and i will list 

* KDE
* XFCE
* Gnome
* LXQT
* and other smaller ones 
