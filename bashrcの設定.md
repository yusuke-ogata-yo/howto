# gitの設定（下記3行を.bashrcの一番上に追加する）
source /usr/local/etc/bash_completion.d/git-prompt.sh
source /usr/local/etc/bash_completion.d/git-completion.bash
GIT_PS1_SHOWDIRTYSTATE=true

# default:cyan / root:red
if [ $UID -eq 0 ]; then
#    PS1="\[\033[31m\]\u@\h\[\033[00m\]:\[\033[01m\]\w\[\033[00m\]\\$ "
    PS1='\[\033[31m\]\u@\h\[\033[00m\]:\[\033[02m\]\w\[\033[00m\]\[\033[32m\]$(__git_ps1)\[\033[00m\]\n\\$ '
else
#    PS1="\[\033[36m\]\u@\h\[\033[00m\]:\[\033[01m\]\w\[\033[00m\]\\$ "
    PS1='\[\033[36m\]\u@\h\[\033[00m\]:\[\033[02m\]\w\[\033[00m\]\[\033[32m\]$(__git_ps1)\[\033[00m\]\n\\$ '
fi

# "-F":ディレクトリに"/"を表示 / "-G"でディレクトリを色表示
alias ls='ls -FG'
alias ll='ls -alFG'
alias vi='vim'
