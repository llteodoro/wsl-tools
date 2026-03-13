# wsl-tools

Ansible playbook to provision a full **SRE / DevOps study environment** inside WSL (Ubuntu).

## What it installs

### Core CLI tools
| Tool | Purpose |
|---|---|
| `kubectl` | Kubernetes CLI |
| `kubectx` / `kubens` | Switch clusters and namespaces (with **fzf selectbox**) |
| `kind` | Run local Kubernetes clusters in Docker |
| `helm` | Kubernetes package manager |
| `k9s` | Terminal UI for Kubernetes clusters |
| `terraform` | Infrastructure as Code |
| `gh` | GitHub CLI |
| `fzf` | Fuzzy finder — powers kubectx/kubens picker + Ctrl-R history |
| `bat` | Syntax-highlighted `cat` |
| `eza` | Modern `ls` with git status and icons |
| `jq` / `yq` | JSON and YAML processors |
| `direnv` | Auto-loads `.envrc` per project directory |
| `docker.io` | Container runtime |
| `zsh` | Shell |

### Zsh setup
- **Powerlevel10k** prompt
- **zsh-autosuggestions** — ghost-text completions
- **zsh-completions** — extended tab completions
- **zsh-syntax-highlighting** — green = valid command, red = not found
- **zsh-history-substring-search** — ↑/↓ arrows search history by typed prefix
- **fzf key bindings** — `Ctrl+R` history, `Ctrl+T` file, `Alt+C` directory

### VS Code (WSL native), Bash color prompt, SRE aliases

## Usage

```bash
# First run or reprovisioning
ansible-playbook -vb tools-playbook.yml -K
```

> `-K` prompts for your sudo password so Ansible can use `become: yes` without running the whole process as root.

After the playbook completes, start a new zsh session:

```bash
zsh
```

Run `p10k configure` on first launch to set up your Powerlevel10k theme.

## Key aliases

```
k       = kubectl          kgp  = kubectl get pods
kgpa    = kubectl get pods -A   kga  = kubectl get all
kns     = kubens (fzf)     kcx  = kubectx (fzf)
tf      = terraform        h    = helm
d       = docker           y    = yq
ll      = eza -lah --git --icons
lt      = eza --tree --level=2
cat     = bat --style=plain
```
