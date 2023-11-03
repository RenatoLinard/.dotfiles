# Guia de Instalação: ArchLinux e Hyprv4

## Passo 1: Crie um Pendrive de Boot

1. Faça o download da versão mais recente do ArchLinux em [https://archlinux.org](https://archlinux.org).
2. Crie um pendrive de boot usando a imagem ISO baixada.

## Passo 2: Inicialize a Partir do Pendrive

Inicie o computador e pressione a tecla F12 para selecionar a opção de inicialização a partir do pendrive.

## Passo 3: Conecte-se à Rede Wi-Fi

Após a inicialização, ative a conexão Wi-Fi com os seguintes comandos:

```shell
iwctl
device list
adapter [nome_do_adaptador] set-property Powered on
station wlan0 show
station wlan0 scan
station wlan0 connect [nome_da_rede]
```

Digite a senha da rede Wi-Fi quando solicitado e pressione "Enter" para conectar.

## Passo 4: Saia do Utilitário iwctl

Digite "quit" para sair.

## Atualização das Chaves

### Passo 5: Inicie o pacman-key

```shell
pacman-key --init
```

### Passo 6: Popule as Chaves do Arch Linux

```shell
pacman-key --populate archlinux
```

## Instalação do ArchLinux

### Passo 7: Inicie o Instalador do ArchLinux

```shell
archinstall
```

### Passo 8: Escolha as Seguintes Opções Importantes:

- Partição principal: ext4
- Partição separada para /home: não
- Carregador de inicialização: GRUB (Sim)
- Perfil pré-programado: Instalação mínima
- Áudio: Pipewire
- Pacotes adicionais: eza, tmux, neovim, alacritty, git, github-cli, genymotion, node, kooha, scrcpy, fonts e configurações pessoais
- Configuração de rede: Use NetworkManager
- Repositórios adicionais: multilib

## Conectando à Rede Wi-Fi no ArchLinux

1. Use o comando "nmcli" para se conectar à rede Wi-Fi com o nome e a senha corretos:

```shell
nmcli device wifi connect [nome_da_rede] password [senha_da_rede]
```

2. Verifique a conectividade com a internet usando o comando "ping":

```shell
ping archlinux.org
```

Observação: Verifique se você está na pasta pessoal usando o comando "pwd".

### Passo 9: Configurar o Git e GitHub-cli

1. Configure seu nome no Git: `git config --global user.name "[seu_nome]"`
2. Configure seu email no Git: `git config --global user.email "[seu_endereco_de_email]"`
3. Faça login no GitHub-cli: `gh auth login`

### Passo 10: Instalação do Hyprv4

1. Clone o repositório Hyprv4: `git clone https://github.com/SolDoesTech/HyprV4.git`
2. Navegue até a pasta hyprv4: `cd ~/hyprv4`
3. Se o script de instalação não estiver executável, torne-o executável com o comando: `chmod +x [nome_do_script]`
4. Execute o script.
5. Durante a instalação do script, siga os passos importantes: {
   - disable wifi powersave? Yes
   - install the packages? Yes
   - copy config files? Yes
   - activate starship shell? Yes
   - Install Asus ROG software suport? No
   - digite 'reboot' e pressione "Enter".}

Programas adicionais que utilizo no dia a dia:

- Genymotion
- Node
- Kooha
- Scrcpy
