### ArchLinux
#### ArchLinux Install
```sh

# 安装系统
$ pacstrap /mnt base linux linux-firmware 

进入新系统
$ arch-chroot /mnt
$ ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtiem #设置时区

# 设置系统语言
$ nvim /etc/locale.gen
  en_US.UTF-8 UTF-8

# 生成本地语言信息
$ locale-gen

# 设置本地语言环境变量
$ nvim /etc/locale.conf
  LANG=en_US-UTF-8

# 主机设置
$ nvim /etc/hostname
  se7en-pc

# 生成hosts
$ nvim /etc/hosts
  127:0:0:1      localhost   # 中间为Tab键
  ::1            localhost
  127:0:0:1      se7en-pc.localdomain     se7en-pc

# 安装pacman包
$ pacman -S grub efibootmgr xorg networkmanager inter-ucode wget git nitrogen rofi zsh python
$ pacman -S ttf-hannom noto-fonts noto-fonts-extra noto-fonts-emoji noto-fonts-cjk wqy-zenhei wqy-microhei  # 中文字体

# 激活启用NetworkManager
$ systemctl enable NetworkManager

# 给root用户设置密码
$ passwd
```

#### pacman
```sh
# 壁纸
sudo pacman -S nitrogen

# 程序启动器
sudo pacman -S rofi

# 剪切板
sudo pacman -S xclip 
```

#### yay
```sh
sudo pacman -S base-devel
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```
#### xinitrc
```sh
sudo pacman -S xorg-xinit
sudo cp /etc/X11/xinit/xinitrc .xinitrc
sudo nvim .xinitrc


################## Start #####################
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
fcitx &
picom -CGb &
flameshot &
exec slstatus &
exec dwm
exec dbus-launch dwm
################## End #####################
```

#### DWM
```sh
git clone https://git.suckless.org/dwm
```

#### dwm-patches
[suckless](https://dwm.suckless.org/) 
```sh
# restartsig
sudo wget https://dwm.suckless.org/patches/restartsig/dwm-restartsig-20180523-6.2.diff

# alpha
sudo wget https://dwm.suckless.org/patches/alpha/dwm-alpha-20201019-61bb8b2.diff

# viewontag
sudo wget https://dwm.suckless.org/patches/viewontag/dwm-r1522-viewontag.diff

# ratatestack
sudo wget https://dwm.suckless.org/patches/rotatestack/dwm-rotatestack-20161021-ab9571b.diff

# vanitygaps
sudo wget https://dwm.suckless.org/patches/vanitygaps/dwm-vanitygaps-20190508-6.2.diff

# uselessgap
sudo wget https://dwm.suckless.org/patches/uselessgap/dwm-uselessgap-20200719-bb2e722.diff
```

#### patch order
```sh
sudo patch -p1 < patches/***.diff
sudo make clean install
```


#### slstatus
```sh
git clone https://git.suckless.org/slstatus
cd slstatus
sudo make clean install
```

#### rofi


#### ranger
```sh
yay -S atool w3m

################# Start zathura打开和预览pdf文件 ####################
sudo pacman -S zathura zathura-djvu zathura-pdf-poppler zathura-ps
cd ~/.config
git clone https://gitlab.com/HiPhish/zathura-config.git
######################### End zathura ###############################

# 预览图片
sudo pacman -S poppler
```

#### alacritty
```sh
cargo install alacritty
```




#### st
```sh
git clone https://git.suckless.org/st
cd st

vim config.mk
########################
X11INC = /usr/include/X11
X11LIB = /usr/include/X11
########################

sudo make clean install
rm config.def.h

#################### patches Start ##############
wget st-alpha-0.8.2.diff
wget st-anysize-0.8.1.diff
wget st-dracula-0.8.5.diff
#################### patches End ################

sudo patch -p1 < xxx.diff
```

#### fzf
```sh
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

vim ~/.zshrc
################################ Start #########################################
[ -f ~/.fzf.zsh ] && source ~/.fzf.zsh

export FZF_DEFAULT_COMMAND='fd --hidden --follow -E ".git" -E "node_modules" . /home /etc'
export FZF_COMPLETION_TRIGGER='\'

_fzf_compgen_path() {
  fd --hidden --follow -E ".git" -E "node_modules" . /home /etc
}

_fzf_compgen_dir() {
  fd --hidden --follow -E ".git" -E "node_modules" . /home /etc
}
################################### End ##########################################
```

#### rg
```sh
sudo pacman -S ripgrep
```

#### nvim
```sh
# MarkdownPreview
sudo pacman -S glow
```

#### fanyi
```sh
npm install fanyi -g

$ vim ~/.config/fanyi/.fanyirc
{
  "iciba": true,
  "youdao": true,
  "dictionaryapi": false,
  "say": false,
  "color": true
}
```

#### archlinux 文件管理器pcmanfm
```bash
sudo pacman -S pcmanfm
```



