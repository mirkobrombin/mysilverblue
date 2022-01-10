# Toolbox status on Starship with ZSH
I use [Starship shell](https://starship.rs) with `zsh` and `oh-my-zsh` plugins. I also use a toolbox (toolbx) for development purposes. The default shell is Bash and this is configured to automatically show a purple `⬢` when inside a toolbox. The following do the trick when using `zsh+starship` but also other shells:

```bash
eval "$(starship init zsh)"

if [[ -f /run/.containerenv && -f /run/.toolboxenv ]]; then
  PURPLE='\033[0;35m'
  NC='\033[0m'
  PS1='%1d '$(printf "${PURPLE}⬢ $NC")
else
  unset PS1
  eval "$(starship init zsh)"
fi
```

Full `.zshrc`:

```bash
export ZSH="$HOME/.oh-my-zsh"
plugins=(git)
source $ZSH/oh-my-zsh.sh

if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi

eval "$(starship init zsh)"

if [[ -f /run/.containerenv && -f /run/.toolboxenv ]]; then
  PURPLE='\033[0;35m'
  NC='\033[0m'
  PS1='%1d '$(printf "${PURPLE}⬢ $NC")
else
  unset PS1
  eval "$(starship init zsh)"
fi

```
