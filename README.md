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

## 🔧 Configurações de DNF & Flatpak

Instale repositórios adicionais e mantenha o cache atualizado.

```bash
# Instalar RPM-Fusion
sudo dnf install \
https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

sudo dnf update

# Instalar Flathub
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

---

## 🎮 Jogos

Para jogos, apps recomendados e outros. (Requer RPMFUSION e FLATHUB)
```bash
sudo dnf install \
lutris
steam
```

Para o Heroic game launcher (epic games), baixe o RPM no site oficial e use o comando abaixo.
lembre de alterar a versão depois do "-"
```bash
# para Heroic (epic games), baixe o original RPM e use o comando abaixo. (troque o nome.)
# sudo dnf install ./heroic-0000.x86_64.rpm
```

```bash
# ProtonPlus para baixar versões de proton. (recomendado o proton CachyOS)
flatpak install flathub com.vysp3r.ProtonPlus
```
---

## 👤 Recomendações Extras

Ferramentas adicionais úteis para melhorar sua experiência no Fedora.

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
