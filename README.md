# 🐧 Fedora-config

Um guia para uma pequena melhora na experiência de uso do Fedora Linux.

Caso algo neste código possa dar problema, altere e avise. Não quero atrapalhar ninguém. Se souber de algo que ajude, compartilhe!

---

## 📋 Tabela de Conteúdos

1. [Atualizações do Sistema](#atualizações-do-sistema)
2. [Configurações de DNF](#configurações-de-dnf)
3. [Limpeza Básica](#limpeza-básica)
4. [Gerenciamento de Energia](#gerenciamento-de-energia)
5. [Recomendações Extras](#recomendações-extras)

---

## 🔄 Atualizações do Sistema

Manter seu sistema atualizado é essencial para segurança e performance.

```bash
# Atualizar todos os pacotes
sudo dnf upgrade

# Atualizar com limpeza automática
sudo dnf upgrade --refresh

# Atualizar o kernel
sudo dnf upgrade kernel
```

---

## 🔧 Configurações de DNF

Instale repositórios adicionais e mantenha o cache atualizado.

```bash
# Instalar RPM-Fusion
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# Atualizar cache
sudo dnf check-update
```

---

## 🧹 Limpeza Básica

Libere espaço removendo arquivos desnecessários e limpando caches.

```bash
# Limpar cache de pacotes antigos
sudo dnf clean all

# Remover arquivos temporários
sudo rm -rf /tmp/* &>/dev/null
sudo rm -rf ~/.cache/* &>/dev/null

# Limpar journals antigos (manter últimos 2 meses)
sudo journalctl --vacuum=time=2months

# Encontrar e remover .cache pesado
du -sh ~/.cache
rm -rf ~/.cache/mozilla  # Se usa Firefox
```

---

## ⚡ Gerenciamento de Energia

### Para Laptop - Instalar PowerTop

Otimize o consumo de energia em laptops com PowerTop.

```bash
# Instalar e configurar powerTop
sudo dnf install powertop

# Executar com análise de economia de energia
sudo powertop

# Aplicar configurações automáticas ao iniciar
sudo powertop --calibrate
sudo powertop --auto-tune
```

### Configurar Perfil de Energia

Escolha o perfil de energia mais adequado para seu dispositivo.

```bash
# Instalar power-profiles-daemon
sudo dnf install power-profiles-daemon

# Listar perfis disponíveis
powerprofilesctl list

# Definir perfil (power-saver, balanced, performance)
# Provavelmente o balanced já basta, mas caso queira, coloque em performance
powerprofilesctl set performance 

# Verificar perfil atual
powerprofilesctl get
```

---

## 👤 Recomendações Extras

Ferramentas adicionais úteis para melhorar sua experiência no Fedora.

```bash
# Steam - Plataforma de Jogos
sudo dnf install steam
```
```bash
# Bottles & wine - Compatibilidade com Windows
sudo dnf install bottles
sudo dnf install wine
```
```bash
# Webapp Manager - Gerenciador de Aplicativos Web
# contem bugs visuais
sudo dnf copr enable bazzite-org/webapp-manager
sudo dnf install webapp-manager
```
```bash
# Minecraft Bedrock - Launcher de Minecraft
flatpak install flathub io.mrarm.mcpelauncher

# caso houver um crash no login use o comando abaixo.
flatpak override --nosocket=wayland --nosocket=fallback-x11 --socket=x11 io.mrarm.mcpelauncher
```
```bash
# GOANIME - para animes, (nao e o metodo padrao de instalação mas e o que funciona.)
sudo dnf install go
go install github.com/alvarorichard/Goanime/cmd/goanime@latest
cd go/bin
sudo mv goanime /usr/bin/
cd
goanime
```
---

## 📝 Notas Importantes

- ⚠️ **Sempre faça backup** antes de executar comandos do sistema
- 🧪 **Não saia copiando e colando** entenda o que cada objeto faz
- 📖 **Leia os comentários** nos scripts antes de executar
- 🔄 Se encontrar problemas, reverta as alterações ou reporte

---

**Última atualização:** Janeiro 2026  
**Contribuições:** Bem-vindas! Sinta-se livre para melhorar este guia
