cp .vimrc ~/.vimrc
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
mkdir ~/.vim/plugged

aur nvm
nvm install 10 --lts
npm install typescript --save -g
sudo pacman -S cmake
~/.vim/plugged/YouCompleteMe/install.py --ts-completer --rust-completer
