# ZSH INSTALL

1. sudo pacman -S zsh
2. sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
3. git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
4. git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
5. git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf && ~/.fzf/install
6. plugins=(
  git
  zsh-syntax-highlighting
  zsh-autosuggestions
  fzf
)
7. ```bash git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k```
8. ```bash ZSH_THEME="powerlevel10k/powerlevel10k"```

```zsh
### Personal Config #####

# Set the default editor
export EDITOR=nvim
export VISUAL=nvim
alias pico='edit'
alias spico='sedit'
alias nano='edit'
alias snano='sedit'
alias vim='nvim'
alias cat='batcat'

# To have colors for ls and all grep commands such as grep, egrep and zgrep
export CLICOLOR=1
export LS_COLORS='no=00:fi=00:di=00;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:*.xml=00;31:'
#export GREP_OPTIONS='--color=auto' #deprecated
alias grep="/usr/bin/grep $GREP_OPTIONS"
unset GREP_OPTIONS

# Color for manpages in less makes manpages a little easier to read
export LESS_TERMCAP_mb=$'\E[01;31m'
export LESS_TERMCAP_md=$'\E[01;31m'
export LESS_TERMCAP_me=$'\E[0m'
export LESS_TERMCAP_se=$'\E[0m'
export LESS_TERMCAP_so=$'\E[01;44;33m'
export LESS_TERMCAP_ue=$'\E[0m'
export LESS_TERMCAP_us=$'\E[01;32m'

# Alias's to modified commands
alias cp='cp -i'
alias mv='mv -i'
alias rm='trash -v'
alias mkdir='mkdir -p'
alias ps='ps auxf'
alias ping='ping -c 10'
alias less='less -R'
alias cls='clear && neofetch && lh'
alias apt-get='sudo apt-get'
alias multitail='multitail --no-repeat -c'
alias freshclam='sudo freshclam'
alias vi='nvim'
alias svi='sudo vi'
alias vis='nvim "+set si"'

# Change directory aliases
alias ~='cd ~'
alias cd..='cd ..'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'

# cd into the old directory
alias bd='cd "$OLDPWD"'

# Remove a directory and all files
alias rmd='/bin/rm  --recursive --force --verbose '

# GIT
# -----------------------------------------------------

alias gs="git status"
alias ga="git add"
alias gc="git commit -m"
alias gp="git push"
alias gpl="git pull"
alias gst="git stash"
alias gsp="git stash; git pull"
alias gcheck="git checkout"


# Alias's for multiple directory listing commands
alias la='eza -lah' # show hidden files
alias lh='eza -lh'
alias ls='eza -aFh --color=always' # add colors and file type extensions
alias lx='eza -lXBh' # sort by extension
alias lk='eza -lSrh' # sort by size
alias lc='eza -lcrh' # sort by change time
alias lu='eza -lurh' # sort by access time
alias lr='eza -lRh' # recursive ls
alias lt='eza -ltrh' # sort by date
alias lm='eza -alh |more' # pipe through 'more'
alias lw='eza -xAh' # wide listing format
alias ll='eza -Fls' # long listing format
alias labc='eza -lap' #alphabetical sort
alias lf="eza -l | egrep -v '^d'" # files only
alias ldir="eza -l | egrep '^d'" # directories only

# Use the best version of pico installed
edit ()
{
	if [ "$(type -t jpico)" = "file" ]; then
		# Use JOE text editor http://joe-editor.sourceforge.net/
		jpico -nonotice -linums -nobackups "$@"
	elif [ "$(type -t nano)" = "file" ]; then
		nano -c "$@"
	elif [ "$(type -t pico)" = "file" ]; then
		pico "$@"
	else
		nvim "$@"
	fi
}

# Extracts any archive(s) (if unp isn't installed)
extract () {
	for archive in "$@"; do
		if [ -f "$archive" ] ; then
			case $archive in
				*.tar.bz2)   tar xvjf $archive    ;;
				*.tar.gz)    tar xvzf $archive    ;;
				*.bz2)       bunzip2 $archive     ;;
				*.rar)       rar x $archive       ;;
				*.gz)        gunzip $archive      ;;
				*.tar)       tar xvf $archive     ;;
				*.tbz2)      tar xvjf $archive    ;;
				*.tgz)       tar xvzf $archive    ;;
				*.zip)       unzip $archive       ;;
				*.Z)         uncompress $archive  ;;
				*.7z)        7z x $archive        ;;
				*)           echo "don't know how to extract '$archive'..." ;;
			esac
		else
			echo "'$archive' is not a valid file!"
		fi
	done
}

#Automatically do an ls after each cd
cd ()
{
    if [ -n "$1" ]; then
        builtin cd "$@" && eza -lh
    else
        builtin cd ~ && eza -lh
    fi
}

# Returns the last 2 fields of the working directory
pwdtail ()
{
	pwd|awk -F/ '{nlast = NF -1;print $nlast"/"$NF}'
}

############## Personal's config ##########################
neofetch


alias upd='sudo pacman -Syyu'
alias dev='cd ~/devmedia_Mobile/'
alias js='cd ~/javascript/'
alias .tmux='vim .tmux.conf'
alias temp="du -h /var/cache/pacman/pkg"
alias clstemp="sudo paccache -rk1 && sudo pacman -Sc"
```
