```markdown
# Passo a Passo: Instalação do ArchLinux e Hyprv4

## Passo 1: Crie um pen drive bootável

- Baixe a versão atualizada do ArchLinux em [https://archlinux.org](https://archlinux.org).
- Crie um pen drive bootável com a imagem ISO baixada.

## Passo 2: Inicialize a partir do pen drive

- Inicie o computador e pressione a tecla F12 para selecionar a opção de inicialização a partir do pen drive.

## Passo 3: Conecte-se à rede Wi-Fi

- Após a inicialização, ative a conexão Wi-Fi com os seguintes comandos:
  ```shell
  iwctl
  device list
  adapter [nome_do_adaptador] set-property Powered on
  station wlan0 show
  station wlan0 scan
  station wlan0 connect [nome_da_rede]```
  Digite a senha da rede Wi-Fi quando solicitado e pressione "Enter" para conectar.

## Passo 4: Saia do utilitário iwctl

- Digite "quit" para sair.

## Atualização das Chaves

### Passo 5: Inicie o pacman-key

```shell
pacman-key --init
```

### Passo 6: Popule as chaves do Arch Linux

```shell
pacman-key --populate archlinux
```

## Instalação do ArchLinux

### Passo 7: Inicie o instalador do ArchLinux

```shell
archinstall
```

### Passo 8: Durante a instalação, selecione os seguintes programas adicionais para instalar:

- eza
- tmux
- neovim
- alacritty
- git
- github-cli

### Passo 9: Escolha as seguintes opções importantes:

- Partição principal: ext4
- Partição separada para /home: não
- Carregador de inicialização: GRUB (Sim)
- Perfil pré-programado: Instalação mínima
- Áudio: Pipewire
- Pacotes adicionais: eza, tmux, neovim, alacritty, git e github-cli
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

Ao seguir este guia passo a passo, você terá o ArchLinux instalado com o ambiente Hyprv4 personalizado e uma conexão Wi-Fi funcionando. Certifique-se de ajustar os nomes das redes e as senhas de acordo com a sua configuração.
```

Agora você pode copiar e colar este conteúdo no seu repositório do GitHub, e ele será exibido em um formato organizado e legível.



   os seguintes programas: genymotion, node, kooha, scrcpy; fonts e adcionar as configurações pessoais










