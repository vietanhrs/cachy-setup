# cachy-setup
My Setup for the Cachy OS Linux Distro
```ansi
           .-------------------------:
          .+=========================.
         :++===++==================-       :++-
        :*++====+++++=============-        .==:
       -*+++=====+***++==========:
      =*++++========------------:
     =*+++++=====-                     ...
   .+*+++++=-===:                    .=+++=:
  :++++=====-==:                     -*****+
 :++========-=.                      .=+**+.
.+==========-.                          .
 :+++++++====-                                .--==-.
  :++==========.                             :+++++++:
   .-===========.                            =*****+*+
    .-===========:                           .+*****+:
      -=======++++:::::::::::::::::::::::::-:  .---:
       :======++++====+++******************=.
        :=====+++==========++++++++++++++*-
         .====++==============++++++++++*-
          .===+==================+++++++:
           .-=======================+++:
             ..........................[1G[21A[58Canhtv@nitrocachy
[58C----------------
[58COS: CachyOS x86_64
[58CHost: Nitro ANV15-51 (V1.26)
[58CKernel: Linux 6.18.3-2-cachyos
[58CUptime: 8 hours, 9 mins
[58CPackages: 1445 (pacman)
[58CShell: fish 4.3.3
[58CDisplay (Samsung Electric Company 23"): 1920x1080 in 23", 60 Hz [External] *
[58CDisplay (BOE0B02): 1920x1080 in 15", 144 Hz [Built-in]
[58CDE: GNOME 49.2
[58CWM: Mutter (Wayland)
[58CWM Theme: Adwaita
[58CTheme: Adwaita [GTK2/3/4]
[58CIcons: Adwaita [GTK2/3/4]
[58CFont: SauceCodePro Nerd Font Medium (11pt) [GTK2/3/4]
[58CCursor: Adwaita (24px)
[58CTerminal: ghostty 1.2.3-arch2.1
[58CTerminal Font: Source Code Pro Medium (10pt)
[58CCPU: 13th Gen Intel(R) Core(TM) i7-13620H (16) @ 4.90 GHz
[58CGPU 1: NVIDIA GeForce RTX 2050 [Discrete]
[58CGPU 2: Intel UHD Graphics @ 1.50 GHz [Integrated]
[58CMemory: 7.79 GiB / 23.17 GiB (34%)
[58CSwap: 22.36 MiB / 23.17 GiB (0%)
[58CDisk (/): 111.79 GiB / 466.41 GiB (24%) - ext4
[58CLocal IP (wlan0): 192.168.2.12/24
[58CBattery (AP18E7M): 100% [AC Connected]
[58CLocale: en_US.UTF-8
[58C
[58C[40m   [41m   [42m   [43m   [44m   [45m   [46m   [47m   [m
[58C[100m   [101m   [102m   [103m   [104m   [105m   [106m   [107m   [m

```

## GNOME Extensions
- [App Indicators](https://extensions.gnome.org/extension/615/appindicator-support/)
- [Apps Menu](https://extensions.gnome.org/extension/6/applications-menu/)
- [Arc Menu](https://extensions.gnome.org/extension/6/applications-menu/)
- [Blur My Shell](https://extensions.gnome.org/extension/3193/blur-my-shell/)
- [Clipboard Indicator](https://extensions.gnome.org/extension/779/clipboard-indicator/)
- [Dash To Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
- [Lockscreen Extension](https://extensions.gnome.org/extension/7472/lockscreen-extension/)
- [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Vitals](https://extensions.gnome.org/extension/1460/vitals/)

## Update keyring and system update
```bash
sudo pacman -Sy archlinux-keyring cachyos-keyring && sudo pacman -Su
```

### Essential tools
```bash
sudo pacman -S zip gnome-browser-connector ghostty discord
```

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
```

## Git setup
```bash
ssh-keygen -t ed25519 -C "vietanhtran.uet@gmail.com"
set SSH_AUTH_SOCK /home/anhtv/.ssh/agent/<only_file_here>
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

## Install ibus-bamboo for Vietnamese typing
```bash
yay -S ibus-bamboo
ibus restart
env DCONF_PROFILE=ibus dconf write /desktop/ibus/general/preload-engines "['BambooUs', 'Bamboo']" && gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'Bamboo')]"
```