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
# mrs4ndman's Tmux config :)

# Custom keybindings
#
# Setting the prefix from C-b to C-Space
unbind C-b
set -g prefix C-space
bind C-space send-prefix

# Reload settings
unbind r
bind r source-file ~/.tmux.conf \; display-message "Settings reloaded!"
 
# Sets Ctrl + H / V for horizontal / vertical splits in the current working directory
bind-key h split-window -v -c "#{pane_current_path}"
bind-key v split-window -h -c "#{pane_current_path}"
#
# Breaks current pane into its own window
bind-key p break-pane -d
#
# Pane resizing
bind-key -r C-h resize-pane -L
bind-key -r C-j resize-pane -D
bind-key -r C-k resize-pane -U 
bind-key -r C-l resize-pane -R
#
# Pane swapping
bind-key -r Down swap-pane -D
bind-key -r Up swap-pane -U
#
# Vim motions & usefeul binds | Atajos de Vim y algunos útiles
bind-key -r V copy-mode
set-window-option -g mode-keys vi
bind-key x kill-pane # Skip kill-pane confirmation | Se salta la confirmación de cerrar el "pane"

# Custom prefix-based stuff
# Scratchbuf + new window shortcut
unbind t
bind-key -r t neww
bind-key -r T display-popup -E
# bind-key -r S display-popup -E "nvim ~/scratch.md"

# Setting keybinds for lazygit, tmux-cht-sh & tmux scripts
bind-key -r g run-shell "tmux neww lazygit"
bind-key -r i run-shell "tmux neww ~/.local/scripts/tmux-cht.sh"
bind-key -r f run-shell "tmux neww ~/.local/scripts/tmux-sessionizer"
bind-key -r N run-shell "tmux neww ~/.local/scripts/tmux-navigator.sh"
# bind-key -r S run-shell "tmux neww ~/.local/scripts/tmux-sender.sh"
# BUG: I don't really know why this isn't working
# bind-key -r O run-shell "tmux new-session -ds obsidian -c ~/Documents/Obsidian\ Vaults"

# Window and client navigation
bind-key -n M-h if -F "#{@navi-state}" "send-keys M-h" "select-pane -LZ"
bind-key -n M-j if -F "#{@navi-state}" "send-keys M-j" "select-pane -DZ"
bind-key -n M-k if -F "#{@navi-state}" "send-keys M-k" "select-pane -UZ"
bind-key -n M-l if -F "#{@navi-state}" "send-keys M-l" "select-pane -RZ"

bind-key -T copy-mode-vi 'M-h' select-pane -L
bind-key -T copy-mode-vi 'M-j' select-pane -D
bind-key -T copy-mode-vi 'M-k' select-pane -U
bind-key -T copy-mode-vi 'M-l' select-pane -R
bind-key -T copy-mode-vi 'M-\' select-pane -l

bind -n M-d detach-client
bind -n M-e new-window nvim
bind -n M-f display-popup -w 50% -h 80% -E ~/.local/scripts/tmux-sessionizer
bind -n M-g display-popup -w 80% -h 80% -E lazygit
bind -n M-r source-file ~/.tmux.conf
bind -n M-q choose-session
bind -n M-t display-popup -E "tmux new-session -A -s scratch-term -c /home/mrsandman"
bind -n M-w display-popup -E ~/.local/scripts/tmux-navigator.sh
bind -n M-v split-window -h -c "#{pane_current_path}"
bind -n M-s split-window -v -c "#{pane_current_path}"
bind -n M-x kill-pane
bind -n 'M-N' next-layout
bind -n 'M-P' previous-layout
bind -n 'M-n' swap-window -dt +1
bind -n 'M-p' swap-window -dt -1
bind -n M-H switch-client -p
bind -n M-J previous-window
bind -n M-K next-window
bind -n M-L switch-client -n
bind -n M-S display-popup -E "tmux new-session -A -s scratch nvim /home/mrsandman/scratch.md"
bind -n M-T split-window -v -l 15 -c "#{pane_current_path}"
bind -n M-C neww
bind -n M-X kill-window

