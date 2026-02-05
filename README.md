# 🐧 Fedora-config

Um guia simples e prático para melhorar a experiência de uso do Fedora Linux.

Se você encontrar alguma informação incorreta ou uma melhoria, abra uma issue ou envie um pull request — contribuições são bem-vindas!

---

## 📋 Conteúdo

1. [Atualização do sistema](#atualização-do-sistema)
2. [Repositórios e Flathub](#repositórios-e-flathub)
3. [Instalação de jogos e utilitários](#instalação-de-jogos-e-utilitários)
4. [Ferramentas úteis](#ferramentas-úteis)
5. [Cuidados e boas práticas](#cuidados-e-boas-práticas)

---

## 🔄 Atualização do sistema

Manter o sistema atualizado é essencial para segurança e estabilidade.

- Atualizar todos os pacotes e dados de repositórios:

```bash
sudo dnf upgrade --refresh -y
```

---

## 🔧 Repositórios e Flathub

Adicione repositórios úteis e mantenha o Flatpak configurado.

- Instalar RPM Fusion (free + nonfree):

```bash
sudo dnf install \
  https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm -y
```

- Habilitar Flathub (Flatpak):

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

---

---

## 🎮 Instalação de launchers e utilitários

Recomendações para jogos (requer RPM Fusion e Flathub):

- Instalar clientes comuns:

```bash
sudo dnf install lutris steam -y
```

- Heroic (recomendado instalar via Flatpak):

```bash
flatpak install flathub com.heroicgameslauncher.hgl -y
```

- Gerenciador de versões Proton

```bash
flatpak install flathub com.vysp3r.ProtonPlus -y
```

---

## ⚙️ Ferramentas úteis

- Bottles (via Flatpak) e Wine (via DNF):

```bash
flatpak install flathub com.usebottles.bottles -y
sudo dnf install wine -y
```

- Webapp Manager (COPR) — pode apresentar pequenos bugs visuais:

```bash
sudo dnf copr enable bazzite-org/webapp-manager -y
sudo dnf install webapp-manager -y
```

- Minecraft (ex.: Bedrock/launchers): prefira versões do Flathub ou repositórios confiáveis. Se houver problemas, verifique permissões e sandbox do Flatpak antes de aplicar workarounds.

- Goanime (exemplo de instalação com Go):

```bash
sudo dnf install golang -y
go install github.com/alvarorichard/Goanime/cmd/goanime@latest
cd go/bin
sudo mv goanime /usr/bin/
cd
goanime
```

---

## ⚠️ Cuidados e boas práticas

- **Faça backup** antes de executar comandos que possam alterar seu sistema.
- **Entenda** os comandos antes de copiá-los e colá-los no terminal.
- Em caso de problemas, tente reverter a ação ou abra uma issue com detalhes (comandos executados, logs e versão do Fedora).

---

**Última atualização:** Fevereiro 2026  
**Contribuições:** Bem-vindas — abra uma issue ou envie um pull request.
