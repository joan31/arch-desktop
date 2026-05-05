# 🚀 Arch Desktop — Arch Linux Post-Install: Plasma Minimal / Hyprland

[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
![Arch Linux](https://img.shields.io/badge/Arch_Linux-blue?logo=arch-linux&logoColor=white)
![Plasma](https://img.shields.io/badge/Plasma_Minimal-1793d1?logo=kde&logoColor=white)
![Hyprland](https://img.shields.io/badge/Hyprland-black?logo=wayland&logoColor=white)

**Plasma Minimal OR Hyprland — your choice!**

This guide assumes you already have a **base Arch Linux system installed**  
👉 See [Arch-Fortress](https://github.com/joan31/arch-fortress) for a secure and minimal base install.

We will cover **common setup steps**, then branch into two chapters: **Plasma Minimal** or **Hyprland**.

---

## 📚 Table of Contents
- [⚙️ Common Setup](#️-common-setup-de-wm-independent)
- [🖥️ Plasma Minimal Setup](#️-plasma-minimal-setup)
  - [🖼️ Plasma Desktop](#️-plasma-desktop)
  - [📦 Core Apps](#-core-apps)
  - [🪟 Enable Display Manager (Plasma Login Manager)](#-enable-display-manager-plasma-login-manager)
- [🌌 Hyprland Setup](#-hyprland-setup)
  - [🖼️ Hyprland Environment](#️-hyprland-environment)
  - [📦 Core Apps](#-core-apps-1)
  - [🔊 Audio & Bluetooth Extras](#-audio--bluetooth-extras)
  - [🎨 Theming & Keyring](#-theming--keyring)
- [📦 AUR & User Apps](#-aur--user-apps)

---

## ⚙️ Common Setup (DE/WM Independent)

### 🎮 Drivers & Graphics
```bash
pacman -S --needed mesa {,lib32-}vulkan-radeon xorg-{xwayland,xrandr}
```
> **mesa**: OpenGL drivers  
> **vulkan-radeon / lib32-vulkan-radeon**: Vulkan drivers for AMD GPUs (32-bit for gaming)  
> **xorg-xwayland**: Run X11 apps inside Wayland  
> **xorg-xrandr**: Multi-monitor setup

### 🔊 Audio System
```bash
pacman -S --needed pipewire pipewire-{pulse,jack} wireplumber
```
> **PipeWire**: Audio & video server  
> **pipewire-pulse**: PulseAudio compatibility  
> **pipewire-jack**: JACK compatibility  
> **wireplumber**: Session manager for PipeWire

### 🛠️ Shell, Tools & Utilities
```bash
pacman -S --needed zsh git fastfetch htop btop eza bat less tree colordiff man-db \
  lf bc lm_sensors 7zip fwupd xdg-user-dirs
```
> **zsh**: modern shell  
> **git**: version control  
> **fastfetch**: system info in terminal  
> **htop / btop**: system monitors  
> **eza**: modern replacement for `ls`  
> **bat**: modern replacement for `cat`  
> **less / tree / colordiff**: file browsing & diff tools  
> **man-db**: manual pages  
> **lf**: terminal file manager  
> **bc**: command line calculator  
> **lm_sensors**: hardware sensors  
> **7zip**: compression  
> **fwupd**: firmware updater  
> **xdg-user-dirs**: user directories

### 🌐 Web, Office & Notifications
```bash
pacman -S --needed firefox libnotify libreoffice-fresh{,-fr} hunspell-{fr,es_es,en_us} \
  gimp keepassxc discord
```
> **Firefox**: web browser  
> **libnotify**: Firefox notifications support  
> **LibreOffice Fresh**: office suite (optional french interface language)  
> **hunspell-xxx**: spell-check dictionaries (French, Spanish, English)  
> **GIMP**: image editor  
> **KeePassXC**: password manager  
> **Discord**: voice and text chat

### 🔤 Fonts
```bash
pacman -S --needed ttf-{dejavu,liberation,nerd-fonts-symbols} noto-fonts{,-{emoji,cjk,extra}}
```
> **DejaVu / Liberation**: standard system fonts (compatibilité + fallback)  
> **Noto Fonts**: large Unicode coverage (emoji, CJK, extra scripts)  
> **Nerd Fonts Symbols**: icons for terminal (powerline, dev, etc.)

### 🕹️ Gaming
```bash
pacman -S --needed steam {,lib32-}{gamemode,mangohud}
```
> **steam**: Steam client  
> **gamemode / lib32-gamemode**: optimize performance while gaming  
> **mangohud / lib32-mangohud**: FPS overlay and performance metrics

---

## 🖥️ Plasma Minimal Setup

### 🖼️ Plasma Desktop
```bash
pacman -S --needed aurorae bluedevil breeze breeze-gtk drkonqi \
  kactivitymanagerd kde-cli-tools kde-gtk-config kdecoration kdeplasma-addons \
  kgamma kglobalacceld kinfocenter kmenuedit knighttime kpipewire kscreen kscreenlocker \
  ksystemstats kwallet-pam kwayland kwin layer-shell-qt libkscreen libksysguard \
  libplasma milou ocean-sound-theme oxygen oxygen-cursors oxygen-sounds plasma-activities \
  plasma-activities-stats plasma-browser-integration plasma-desktop plasma-disks \
  plasma-firewall plasma-integration plasma-login-manager plasma-nm plasma-pa \
  plasma-systemmonitor plasma-workspace plasma-workspace-wallpapers plasma5support \
  plymouth-kcm polkit-kde-agent powerdevil qqc2-breeze-style spectacle systemsettings \
  xdg-desktop-portal-kde
```
> **aurorae**: window decoration engine  
> **bluedevil**: Bluetooth integration  
> **breeze / breeze-gtk**: default KDE themes  
> **drkonqi**: crash handler  
> **kactivitymanagerd**: activity manager daemon  
> **kde-cli-tools**: command-line tools for KDE  
> **kde-gtk-config**: GTK theme integration  
> **kdecoration**: window decoration library  
> **kdeplasma-addons**: extra widgets and applets  
> **kgamma**: monitor gamma settings  
> **kglobalacceld**: global shortcut daemon  
> **kinfocenter**: system information center  
> **kmenuedit**: application menu editor  
> **knighttime**: helpers for scheduling the dark-light cycle  
> **kpipewire**: PipeWire integration for Plasma  
> **kscreen**: display configuration  
> **kscreenlocker**: screen locker  
> **ksystemstats**: system statistics service  
> **kwallet-pam**: KWallet integration with PAM  
> **kwayland**: Wayland support libraries  
> **kwin**: window manager/compositor  
> **layer-shell-qt**: layer-shell protocol support for Qt  
> **libkscreen**: backend for display management  
> **libksysguard**: system monitor libraries  
> **libplasma**: Plasma core libraries  
> **milou**: search widget (KRunner frontend)  
> **ocean-sound-theme / oxygen-sounds**: sound themes  
> **oxygen**: Oxygen widget style  
> **oxygen-cursors**: Oxygen cursors  
> **plasma-activities / plasma-activities-stats**: activity tracking  
> **plasma-browser-integration**: browser integration with Plasma  
> **plasma-desktop**: main Plasma desktop shell  
> **plasma-disks**: monitor disk health (SMART)  
> **plasma-firewall**: firewall management GUI  
> **plasma-integration**: Qt integration in Plasma  
> **plasma-login-manager**: Plasma display manager (replace SDDM)  
> **plasma-nm**: network manager applet  
> **plasma-pa**: audio volume applet  
> **plasma-systemmonitor**: system monitoring app  
> **plasma-workspace / plasma-workspace-wallpapers**: Plasma workspace & wallpapers  
> **plasma5support**: compatibility libraries for old Plasma 5 code  
> **plymouth-kcm**: settings module for Plymouth  
> **polkit-kde-agent**: PolicyKit authentication agent  
> **powerdevil**: power management daemon  
> **spectacle**: screenshot capture utility  
> **qqc2-breeze-style**: Breeze style for Qt Quick Controls 2  
> **systemsettings**: Plasma system configuration tool  
> **xdg-desktop-portal-kde**: desktop portal implementation for KDE

### 📦 Core Apps
```bash
pacman -S --needed code kcalc dolphin kdegraphics-thumbnailers ffmpegthumbs ark kwallet konsole \
  partitionmanager gwenview okular kdeconnect vlc{,-plugins-all}
```
> **code**: the open source build of VSCode editor  
> **kcalc**: calculator  
> **Dolphin**: file manager  
> **kdegraphics-thumbnailers**: PDF and PS thumbnails  
> **ffmpegthumbs**: video thumbnails in Dolphin  
> **Ark**: archive manager  
> **KWallet**: secure password storage (system keyring)  
> **Konsole**: KDE terminal emulator  
> **PartitionManager**: KDE utility to manage disks, partitions and file systems  
> **Gwenview**: image viewer  
> **Okular**: PDF reader  
> **KDEConnect**: communication with smartphone  
> **VLC**: multimedia player

### 🪟 Enable Display Manager (Plasma Login Manager)
```bash
systemctl enable plasmalogin.service
```
> Enable graphical login

---

## 🌌 Hyprland Setup

### 🖼️ Hyprland Environment
```bash
pacman -S --needed hyprland awww waybar rofi mako hypridle hyprlock wl-clipboard cliphist \
  grim slurp swappy qt{5,6}{ct,-wayland} xdg-{desktop-portal-{gtk,hyprland}}
```
> **hyprland**: window manager (Wayland)  
> **awww**: wallpaper manager  
> **waybar**: status bar  
> **rofi**: app launcher  
> **mako**: notifications daemon  
> **hypridle**: idle management  
> **hyprlock**: screen lock  
> **wl-clipboard / cliphist**: clipboard tools  
> **grim / slurp / swappy**: screenshot utilities  
> **qt5ct / qt6ct**: Qt theming control  
> **xdg-desktop-portal-gtk / xdg-desktop-portal-hyprland**: XDG portals (GTK needed for file-picker)

### 📦 Core Apps
```bash
pacman -S --needed thunar imv mpv mpv-mpris playerctl
```
> **Thunar**: file manager  
> **imv**: image viewer  
> **mpv**: video player  
> **mpv-mpris**: MPRIS support for mpv  
> **playerctl**: media player controller

### 🔊 Audio & Bluetooth Extras
```bash
pacman -S --needed pulsemixer bluez-utils cava
```
> **pulsemixer**: terminal audio mixer  
> **bluez-utils**: Bluetooth tools  
> **cava**: audio visualizer

### 🎨 Theming & Keyring
```bash
pacman -S --needed gnome-keyring gnome-themes-extra gtk-engine-murrine xsettingsd
```
> **gnome-keyring**: system password/key manager for kDrive cloud  
> **gnome-themes-extra**: extra GTK themes  
> **gtk-engine-murrine**: GTK2 theme engine  
> **xsettingsd**: XSettings daemon for GTK themes

---

## 📦 AUR & User Apps

### 🛠️ Install AUR Helper (yay)
```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
cd ..
rm -rf yay
```

### 🔄 Update
```bash
yay
```

### 🎉 Install User Applications
```bash
yay -S arch-update ventoy-bin proton-ge-custom-bin xpadneo-dkms-git kdrive-bin rtl8761b-firmware
```
> **arch-update**: Arch Linux update notifier  
> **ventoy-bin**: bootable USB creation tool  
> **proton-ge-custom-bin**: custom Proton build for gaming  
> **xpadneo-dkms-git**: Xbox controller driver  
> **kdrive-bin**: Infomaniak kDrive client  
> **rtl8761b-firmware**: TP-Link UB500 USB Bluetooth Adapter old firmware with better stability

---

✅ Done! Choose **Plasma Minimal** or **Hyprland**, depending on your workflow 🎉