# Sets the status bar (and its refresh rate) on top | Coloca la barra de estado (y refresco) arriba
# set -g status-position top
set -g status-interval 1

# Mouse scroll support on Tmux (disable it on your terminal emulator if needed)
# Habilita el uso de ratón (deshabilitalo en tu emulador de terminal si interfiere)
set -g mouse on

# Setting base window number to 1 | Tomando 1 como número de base para ventanas y divisiones
set -g base-index 1
set -g pane-base-index 1
set-option -g renumber-windows on

# NVIM integration config | Configuración para integrar con Neovim:
set-option -g focus-events on
# zero-out escape time delay
set-option -sg escape-time 0

# Sets default terminal for fixing colors inside Neovim | Fija el terminal para mantener
# los colores correctos dentro de Neovim
set -g default-terminal "tmux-256color"
set -ga terminal-features ',xterm-kitty:RGB'
set -g terminal-overrides ',*:Smulx=\E[4::%p1%dm'  # undercurl support
set -g terminal-overrides ',*:Setulc=\E[58::2::%p1%{65536}%/%d::%p1%{256}%/%{255}%&%d::%p1%{255}%&%d%;m'  

set-option -g allow-rename off
set -g @rose_pine_bar_bg_disable 'on'
set -g @rose_pine_bar_bg_disable_color_option '0'
set -g monitor-activity on
set -g status-justify absolute-centre

# List of plugins | Lista de plugins + Gestor
set -g @plugin 'tmux-plugins/tpm' # Plugin manager | Gestor plugins
set -g @plugin 'tmux-plugins/tmux-sensible' # Sensible default config | Config de sentido común
set -g @plugin 'tmux-plugins/tmux-resurrect' # Never ending persistent sessions
set -g @plugin 'tmux-plugins/tmux-continuum' # Continuous saving + start
set -g @plugin 'tmux-plugins/tmux-yank' # System clipboard for tmux yanks
set -g @plugin 'tmux-plugins/tmux-copycat' # System clipboard for tmux yanks

set -g @plugin 'rose-pine/tmux' # My very own Rose Pine colorscheme
# set -g @plugin 'MunifTanjim/tmux-mode-indicator' # Cool AF mode indicator 😉

# Rosé Pine theme config
set -g @rose_pine_variant 'main'
set -g @rose_pine_directory 'on'
set -g @rose_pine_show_current_program 'on'
set -g @rose_pine_date_time '%H:%M | %a'
set -g @rose_pine_status_left_prepend_section '#(cat #{socket_path}-\#{session_id}-vimbridge)'
set -g @rose_pine_status_right_append_section '#(cat #{socket_path}-\#{session_id}-vimbridge-R)'
# set -g @rose_pine_status_left_append_section 'll'
# set -g @rose_pine_status_right_prepend_section 'rr'
# set -g @rose_pine_bar_bg_transparent_option '7'
# set -g @rose_pine_disable_active_window_menu 'on'
# set -g @rose_pine_default_window_behavior 'on'
# set -g @rose_pine_show_pane_directory 'on'
# set -g @rose_pine_prioritize_windows 'on'
# set -g @rose_pine_width_to_hide '80'
# set -g @rose_pine_window_count '5'
# set -g @rose_pine_user 'on'
# set -g @rose_pine_host 'on'
# set -g @rose_pine_left_separator ' > '
# set -g @rose_pine_right_separator '  '
# set -g @rose_pine_active_window_color 'love'
# set -g @rose_pine_window_status_separator ''
# set -g @rose_pine_window_tabs_enabled 'on' -- OLD

# Set permanent sessions = on
# set -g @continuum-restore 'on'

# set -g status-right '#{tmux-mode-indicator}'

# Initialise TMUX plugin manager
run-shell "~/.local/scripts/navi.tmux"
run '~/.tmux/plugins/tpm/tpm'
set -g status-left-length 100
set -g status-right-length 100
```
