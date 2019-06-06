How to setup i3:

sudo pacman -S i3-gaps rofi rxvt-unicode python-pywal feh noto-fonts noto-fonts-cjk noto-fonts-emoji powerline powerline-fonts alsa-utils upower speedtest-cli

curl https://sh.rustup.rs -sSf | sh

aur ttf-font-awesome-4
aur i3status-rust-git

cp config ~/.config/i3/
cp status.toml ~/.config/i3/ 

// Japanese input
sudo pacman -S uim
aur mozc
aur uim-mozc

Warning: You must run the following command whenever you upgrade or (re-)install uim.
sudo uim-module-manager --register mozc

// Add to ~/.xinitrc
export GTK_IM_MODULE='uim'
export QT_IM_MODULE='uim'
uim-xim &
export XMODIFIERS='@im=uim'

// No Audio
run alsamixer and unmute and increase the master volume

start vivaldi from terminial to see what codecs are missing usually chromium-codecs-ffmpeg-extra
