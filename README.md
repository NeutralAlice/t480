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

### install xrandr
#set backlight to 30% /sys/class/backlight/intel_backlight/brightness


###set i3 config
#i3 config:
    include XF86 audio settings
