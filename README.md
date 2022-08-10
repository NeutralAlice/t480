 This repo is specifically for configuration of my thinkpad t480 using fedora with systemd as the operating system

Text description of what should be done to setup the t480 for installs and settings of those installs

###install neovim
## sudo dnf install neovim python3-neovim

###install throttled 
##https://github.com/erpalma/throttled
#throttled config:
    [battery] core -100mV

###install tlp
## sudo dnf install tlp tlp-rdw
# dnf remove power-profiles-daemon ## not present on F36?

###install ranger

###install feh

### install xrandr  ##checking if I really need xrandr, probably not
#set backlight to 30% /sys/class/backlight/intel_backlight/brightness

### install xbacklight
##add the correct device for intel based backlight to /etc/X11/xorg.conf.d/20-intel.conf
#Section "Device"
#    Identifier  "Intel Graphics"
#    Driver      "intel"
#    Option      "Backlight"  "intel_backlight"
#EndSection

###set i3 config
#i3 config:
    bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute @DEFAULT_SINK@ toggle && $refresh_i3status
    bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ -1% && $refresh_i3status
    bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ +1% && $refresh_i3status
    bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute @DEFAULT_SINK@ toggle && $refresh_i3status
    bindsym XF86AudioMicMute exec --no-startup-id pactl set-source-mute @DEFAULT_SOURCE@ toggle && $refresh_i3status
    bindsym XF86MonBrightnessDown exec xbacklight -dec 5 # decrease brightness
    bindsym XF86MonBrightnessUp exec xbacklight -inc 5 # increase screen brightness

