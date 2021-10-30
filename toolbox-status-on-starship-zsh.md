# Toolbox status on Starship with ZSH

`.zshrc`:

```bash
# uncomment following for oh-my-zsh
# export ZSH="/var/home/mirko/.oh-my-zsh" # your path
# plugins=(git)
# source $ZSH/oh-my-zsh.sh

function setToolboxHeader(){
  tput sc
  tput csr 1 $((`tput lines` - 1))
  tput cup 0 0
  tput el
  printf "\033[0;36m ⬢ Running inside a Toolbox.\e[0m"
  tput rc
}

function clearToolbox(){
  clear
  setToolboxHeader
  echo ""
}

if [[ -f /run/.containerenv && -f /run/.toolboxenv ]]; then
  setToolboxHeader
  alias clear=clearToolbox
fi

eval "$(starship init zsh)"
```
