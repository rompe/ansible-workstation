# ansible-workstation
Ansible playbook to update freshly installed Linux workstations for my needs - forked from Ulf's repo
to adjust to my personal needs, copying some things I found all over the web.

## Usage

For the default installation:
```
ansible-pull -U https://github.com/gmanic/ansible-workstation -K
```

In addition, for NFS servers:
```
ansible-pull -U https://github.com/gmanic/ansible-workstation nfs-server.yml
```

The host name `localhost` is used per default. This only works if /etc/ansible/hosts ist left
empty or features a `localhost` line.

Autostart apps are defined in the user_tasks, that they are run as the calling user. NO browser included, as I first unlock keepassxc manually.

## To be configured manually, if needed - always copy files to destination in /etc to avoid selinux issues
* Set proper hostname with `hostnamectl set-hostname <machine-name>`
* Define automount map (stored offline, Files extra.autofs and auto.nfs)
* Enable autofs.service (obviously, it is required with -33 to `setsebool -P nis_enabled 1` to enable rpcbind and some more on -34...
* Perhaps change codium's marketplace
* Setup openvpn (use the offline encrypted tar I have, perhaps some selinux issues to clear)
  Reminder: use the configs and ´systemctl enable openvpn-client@<conf-name>.service´ + ´systemctl start ´ the service
* Setup keybindings for desktop (hopefully someday with dconf reset/load from offline stored settings), like use alt-tab to switch through all single terminals instead of all at once... (see below)
* Setup all my terminal profiles for the different machines. ´dconf dump´ and ´dconf load´ to the rescue, very helpful; hint: "terminals" stored offline
* Setup virt-manager details
* ...
* then update the whole thing
  * `dnf upgrade --refresh`
  * `dnf groupupdate core`
  * `dnf install -y dnf-plugins-core`)
* compile and install v4l2loopback
  needed for chrome (-> Signal-flatpak) the following options are needed:
  * `modprobe v4l2loop devices=1 card_label="loopback 1" exclusive_caps=1,1,1,1,1,1,1,1`
* example settings, as reminder: windows - unlock modal windows from parent
* nextcloud issue on icon status bar: delay startup with special desktop description file (stored offline)
* For now collecting some settings, will include in proper ansible-task later, I guess:
  * `gsettings set org.gnome.shell.window-switcher current-workspace-only false` # enable window switching through all windows on all workspaces
  * `gsettings set org.gnome.desktop.wm.keybindings switch-applications ['']` # remove application switching
  * `gsettings set org.gnome.desktop.wm.keybindings switch-windows ['<Alt>Tab']` # instead do window switching with alt-tab
  * `dconf write /org/gnome/desktop/input-sources/xkb-options "['grp_led:scroll']"` # enable window switch last (instead of changing keyboard with alt-shift)

## To be added manually

Some packages can't be installed using ansible.

See also, e.g. https://mutschler.eu/linux/install-guides/fedora-post-install/
  * btrfs ssd optimization in fstab:
    * replace for / default with `ssd,noatime,space_cache,commit=120,compress=zstd,discard=async`

## Disclaimer

If you aren't me (or Jens), you probably don't want to use this. Probably, it wouldn't fit Ulf as well anymore :)
