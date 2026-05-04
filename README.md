# Ansible Workstation Playbooks

This repository contains two Ansible playbooks tailored for different environments: a WSL-based study environment and a full native Ubuntu production workstation for a Senior SRE.

---

## 1. WSL Tools Study Environment (`tools-playbook.yml`)

Ansible playbook to provision a full **SRE / DevOps study environment** inside Windows Subsystem for Linux (WSL / Ubuntu). It focuses on CLI tools, terminal performance, and a pure ZSH + Powerlevel10k setup without GUI apps.

### Core Tools Installed
- **Kubernetes**: `kubectl`, `kubectx` / `kubens` (with fzf), `kind`, `helm`, `k9s`
- **IaC**: `terraform`
- **Utilities**: `gh` (GitHub CLI), `jq`, `yq`, `bat`, `eza`, `fzf`, `direnv`
- **Containers**: `docker.io`
- **Shell**: `zsh` with manual plugins (zsh-autosuggestions, zsh-completions, zsh-syntax-highlighting, zsh-history-substring-search) and **Powerlevel10k** prompt.

### Usage
```bash
ansible-playbook -vb tools-playbook.yml -K
```
> `-K` prompts for your sudo password so Ansible can use `become: yes` without running the whole process as root.

After completion, start a new `zsh` session and run `p10k configure` on first launch.

---

## 2. Ubuntu SRE Production Environment (`ubuntu-sre-playbook.yml`)

Ansible playbook designed to provision a **Production Workstation** for a Senior SRE on a native Ubuntu machine. It includes everything from the study environment, plus visual apps, advanced Cloud SDKs, and a robust Oh-My-Zsh configuration.

### Core Tools Installed
- **Kubernetes**: `kubectl`, `kubectx` / `kubens`, `kind`, `helm`, `k9s`
- **IaC**: **`tfenv`** (Terraform version manager), `vagrant`, `gomplate`
- **Cloud**: AWS CLI v2, Google Cloud SDK
- **Development**: `golang-go`, `python3`, `python3-pip`, `make`, `git`
- **Containers**: Official `docker-ce`, `docker-compose-plugin`, `docker-buildx-plugin`
- **Utilities**: `jq`, `yq`, `bat`, `eza`, `fzf`, `direnv`, `htop`, `ncdu`, `tree`, `mlocate`, `mtr`
- **GUI Apps (Ubuntu Desktop)**: `google-chrome-stable`, `virtualbox`, `flameshot`, `tilix`, `krita`, `code` (VS Code) + automatic SRE extensions.
- **Shell**: `zsh` with **Oh-My-Zsh** (Agnoster theme) and custom plugins (`zsh-autosuggestions`, `zsh-syntax-highlighting`, `zsh-completions`, `zsh-history-substring-search`).

### Usage
```bash
ansible-playbook -vb ubuntu-sre-playbook.yml -K
```

---

## Key Aliases (Available in both)

```bash
k       = kubectl          kgp  = kubectl get pods
kgpa    = kubectl get pods -A   kga  = kubectl get all
kns     = kubens (fzf)     kcx  = kubectx (fzf)
tf      = terraform        h    = helm
d       = docker           y    = yq
ll      = eza -lah --git --icons
lt      = eza --tree --level=2
cat     = bat --style=plain
```
