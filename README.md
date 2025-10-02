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
- [⚙️ Common Setup](#-common-setup-de-wm-independent)
- [🖥️ Plasma Minimal Setup](#-plasma-minimal-setup)
  - [🖼️ Plasma Desktop](#-plasma-desktop)
  - [📦 Core Apps](#-core-apps)
  - [🪟 Enable Display Manager (SDDM)](#-enable-display-manager-sddm)
- [🌌 Hyprland Setup](#-hyprland-setup)
  - [🖼️ Hyprland Environment](#-hyprland-environment)
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
pacman -S --needed zsh git fastfetch htop btop eza bat less tree colordiff man-db lf lm_sensors 7zip fwupd
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
> **lm_sensors**: hardware sensors  
> **7zip**: compression  
> **fwupd**: firmware updater

### 🌐 Web, Office & Notifications
```bash
pacman -S --needed firefox libnotify libreoffice-fresh hunspell-{fr,es_es,en_us} gimp keepassxc
```
> **Firefox**: web browser  
> **libnotify**: notifications support  
> **LibreOffice Fresh**: office suite  
> **hunspell-xxx**: spell-check dictionaries (French, Spanish, English)  
> **GIMP**: image editor  
> **KeePassXC**: password manager

### 🕹️ Gaming
```bash
pacman -S --needed steam-native-runtime {,lib32-}gamemode
```
> **steam-native-runtime**: Steam client  
> **gamemode / lib32-gamemode**: optimize performance while gaming

---

## 🖥️ Plasma Minimal Setup

### 🖼️ Plasma Desktop
```bash
pacman -S --needed aurorae bluedevil breeze breeze-gtk breeze-plymouth drkonqi \
  kactivitymanagerd kde-cli-tools kde-gtk-config kdecoration kdeplasma-addons \
  kgamma kglobalacceld kinfocenter kmenuedit kpipewire kscreen kscreenlocker \
  ksystemstats kwallet-pam kwayland kwin layer-shell-qt libkscreen libksysguard \
  libplasma milou ocean-sound-theme oxygen oxygen-sounds plasma-activities \
  plasma-activities-stats plasma-browser-integration plasma-desktop plasma-disks \
  plasma-firewall plasma-integration plasma-nm plasma-pa plasma-systemmonitor \
  plasma-workspace plasma-workspace-wallpapers plasma5support plymouth-kcm \
  polkit-kde-agent powerdevil qqc2-breeze-style sddm-kcm systemsettings \
  xdg-desktop-portal-kde
```
> **aurorae**: window decoration engine  
> **bluedevil**: Bluetooth integration  
> **breeze / breeze-gtk / breeze-plymouth**: default KDE themes  
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
> **plasma-activities / plasma-activities-stats**: activity tracking  
> **plasma-browser-integration**: browser integration with Plasma  
> **plasma-desktop**: main Plasma desktop shell  
> **plasma-disks**: monitor disk health (SMART)  
> **plasma-firewall**: firewall management GUI  
> **plasma-integration**: Qt integration in Plasma  
> **plasma-nm**: network manager applet  
> **plasma-pa**: audio volume applet  
> **plasma-systemmonitor**: system monitoring app  
> **plasma-workspace / plasma-workspace-wallpapers**: Plasma workspace & wallpapers  
> **plasma5support**: compatibility libraries for old Plasma 5 code  
> **plymouth-kcm**: settings module for Plymouth  
> **polkit-kde-agent**: PolicyKit authentication agent  
> **powerdevil**: power management daemon  
> **qqc2-breeze-style**: Breeze style for Qt Quick Controls 2  
> **sddm-kcm**: SDDM settings in System Settings  
> **systemsettings**: Plasma system configuration tool  
> **xdg-desktop-portal-kde**: desktop portal implementation for KDE

### 📦 Core Apps
```bash
pacman -S --needed dolphin ffmpegthumbs ark kwallet
```
> **Dolphin**: file manager  
> **ffmpegthumbs**: video thumbnails in Dolphin  
> **Ark**: archive manager  
> **KWallet**: secure password storage (system keyring)

### 🪟 Enable Display Manager (SDDM)
```bash
systemctl enable sddm.service
```
> Enable graphical login

---

## 🌌 Hyprland Setup

### 🖼️ Hyprland Environment
```bash
pacman -S --needed hyprland swww waybar rofi mako hypridle hyprlock wl-clipboard cliphist \
  grim slurp swappy qt{5,6}{ct,-wayland} xdg-{user-dirs,desktop-portal-{gtk,hyprland}}
```
> **hyprland**: window manager (Wayland)  
> **swww**: wallpaper manager  
> **waybar**: status bar  
> **rofi**: app launcher  
> **mako**: notifications daemon  
> **hypridle**: idle management  
> **hyprlock**: screen lock  
> **wl-clipboard / cliphist**: clipboard tools  
> **grim / slurp / swappy**: screenshot utilities  
> **qt5ct / qt6ct**: Qt theming control  
> **xdg-user-dirs / xdg-desktop-portal-gtk / xdg-desktop-portal-hyprland**: XDG portals

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
> **gnome-keyring**: password/key manager  
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
yay -S arch-update vscodium-bin ventoy-bin proton-ge-custom-bin xpadneo-dkms-git {,lib32-}mangohud-git kdrive-bin
```
> **arch-update**: Arch Linux update notifier  
> **vscodium-bin**: open-source build of VS Code  
> **ventoy-bin**: bootable USB creation tool  
> **proton-ge-custom-bin**: custom Proton build for gaming  
> **xpadneo-dkms-git**: Xbox controller driver  
> **mangohud / lib32-mangohud**: FPS overlay and performance metrics  
> **kdrive-bin**: Infomaniak kDrive client

---

✅ Done! Choose **Plasma Minimal** or **Hyprland**, depending on your workflow 🎉
