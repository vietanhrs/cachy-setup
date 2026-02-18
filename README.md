# cachy-setup
My Setup for the Cachy OS Linux Distro
```
           .-------------------------:                    anhtv@nitrocachy
          .+=========================.                    ----------------
         :++===++==================-       :++-           OS: CachyOS x86_64
        :*++====+++++=============-        .==:           Host: Nitro ANV15-51 (V1.26)
       -*+++=====+***++==========:                        Kernel: Linux 6.18.3-2-cachyos
      =*++++========------------:                         Uptime: 8 hours, 13 mins
     =*+++++=====-                     ...                Packages: 1445 (pacman)
   .+*+++++=-===:                    .=+++=:              Shell: fish 4.3.3
  :++++=====-==:                     -*****+              Display (Samsung Electric Company 23"): 1920x1080 in 23", 60 Hz [External] *
 :++========-=.                      .=+**+.              Display (BOE0B02): 1920x1080 in 15", 144 Hz [Built-in]
.+==========-.                          .                 DE: GNOME 49.2
 :+++++++====-                                .--==-.     WM: Mutter (Wayland)
  :++==========.                             :+++++++:    WM Theme: Adwaita
   .-===========.                            =*****+*+    Theme: Adwaita [GTK2/3/4]
    .-===========:                           .+*****+:    Icons: Adwaita [GTK2/3/4]
      -=======++++:::::::::::::::::::::::::-:  .---:      Font: SauceCodePro Nerd Font Medium (11pt) [GTK2/3/4]
       :======++++====+++******************=.             Cursor: Adwaita (24px)
        :=====+++==========++++++++++++++*-               Terminal: ghostty 1.2.3-arch2.1
         .====++==============++++++++++*-                Terminal Font: Source Code Pro Medium (10pt)
          .===+==================+++++++:                 CPU: 13th Gen Intel(R) Core(TM) i7-13620H (16) @ 4.90 GHz
           .-=======================+++:                  GPU 1: NVIDIA GeForce RTX 2050 [Discrete]
             ..........................                   GPU 2: Intel UHD Graphics @ 1.50 GHz [Integrated]
                                                          Memory: 8.14 GiB / 23.17 GiB (35%)
                                                          Swap: 22.36 MiB / 23.17 GiB (0%)
                                                          Disk (/): 111.79 GiB / 466.41 GiB (24%) - ext4
                                                          Local IP (wlan0): 192.168.2.12/24
                                                          Battery (AP18E7M): 100% [AC Connected]
                                                          Locale: en_US.UTF-8
```

## Permanently set the MTU to 1490 to prevent slow page loading
```bash
nmcli connection show
sudo nmcli connection modify "<wifi name>" wifi.mtu 1490
sudo nmcli connection up "<wifi name>"
```

## Update keyring and system update
```bash
sudo pacman -Sy archlinux-keyring cachyos-keyring && sudo pacman -Su
```

## Essential tools
```bash
sudo pacman -S zip gnome-browser-connector ghostty discord jdk-openjdk flatpak
```

## GNOME Extensions
Requires: `gnome-browser-connector` installed above

- [App Indicators](https://extensions.gnome.org/extension/615/appindicator-support/)
- [Apps Menu](https://extensions.gnome.org/extension/6/applications-menu/)
- [Arc Menu](https://extensions.gnome.org/extension/3628/arcmenu/)
- [Blur My Shell](https://extensions.gnome.org/extension/3193/blur-my-shell/)
- [Clipboard Indicator](https://extensions.gnome.org/extension/779/clipboard-indicator/)
- [Dash To Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
- [Lockscreen Extension](https://extensions.gnome.org/extension/7472/lockscreen-extension/)
- [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Vitals](https://extensions.gnome.org/extension/1460/vitals/)

## Yay and Google Chrome + VS Code
```bash
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
yay -Syu google-chrome visual-studio-code-bin slack-desktop telegram-desktop
```

## Gaming essentials
```bash
sudo pacman -S cachyos-gaming-applications cachyos-gaming-meta
# Recommened: Open Cachy OS Hello -> App/Tweaks -> Install Gaming packages
```

## Rust setup
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env.fish"
```

## Install Node.js with nvm
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
fisher install jorgebucaran/nvm.fish
nvm ls-remote
nvm install v24 # replace with the latest LTS version
nvm use v24
npm install -g corepack
set --universal nvm_default_version v24 # set default version for new shells
```

## Git setup
```bash
ssh-keygen -t ed25519 -C "vietanhtran.uet@gmail.com"
eval "$(ssh-agent -s)"
set SSH_AUTH_SOCK /home/anhtv/.ssh/agent/<output_of_the_previous_command>
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
git config --global user.name "vietanhrs"
git config --global user.email "vietanhtran.uet@gmail.com"
```

## Install fonts
```bash
sudo pacman -S ttf-sourcecodepro-nerd adobe-source-code-pro-fonts
fc-cache -fv
```

## Install fcitx5 for Vietnamese typing
```bash
sudo pacman -S fcitx5-im fcitx5-bamboo fcitx5-configtool
sudo nano /etc/environment
```
Add these variables
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```

## Install Gruvbox theme for GNOME
```bash
yay -S gtk-engine-murrine
git clone https://github.com/Fausto-Korpsvart/Gruvbox-GTK-Theme
cd Gruvbox-GTK-Theme/themes/
./install.sh -n "Gruvbox-BL-MB"
# Then set the GNOME theme in Tweaks
```