# 6Sazer-s_home
#archlinux i3 gaps

#root模式下
nano .zshrc
#在最后加上
alias ll='ls -l'
alias la='ls -a'
alias vi='vim'
alias svi='sudo vim'
alias grep='grep --color=auto'
alias install='sudo pacman -S'
alias remove='sudo pacman -Rcn'
alias upgrade='sudo pacman -Syu'
alias findProc='ps -ef | grep '
alias docker='sudo docker '
alias cls='printf "\033c"'
#保存后退出，执行
source .zshrc
#编辑相关的源
sudo vim /etc/pacman.conf
#在最后加上
[archlinuxcn]
SigLevel = Optional TrustAll
Server   = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
#同时打开相关仓库，之后保存退出
#编辑~/.i3/config文件
#===============设置字体===============
font pango:Source Code Pro, EmojiOne Color 10

#===============定义$mod键为win键===============
# customized
set $mod Mod4

#===============设置窗口边框===============
new_window none
bindsym $mod+t border normal
bindsym $mod+y border pixel 1
bindsym $mod+u border none


#===============状态栏===============
bindsym $mod+m bar mode toggle
bar {
    i3bar_command i3bar -t
#    status_command i3status
    status_command py3status 
    position bottom
    modifier Shift
    separator_symbol " | "

    colors {
        background #000000CC
        #statusline #000000FF
        separator #B8F788
        focused_workspace  #B8F788 #000000AA
        active_workspace   #FFFFFF #FFFFFFAA
        inactive_workspace #AAAAAA #000000AA #AAAAAA
        urgent_workspace   #E57B85 #000000AA
    }
}

#===============窗口间距===============
gaps inner 6
gaps outer 0
smart_gaps on

#===============系统命令===============
set $mode_system  注销(O) 关机(S) 重启(R) 取消(Esc)
bindsym $mod+shift+q mode "$mode_system"
mode "$mode_system" {
    bindsym o exec i3-msg exit
    bindsym s exec systemctl poweroff
    bindsym r exec systemctl reboot
    bindsym Escape mode "default"
}

#===============鼠标聚焦===============
focus_follows_mouse no

#===============锁屏快捷键===============
# bindsym Mod4+l exec --no-startup-id i3lock -i '/home/huang/Pictures/Wallpapers/universe.png'
bindsym Mod4+l exec --no-startup-id i3lock -i 'path/to/lock/screen/wallpaper'

#===============自动启动fcitx===============
exec --no-startup-id fcitx
bindsym $mod+e exec nautilus

#===============音量控制===============
bindsym XF86AudioRaiseVolume exec --no-startup-id amixer -q sset Master 5%+
bindsym XF86AudioLowerVolume exec --no-startup-id amixer -q sset Master 5%-

#===============浮动窗口===============
# use Mouse+Mod1 to drag floating windows to their wanted position
#floating_modifier $mod

#===============打开终端===============
# bindsym $mod+Return exec i3-sensible-terminal
bindsym $mod+Return exec lilyterm

#===============关闭窗口===============
bindsym Control+Mod1+w kill

#===============打开dmenu===============
# start dmenu (a program launcher)
bindsym $mod+d exec dmenu_run
# There also is the (new) i3-dmenu-desktop which only displays applications

# bindsym Mod1+d exec --no-startup-id i3-dmenu-desktop

# change focus
#bindsym $mod+$left focus left
#bindsym $mod+$down focus down
#bindsym $mod+$up focus up
#bindsym $mod+$right focus right

# alternatively, you can use the cursor keys:
#===============窗口聚焦===============
bindsym $mod+Left focus left
bindsym $mod+Down focus down
bindsym $mod+Up focus up
bindsym $mod+Right focus right

# move focused window
#bindsym $mod+Shift+$left move left
#bindsym $mod+Shift+$down move down
#bindsym $mod+Shift+$up move up
#bindsym $mod+Shift+$right move right

# alternatively, you can use the cursor keys:
#===============窗口移动===============
bindsym $mod+Shift+Left move left
bindsym $mod+Shift+Down move down
bindsym $mod+Shift+Up move up
bindsym $mod+Shift+Right move right

#===============窗口拆分模式===============
bindsym $mod+h split h
bindsym $mod+v split v

#===============切换全屏===============
bindsym $mod+f fullscreen toggle

#===============切换布局模式===============
#bindsym $mod+s layout stacking
#bindsym $mod+w layout tabbed
#bindsym Mod1+e layout toggle split

#===============切换窗口浮动===============
bindsym $mod+Shift+space floating toggle

#===============浮动/平铺聚焦切换===============
bindsym $mod+space focus mode_toggle

#===============聚焦到父窗口===============
#bindsym $mod+a focus parent

#===============聚焦到子窗口===============
#bindsym Mod1+d focus child

#===============添加窗口到存储===============
bindsym $mod+Shift+minus move scratchpad

#===============切换存储器中的窗口===============
# Show the next scratchpad window or hide the focused scratchpad window.
# If there are multiple scratchpad windows, this command cycles through them.
bindsym Mod1+minus scratchpad show

#===============绑定workspace快捷键===============
# switch to workspace
bindsym $mod+1 workspace 1:Info
bindsym $mod+2 workspace 2:Web
bindsym $mod+3 workspace 3:Work
bindsym $mod+4 workspace 4:Work
bindsym $mod+5 workspace 5:Work
bindsym $mod+6 workspace 6:Work
bindsym $mod+7 workspace 7:Work
bindsym $mod+8 workspace 8:Other
bindsym $mod+9 workspace 9:Other
bindsym $mod+0 workspace 10:Other

