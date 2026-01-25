# 🐧 Fedora-config

Um guia para uma pequena melhora na experiência de uso do Fedora Linux.

Caso algo nesse codigo possa dar problema, altere e avise, nao quero atrapalhar ninguem ou tambem caso saiba de algo que ajude, compartilhe.

---

## 📋 Tabela de Conteúdos

1. [Atualizações do Sistema](#atualizações-do-sistema)
2. [Configurações de DNF](#configurações-de-dnf)
3. [Limpeza Básica](#limpeza-básica)
4. [Gerenciamento de Energia](#gerenciamento-de-energia)
5. [Desktop Environment](#desktop-environment)

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
# install RPM-Fusion
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
```

---

## ⚡ Gerenciamento de Energia

### Para Laptop - Instalar PowerTop

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

## 🖥️ Desktop Environment

### Otimizações GNOME (se usar GNOME)

Desabilite recursos desnecessários para melhorar a performance.

```bash
# Desabilitar efeitos de animação
# Recomendado somente em PC extremamente fraco (não ajuda muito)
gsettings set org.gnome.desktop.interface enable-animations false

# Desabilitar histórico de atividades (economia de recursos)
gsettings set org.gnome.desktop.privacy remember-recent-files false
```

---

## 👤 Pessoal

### recomendações extras

```bash
# htop
sudo dnf install htop

# steam
sudo dnf install steam

# bottles
sudo dnf install bottles

# webapp-manager (visual pode esta quebrado mas funciona perfeitamente)
sudo dnf copr enable bazzite-org/webapp-manager
sudo dnf install webapp-manager

# minecraft bedrock
flatpak install io.mrarm.mcpelauncher
```