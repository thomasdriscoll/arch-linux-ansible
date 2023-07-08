## Creating the USB stick to get this working
- Using archiso, creating a new ISO -- the necessary packages are
"ansible" and "git"
    - https://wiki.archlinux.org/title/Archiso

## Bootstrapping
- First establish an internet connection
    - Using iwctl
        - ``` iwctl adapter phy0 set-property Powered on ``` ## most
          likely to be different
        - ``` iwctl station wlan0 scan```
        - ``` iwctl station wlan0 connect <wifi_name> ```
- Then clone the repository
    - ``` git clone
      https://github.com/thomasdriscoll/arch-linux-ansible.git ```
- Set the root variables in variables/bootstrap-vars.yml
