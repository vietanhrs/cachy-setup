# cachy-setup
My Setup for Cachy OS Linux Distro

## Update keyring and system update
```bash
sudo pacman -Sy archlinux-keyring cachyos-keyring && sudo pacman -Su
```

## Hyprland essentials
```bash
sudo pacman -S waybar hyprpaper hyprlauncher
```

## Yay and Google Chrome + VS Code
```bash
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
yay -S google-chrome
yay -S visual-studio-code-bin
```

## Gaming essentials
```bash
sudo pacman -S cachyos-gaming-applications cachyos-gaming-meta
```

## Rust setup
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env.fish"
```

## Install Node.js with nvm
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
nvm ls-remote
nvm install v24 # replace with the latest LTS version
nvm use v2
npm install -g corepack
```

## Git setup
```bash
ssh-keygen -t ed25519 -C "vietanhtran.uet@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
git config --global user.name "openVietAnh"
git config --global user.email "vietanhtran.uet@gmail.com"
```

