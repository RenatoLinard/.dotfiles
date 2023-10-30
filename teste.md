```markdown
# Customização do Prompt de Comandos com Starship e Paleta de Cores Rose Pine

Este arquivo contém as configurações para personalizar o prompt de comando no ambiente Bash usando a ferramenta Starship. A customização inclui a aplicação de cores e estilos com base na popular paleta de cores Rose Pine.

O Starship é uma ferramenta altamente configurável para a personalização de prompts de comandos em diversos sistemas operacionais. Ao combinar o poder do Starship com a estética única da paleta de cores Rose Pine, você pode criar um prompt de comando visualmente atraente e funcional.

Neste arquivo, você encontrará as configurações necessárias para definir a aparência e o comportamento do seu prompt de comando, incluindo a escolha de ícones, cores de fundo, cores de texto e muito mais. As configurações estão organizadas para fornecer a você o controle completo sobre como o seu prompt de comando é exibido.

Personalize seu ambiente de linha de comando com o Starship e a paleta de cores Rose Pine e aproveite um terminal elegante e funcional que reflete o seu estilo pessoal. Sinta-se à vontade para ajustar as configurações conforme suas preferências para criar uma experiência de linha de comando única.

format = """
[╭─](#f6c177)\
[░▒▓](#eb6f92)\
[ 𝓡𝓔𝓝󰣇𝓣𝓞 𝓛𝓘𝓝󰣇𝓡𝓓 ](bg:#eb6f92 fg:#191724)\
[]( fg:#eb6f92)\
[]( fg:#2f1d2e)\
$directory\
[]( fg:#2f1d2e)\
[]( fg:#26233a)\
$git_branch\
$git_status\
[▓▒░](fg:#26233a)\
\n[](#f6c177)\
\n$character"""


[character]
success_symbol = '[╰─](fg:#f6c177) '
error_symbol = '[╰─󰶯](fg:#e02416) '

[directory]
style = "fg:#eb6f92 bg:#2f1d2e"
format = "[ $path ]($style)"
truncation_length = 3
truncation_symbol = "…/"
home_symbol = " ~"

[directory.substitutions]
"Documents" = "󰈙 "
"Downloads" = " "
"Music" = " "
"Pictures" = " "

[git_branch]
symbol = " "
style = "bg:#26233a"
format = '[[ $symbol $branch ](fg:#eb6f92 bg:#26233a)]($style)'
truncation_length = 40
truncation_symbol = "…/"

[git_status]
style = "bg:#26233a"
format = '[[($all_status$ahead_behind )](fg:#eb6f92 bg:#26233a)]($style)'

[git_commit]
commit_hash_length = 4
tag_symbol = '🔖 '