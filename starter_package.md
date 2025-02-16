# Arch Linux + Hyprland installation guide
# minimal installation
# with all essential packages 
# a functional web browser and GUI terminal 


# Arch Linux and `Hyprland` installation on ROG G14 

## GOALS 

- [] Arch Linux installation from USB Boot Drive 
- [] G14 Kernels and Nvidia drivers 
- [] Hyprland installation with essential packages and functional GUI

### 1. Arch Linux installation 


##### prepare bootable usb drive
https://archlinux.org/download/
https://rufus.ie/en/

##### post installation essentials 

    system upgrade
```bash 
sudo pacman -Syu
```
    essential packages 
```bash
sudo pacman -S nano git 
```
    yay (AUR helper) 
```bash 
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
### 2. Custom Kernel and Nvidia drivers for ROG G14 

    add the repo sign key 
```bash 
pacman-key --recv-keys 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
pacman-key --finger 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
pacman-key --lsign-key 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
pacman-key --finger 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
```
    add to the /etc/pacman.conf/ (at the end)

[g14]
Server = https://arch.asus-linux.org

    G14 kernel (needed for ROG GUI to work) 
```bash
pacman -Sy linux-g14 linux-g14-headers
grub-mkconfig -o /boot/grub/grub.cfg

```
    nvidia driver (yay nvidia-dkms)
```bash
yay -S nvidia-dkms
```
    asusctl, superctl and rog-control-center 

```bash
pacman -S asusctl power-profiles-daemon
systemctl enable --now power-profiles-daemon.service
pacman -S supergfxctl switcheroo-control
systemctl enable --now supergfxd
systemctl enable --now switcheroo-control
pacman -S rog-control-center
```

### 3. Hyprland installation 

##### bare minimum
```bash
sudo pacman -S hyprland 
sudo pacman -S kitty 
sudo pacman -S firefox

[] Bluetooth 
[] Network Manager GUI 
[] 
```
##### minimal and functional 
```bash
bash <(curl -s https://raw.githubusercontent.com/mylinuxforwork/hyprland-starter/main/setup.sh)
```

### 4. Starter packages 

[] Timeshift 
[] Waybar 
[] App Launcher (rofi, Wofi) 
[] Notification service (swaync)
[] File Manager (Thunar and/or Yazi)
[] ScratchPads (pyprland)
[] xdg-desktop-wayland-portal 

### 5. Further optimization 

[] Display resolution and refresh rate 
[] Shell config  
[] Battery optimization (disable animation and blurs, power management and custom fan curve)
[] Natural Scrolling
[] Hibernate to SWAP
[] Calendar, Quick links and Shortcut Helper in status bar 

### 6. Next Step: Developer Setup

[] screen sharing and screen recording 
[] essentials (vscode, docker, virtualBox and local AI)
[] nvim config 
[] file organizer (PRs, Zettelkasten and Obsidian)
[] dotfiles management 
[] custom shell scripts 