#==============设置workspace默认显示到LVDS1===============
workspace "1:Info" output LVDS1
workspace "2:Web" output LVDS1
workspace "3:Dev" output LVDS1
workspace "4:Dev" output LVDS1
workspace "5:Dev" output LVDS1
workspace "6:Dev" output LVDS1
workspace "7:Dev" output LVDS1
workspace "8:Music" output LVDS1
workspace "9:Other" output LVDS1
workspace "10:Other" output LVDS1

#===============绑定移动窗口到指定workspace快捷键===============
# move focused container to workspace
bindsym $mod+Shift+1 move container to workspace 1:Info
bindsym $mod+Shift+2 move container to workspace 2:Web
bindsym $mod+Shift+3 move container to workspace 3:Work
bindsym $mod+Shift+4 move container to workspace 4:Work
bindsym $mod+Shift+5 move container to workspace 5:Work
bindsym $mod+Shift+6 move container to workspace 6:Work
bindsym $mod+Shift+7 move container to workspace 7:Work
bindsym $mod+Shift+8 move container to workspace 8:Other
bindsym $mod+Shift+9 move container to workspace 9:Other
bindsym $mod+Shift+0 move container to workspace 10:Other

#===============指定程序打开后出现在指定工作区===============
assign [class="chrome"] 2:Web
# assign [class="idea"] 3:Dev
# assign [class="VirtualBox"] 9:Other

#===============重新加载配置===============
# reload the configuration file
bindsym $mod+Shift+c reload

#===============重启i3===============
# restart i3 inplace (preserves your layout/session, can be used to upgrade i3)
bindsym $mod+Shift+r restart

#===============退出i3===============
# exit i3 (logs you out of your X session)
bindsym $mod+Shift+e exec "i3-nagbar -t warning -m '是否确定退出i3? 这将导致所有工作窗口被关闭.' -b '确定' 'i3-msg exit'"

#===============调整窗口大小===============
# resize window (you can also use the mouse for that)
mode "resize" {
        # same bindings, but for the arrow keys
        bindsym Left        resize shrink width 10 px or 10 ppt
        bindsym Down        resize grow height 10 px or 10 ppt
        bindsym Up          resize shrink height 10 px or 10 ppt
        bindsym Right       resize grow width 10 px or 10 ppt

        # back to normal: Enter or Escape
        bindsym Return mode "default"
        bindsym Escape mode "default"
}

#===============绑定调整窗口大小快捷键===============
bindsym $mod+r mode "resize"

#===============开启i3时自启动项===============
exec_always --no-startup-id feh --bg-fill path/to/background/image
exec i3-config-wizard
exec --no-startup-id i3-msg "workspace 1:Info"
exec compton &

#========================================================================================================
install noto-fonts-emoji
#修改~/.i3status. conf文件
general {
    output_format = "i3bar"
    colors = true
    color_good = "#BBBBBB"
    color_bad = "#CC1616"
    color_degraded = "#55858E"
    interval = 1
}

order += "sysdata"
order += "cpu_usage"
order += "cpu_temperature 0"
order += "net_rate"
order += "imap"
order += "time"
order += "volume_status"
order += "static_string screenshot"
order += "dpms"

sysdata {
    format = "📈 {mem_used}G 📉 {mem_used_percent}%"
    color = "#48CCCD"
}

cpu_usage {
    format = "🔲 %usage"
    color = "#52D017"
}

cpu_temperature 0 {
    format = "♨️ %degrees °C"
    max_threshold = 65
    path = "/sys/class/thermal/thermal_zone0/temp"
    color = "#CCFB5D"
}

net_rate {
    interfaces = "enp0s25"
    format = "🔻{down} 🔺{up}"
    color = "#FFDB58"
}

imap {
    cache_timeout = 60
    format = "📩 {unseen}"
    imap_server = 'imap.gmail.com'
    mailbox = 'INBOX'
    name = 'you/name'
    password = 'you/mail/password'
    port = '993'
    user = 'your/mail'
    new_mail_color = "#F87431#F62217"
    on_click 1 = 'exec google-chrome-stable https://mail.google.com/mail'
    color = "#FCDFFF"
}

time {
    format = "🕔 %Y-%m-%d %H:%M:%S"
    color = "#9E7BFF"
}

volume_status {
    format = "🔊 {percentage}%"
    cache_timeout = 1
    device = "default"
    thresholds = [
        (0, "#A0CFEC"),
        (10, "#82CAFF"),
        (20, "#79BAEC"),
        (30, "#3BB9FF"),
        (40, "#56A5EC"),
        (50, "#5CB3FF"),
        (60, "#1589FF"),
        (70, "#157DEC"),
        (80, "#306EFF"),
        (90, "#2B65EC")
    ]
}

static_string 'screenshot' {
    format = "🖥"
        on_click 1 = "exec gnome-screenshot"
        color = "#C44975"
}

dpms {
    format_on = "🖥 DPMS"
    format_off = "🖥 DPMS"
    color_on = "#F9B7FF"
    color_off = "#6B9299"
}

#编辑vim ~/.xinitrc文件，添加
export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
export LC_CTYPE=en_US.UTF-8

export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx

exec i3
exec sogou-qimpanel

#vim ~/.zshrc，最后加上
[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && exec startx



