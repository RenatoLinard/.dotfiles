# Customização do Prompt de Comandos com Starship e Paleta de Cores Rose Pine

Este arquivo contém as configurações para personalizar o prompt de comando no ambiente Bash usando a ferramenta Starship. A customização inclui a aplicação de cores e estilos com base na popular paleta de cores Rose Pine.

O Starship é uma ferramenta altamente configurável para a personalização de prompts de comandos em diversos sistemas operacionais. Ao combinar o poder do Starship com a estética única da paleta de cores Rose Pine, você pode criar um prompt de comando visualmente atraente e funcional.

Neste arquivo, você encontrará as configurações necessárias para definir a aparência e o comportamento do seu prompt de comando, incluindo a escolha de ícones, cores de fundo, cores de texto e muito mais. As configurações estão organizadas para fornecer a você o controle completo sobre como o seu prompt de comando é exibido.

Personalize seu ambiente de linha de comando com o Starship e a paleta de cores Rose Pine e aproveite um terminal elegante e funcional que reflete o seu estilo pessoal. Sinta-se à vontade para ajustar as configurações conforme suas preferências para criar uma experiência de linha de comando única.

![Mybash_custom](https://github.com/RenatoLinard/wallpaper/blob/main/screen_bash.png)

```markdown
"$schema" = 'https://starship.rs/config-schema.json'

format = """
[╭─](fg:color_green)\
[░▒▓](color_orange)\
[󰣇](bg:color_orange fg:color_fg0)\
$username\
[](bg:color_yellow fg:color_orange)\
$directory\
[](fg:color_yellow bg:color_aqua)\
$git_branch\
$git_status\
[](fg:color_aqua bg:color_blue)\
$c\
$rust\
$golang\
$nodejs\
$php\
$java\
$kotlin\
$haskell\
$python\
[](fg:color_blue bg:color_bg3)\
$docker_context\
$conda\
[](fg:color_bg3 bg:color_bg1)\
$time\
[▓▒░](fg:color_bg1)\
$line_break$character"""

palette = 'gruvbox_dark'

[palettes.gruvbox_dark]
color_fg0 = '#d6b9a3'
color_bg1 = '#201e26'
color_bg3 = '#5b5464'
color_blue = '#70595a'
color_aqua = '#91899c'
color_green = '#a0422d'
color_orange = '#4f4349'
color_purple = '#929597'
color_red = '#5b5c5b'
color_yellow = '#929597'

[os]
disabled = false
style = "bg:color_orange fg:color_fg0"

[os.symbols]
Windows = "󰍲"
Ubuntu = "󰕈"
SUSE = ""
Raspbian = "󰐿"
Mint = "󰣭"
Macos = "󰀵"
Manjaro = ""
Linux = "󰌽"
Gentoo = "󰣨"
Fedora = "󰣛"
Alpine = ""
Amazon = ""
Android = ""
Arch = "󰣇"
Artix = "󰣇"
CentOS = ""
Debian = "󰣚"
Redhat = "󱄛"
RedHatEnterprise = "󱄛"

[username]
show_always = true
style_user = "bg:color_orange fg:color_fg0"
style_root = "bg:color_orange fg:color_fg0"
format = '[ $user ]($style)'

[directory]
style = "fg:color_fg0 bg:color_yellow"
format = "[ $path ]($style)"
truncation_length = 3
truncation_symbol = "…/"

[directory.substitutions]
"Documents" = "󰈙 "
"Downloads" = " "
"Music" = "󰝚 "
"Pictures" = " "
"Developer" = "󰲋 "

[git_branch]
symbol = ""
style = "bg:color_aqua"
format = '[[ $symbol $branch ](fg:color_fg0 bg:color_aqua)]($style)'

[git_status]
style = "bg:color_aqua"
format = '[[($all_status$ahead_behind )](fg:color_fg0 bg:color_aqua)]($style)'

[nodejs]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[c]
symbol = " "
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[rust]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[golang]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[php]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[java]
symbol = " "
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[kotlin]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[haskell]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[python]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version) ](fg:color_fg0 bg:color_blue)]($style)'

[docker_context]
symbol = ""
style = "bg:color_bg3"
format = '[[ $symbol( $context) ](fg:#83a598 bg:color_bg3)]($style)'

[conda]
style = "bg:color_bg3"
format = '[[ $symbol( $environment) ](fg:#83a598 bg:color_bg3)]($style)'

[time]
disabled = false
time_format = "%R"
style = "bg:color_bg1"
format = '[[  $time ](fg:color_fg0 bg:color_bg1)]($style)'

[line_break]
disabled = false

[character]
disabled = false
success_symbol = '[╰󰭃󰑆󰊼](bold fg:color_green)'
error_symbol = '[╰󰭃󰑆󰊼](bold fg:color_red)'
vimcmd_symbol = '[](bold fg:color_green)'
vimcmd_replace_one_symbol = '[](bold fg:color_purple)'
vimcmd_replace_symbol = '[](bold fg:color_purple)'
vimcmd_visual_symbol = '[](bold fg:color_yellow)'

