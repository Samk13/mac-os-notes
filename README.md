# MacOS Notes

## Keyboard Shortcuts
On a nordic keyboard layout, change "Move focus to next window" shortcut:

- Open System Settings ( → System Settings).
- Go to Keyboard → Keyboard Shortcuts….
- In the sidebar, pick Keyboard.
- Look for “Move focus to next window” (that's the one triggered by `⌘ + ``).
- Select it, then press your new shortcut: ⌘ + §.
- It should update immediately.

## zshrc Configuration

# Add the following lines to your ~/.zshrc file

```zsh
# https://spaceship-prompt.sh/
# https://www.nerdfonts.com/font-downloads#:~:text=JetBrains%20officially%20created%20font%20for%20developers
source /opt/homebrew/opt/spaceship/spaceship.zsh
# https://github.com/zsh-users/zsh-syntax-highlighting
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
# https://github.com/zsh-users/zsh-autosuggestions
source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh
# https://github.com/junegunn/fzf
source <(fzf --zsh)
# export FZF_ALT_C_OPTS="--walker-skip Library,node_modules,target,.git,.pyenv,.nvm,.Trash,.local,.oh-my-zsh,*/.*,Applications"
# Bind fzf-cd-widget to Command+C (assuming terminal sends \e[c for Command+C)
export FZF_ALT_C_COMMAND='fd --type d . ~/Documents' # Add extra folders that you want to be visible here
export FZF_ALT_C_OPTS='--preview "ls -la {}"'
bindkey 'ç' fzf-cd-widget

# uv 
. "$HOME/.local/bin/env"

# https://github.com/nvm-sh/nvm
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# Azure CLI autocompletion
autoload bashcompinit && bashcompinit
source $(brew --prefix)/etc/bash_completion.d/az
source <(kubectl completion zsh)

# Aliases
alias vim=nvim
alias vi=nvim
alias celerykill="pkill -f 'celery worker'"
alias celeryls="ps aux|grep \"celery worker\""
alias update="brew update && brew upgrade && brew cleanup && brew doctor"
alias k=kubectl
alias kx="kubectl exec -it"
alias kgp="kubectl get pods"
```

# Config

in ~/.config/ghostty/config
```ini
# theme = Sea Shells
theme = Catppuccin Mocha
# needed for vim keybindings
macos-option-as-alt = true
# keep vim works on right alt only to not affect | ~ ...
macos-option-as-alt = right

keybind = performable:ctrl+v=paste_from_clipboard
keybind = performable:ctrl+c=copy_to_clipboard
keybind = performable:ctrl+w=close_window
keybind = ctrl+alt+c=text:\x1bc
working-directory = "~"
font-family = "JetBrainsMonoNL Nerd Font Mono"
font-size = 15

window-height = 25
window-width = 278

window-padding-y = 20
window-padding-x = 20
window-position-x = 5
window-position-y = 830
````
