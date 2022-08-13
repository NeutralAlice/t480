This repo is specifically for configuration of my thinkpad t480 using fedora with systemd as the operating system

Text description of what should be done to setup the t480 for installs and settings of those installs
#^=local install
#*=config setup
#?=unsure if used enough

# INSTALLS
zsh *  
alacritty **  
i3-gaps  
ranger  
cmus  
neovim  
tlp  
tlp-rdw  
librewolf  
xbacklight *  
xprop  
git *  
gh  
pycharm-community  
rclone *  
keepassxc  
neofetch  
exa  
bat  
gimp  
evolution  
flameshot  
krita  
xournalpp ?  
btop  
cmake  
freetype-devel  
fontconfig-devel  
libxcb-dev  
mpv  
glances  
throttled *  
picom ? jonaburg or other  
@virtualization ?  
zoom ^  

## REPOS
rpmfusion https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm#rpmfusion  
rpmsphere ^  

# REMOVALS
firefox  
mousepad  

# Configuration
## @virtualization
sudo usermod -aG libvirt user  
sudo systemctl start libvirtd && systemctl enable libvirtd  

## throttled 
config:  
    [battery] core -100mV  

## rclone
mount googledrive

## tlp
sudo dnf remove power-profiles-daemon ## not present on F36?  

## xbacklight
add the correct device for intel based backlight to /etc/X11/xorg.conf.d/20-intel.conf  
Section "Device"  
    Identifier  "Intel Graphics"  
    Driver      "intel"  
    Option      "Backlight"  "intel_backlight"  
EndSection  

## i3
config:  
    bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute @DEFAULT_SINK@ toggle && $refresh_i3status  
    bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ -1% && $refresh_i3status  
    bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ +1% && $refresh_i3status  
    bindsym XF86AudioMicMute exec --no-startup-id pactl set-source-mute @DEFAULT_SOURCE@ toggle && $refresh_i3status  
    bindsym XF86MonBrightnessDown exec xbacklight -dec 5 # decrease brightness  
    bindsym XF86MonBrightnessUp exec xbacklight -inc 5 # increase screen brightness  
    bindsym XF86Favorites exec --no-startup-id librewolf  
    bindsym Print exec flameshot gui --clipboard  
