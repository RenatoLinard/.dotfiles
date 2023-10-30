```markdown
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