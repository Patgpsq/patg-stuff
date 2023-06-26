# patg-stuff

This is a repo that Patrick uses to add documentation and other things to make life easier and automate setup various systems

## Dev Box (Laptop setup) for Mac OS

1. Install xcode.
`sudo xcode-select --install`
2. Install Rosetta2
`sudo /usr/sbin/softwareupdate --install-rosetta --agree-to-license`
3. Install Homebrew
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
4. `brew update`
5. Install various packages you need for DevOps work `brew install github terraform helm kubectl fzf`
6. Set homebrew path `echo 'export PATH=$PATH:/opt/homebrew/bin >> ~/.zshrc'` and `. ~/.zshrc`
7. Install kubectl krew plugin manager
```
(
  set -x; cd "$(mktemp -d)" &&
  OS="$(uname | tr '[:upper:]' '[:lower:]')" &&
  ARCH="$(uname -m | sed -e 's/x86_64/amd64/' -e 's/\(arm\)\(64\)\?.*/\1\2/' -e 's/aarch64$/arm64/')" &&
  KREW="krew-${OS}_${ARCH}" &&
  curl -fsSLO "https://github.com/kubernetes-sigs/krew/releases/latest/download/${KREW}.tar.gz" &&
  tar zxvf "${KREW}.tar.gz" &&
  ./"${KREW}" install krew
)
```
8. Add krew path to Zsh rc file `echo 'export PATH="${KREW_ROOT:-$HOME/.krew}/bin:$PATH"' >> ~/.zshrc` and `. ~/.zshrc`
9. Install kubectl ns plugin Run `kubectl krew install ns` 
10. Set up kubectl command completion 
```
mkdir -p ~/.oh-my-zsh/custom/plugins/kubectl-autocomplete/
kubectl completion zsh > ~/.oh-my-zsh/custom/plugins/kubectl-autocomplete/kubectl-autocomplete.plugin.zsh
```
11. Setup kubectl ns command completion 
```
curl -LO https://raw.githubusercontent.com/ahmetb/kubectx/master/kubectx
curl -LO https://raw.githubusercontent.com/ahmetb/kubectx/master/kubens

sudo chmod +x ./{kubectx,kubens}
sudo mv ./{kubectx,kubens} /usr/local/bin/

mkdir -p ~/.oh-my-zsh/completions
curl -L https://raw.githubusercontent.com/ahmetb/kubectx/master/completion/kubectx.zsh -o ~/.oh-my-zsh/completions/_kubectx.zsh
curl -L https://raw.githubusercontent.com/ahmetb/kubectx/master/completion/kubens.zsh -o ~/.oh-my-zsh/completions/_kubens.zsh
```

## Further setup

Please also see [Michael's setup](https://github.com/michaeljoy/osx-setup/tree/master)
