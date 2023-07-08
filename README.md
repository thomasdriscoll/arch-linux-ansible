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
- Check the disks on your system (/dev/sda and others) and add them to the
disk list in playbooks/bootstrap.yml
- Choose your partition strategy and add them to the partition list playbooks/bootstrap.yml
    - Most likely one boot partition (/dev/sda1) and another (/dev/sda2)
    - If you have another disk (/dev/sdb), probably one partition for the
    whole thing (/dev/sdb1)
- Then run ```ansible-playbook playbooks/bootstrap.yml``` in the root of
the git project

## System configuration
- In variables/sys-config-vars.yml
    - Add all desired users on the system
    - Make sure to include their passwords and at least all fields in the
    examples provided
- Then run ```ansible-playbook playbooks/system_configuration.yml``` in
the root folder of the git project

