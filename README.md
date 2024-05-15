## change pacman source

- change source rank

choose mirror – `sudo pacman-mirrors -i -c China -m rank`

append the following at `/etc/pacman.conf`
```
[archlinuxcn]
SigLevel = TrustAll
Server = http://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

[arch4edu]
SigLevel = TrustAll
Server = http://mirrors.tuna.tsinghua.edu.cn/arch4edu/$arch
```

import GPG key – `sudo pacman -Syy && sudo pacman -S archlinuxcn-keyring`

update system – `sudo pacman -Syu`

## git config
`git config --global user.name GuoKunchang && git config --global user.email 18213857028@163.com`

`ssh-keygen -t ed25519 -C "18213857028@163.com"`

## turn off beep

> [PC speaker](https://wiki.archlinux.org/title/PC_speaker)
> Another way is to uncomment or add this line in `/etc/inputrc` or `~/.inputrc`:
> `set bell-style none`

## install yay
`sudo pacman -Sy base-devel && sudo pacman -Sy yay`

## issue: [tsinghua no longer support aur source](https://blog.51cto.com/u_14597003/5989103)
remove all entries containing "aur.tsinghua.edu.cn"

## sogou pinyin input

install fcitx-configtool: `sudo pacman -S fcitx-configtool`

download [deb file](https://shurufa.sogou.com/linux)

install and change configurations: `yay -S fcitx-sogoupinyin --editmenu` (if checksum error still occurs, package cleaning is needed).

replace `curl -s $url | grep -o "https://[0-9a-z:\/\._-]*/$filename" | xargs curl -o $startdir/$filename` with `cp ~/Downloads/sogoupinyin_4.2.1.145_amd64.deb $startdir/$filename`

add environment variables as follows:

```
# ~/.xporfile
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
```

then open configure panel to add input method

## neovim
`sudo pacman -S neovim`

`git clone https://github.com/LazyVim/starter ~/.config/nvim && rm -rf ~/.config/nvim/.git && nvim`

enable configurations by tapping `LazyVim Extras`

## tmux

## clash
`https://feed.iggv5.com/c/ed54bd84-e6b6-4846-8567-61d5a3021203/platform/clash/iGG-iGuge`

## flameshot

`sudo pacman -S flameshot`

## typora

`yay -S typora`

## nvidia driver

![image-20240302211353871](./assets/image-20240302211353871.png)

to handle case that cuda randomly crashes causing `cuda init error`, 
execute `sudo modprobe -r nvidia_uvm && sudo modprobe nvidia_uvm`

## mozilla

- account recovery key – `AH1W 8WD7 KKFD HQ4C 3TRX Z03J VB14 83BD`

## zsh

- install oh-my-zsh – `curl -L http://install.ohmyz.sh | sh`
- change zsh as default – `chsh -s /bin/zsh`

## pytorch

`pip3 install torch torchvision torchaudio`

be careful to check if cuda version matches torch version

## zoxide

add `eval "$(zoxide init zsh)"` to `~/.zshrc`

## WPS
```
yay -S ttf-wps-fonts wps-office-mui-zh-cn wps-office-mime-cn wps-office-cn
yay -S wps-office-fonts ttf-ms-fonts
yay -S ttf-wps-fonts libtiff5
```
```
install `fakechinese` fonts: `winetricks fakechinese`, 
then install wechat `wine [path to wechat_x86.exe]`

## zip file encoded with `gbk`
install `unarchiver` with `sudo pacman -S unarchiver`, then unzip file with `unar [filename]`
