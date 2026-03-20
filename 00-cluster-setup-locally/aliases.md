# ⚡ Aliases & Shell Setup

Set these up before every practice session.
On exam day, run them in the first 60 seconds — before touching a single question.

---

## The Minimum (Must Have)

```bash
alias k=kubectl
source <(kubectl completion bash)
complete -F __start_kubectl k
```

These three lines alone will save you hundreds of keystrokes in a 2-hour exam.

---

## Full Alias Set (Add to ~/.bashrc or ~/.zshrc)

```bash
# Core
alias k=kubectl
source <(kubectl completion bash)
complete -F __start_kubectl k

# Get shortcuts
alias kgp='kubectl get pods'
alias kgpa='kubectl get pods -A'
alias kgn='kubectl get nodes'
alias kgs='kubectl get svc'
alias kgd='kubectl get deployment'
alias kgcm='kubectl get configmap'
alias kgsec='kubectl get secret'
alias kgpv='kubectl get pv'
alias kgpvc='kubectl get pvc'

# Describe shortcuts
alias kdp='kubectl describe pod'
alias kdn='kubectl describe node'
alias kds='kubectl describe svc'

# Apply / Delete
alias kaf='kubectl apply -f'
alias kdf='kubectl delete -f'

# Logs
alias kl='kubectl logs'
alias klf='kubectl logs -f'
alias klp='kubectl logs --previous'

# Namespace shortcut — set a default namespace
# Usage: kns kube-system
kns() { kubectl config set-context --current --namespace="$1"; }

# Reload
source ~/.bashrc
```

---

## Vim Config for YAML Editing

The exam uses vim by default. Add this to `~/.vimrc` to make YAML editing bearable:

```vim
set expandtab
set tabstop=2
set shiftwidth=2
set number
set autoindent
set paste
```

```bash
echo "set expandtab
set tabstop=2
set shiftwidth=2
set number
set autoindent" > ~/.vimrc
```

---

## tmux (Optional but Powerful)

If you're comfortable with tmux, use it to split your terminal:
- Left pane: editing manifests
- Right pane: running kubectl commands

```bash
# Split horizontally
Ctrl+b then "

# Split vertically
Ctrl+b then %

# Switch panes
Ctrl+b then arrow key
```

---

> ⚠️ On exam day, you cannot use your local `.bashrc`.
> The exam environment has its own shell. Type the alias and autocomplete lines manually at the start.
> Practice doing this until it takes under 30 seconds.
