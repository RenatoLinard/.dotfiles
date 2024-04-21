# Tmux shortcuts and configs

## Shortcuts

- Prefix - `<C-space>`

- Create new window - `prefix + c`

- Create a new session - `tmux new -s name`

- Navigate beteewen window - `prefix + n` or `prefix + p`

- Rename window - `prefix + ,`

- Kill a window - `prefix + &`

- Kill a painel - `prefix + x`

- Painels vertical - `prefix + |`

- Painels horizintal - `prefix + _`

- List session - `prefix + s` or `prefix + w`

- Attach the last session - `tmux attach`

```.tmux.conf
#################################### TMUX' CONFIG ############################

#################################### TMUX' CONFIG ############################

#################################### TMUX' CONFIG ############################

# Define o tipo do terminal...
set -g default-terminal "xterm-256color"
# Habilita cores de 24 bits...
set -sa terminal-overrides ",xterm-256color:Tc"
# Set true color
set-option -sa terminal-overrides ",xterm*:Tc"

# Passa para o shell os atalhos do readline... 
set-window-option -g xterm-keys on

# Configura o atraso da tecla ESC para 0ms... 
set -s escape-time 0

# Setting the prefix from C-b to C-Space
unbind C-b
set -g prefix C-space
bind C-space send-prefix

# Reload settings
unbind r
bind r source-file ~/.tmux.conf \; display-message "Settings reloaded!"

# Remove as associações das teclas % e "...
unbind %
unbind '"'
# Associa <prefixo>h à criação de um novo painel ao lado...
bind | split-window -h
# Associa <prefixo>v à criação de um novo painel abaixo...
bind _ split-window -v

# Navegação entre painéis com Alt+<setas>...
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Índice inicial de janelas e painéis...
set -g base-index 1
set -g pane-base-index 1

# Status do prefixo pressionado:
color_prefix="#[fg=color5]#[bold]#[bg=default]"
ind_prefix="#{?client_prefix,${color_prefix}PREFIX ${lis},}"
set -g status-position bottom
# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'mcanueste/rose-pine-tmux'


# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'





```
