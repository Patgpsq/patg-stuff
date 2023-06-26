# patg-stuff

This is a repo that Patrick uses to add documentation and other things to make life easier and automate setup various systems

## Dev Box (Laptop setup) for Mac OS

1. Run `sudo xcode-select --install`
2. Run `sudo /usr/sbin/softwareupdate --install-rosetta --agree-to-license`
3. Run `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
4. Run `brew update`
5. Run `brew install github terraform helm kubectl fzf`
6. Run `echo 'export PATH=$PATH:/opt/homebrew/bin >> ~/.zshrc'` 
7. Run
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
8. Run `echo 'export PATH="${KREW_ROOT:-$HOME/.krew}/bin:$PATH"' >> ~/.zshrc`
9. Run `kubectl krew install ns` 
10. Run 
```
mkdir -p ~/.oh-my-zsh/custom/plugins/kubectl-autocomplete/
kubectl completion zsh > ~/.oh-my-zsh/custom/plugins/kubectl-autocomplete/kubectl-autocomplete.plugin.zsh
```
11. Run
```
curl -LO https://raw.githubusercontent.com/ahmetb/kubectx/master/kubectx
curl -LO https://raw.githubusercontent.com/ahmetb/kubectx/master/kubens

sudo chmod +x ./{kubectx,kubens}
sudo mv ./{kubectx,kubens} /usr/local/bin/

mkdir -p ~/.oh-my-zsh/completions
curl -L https://raw.githubusercontent.com/ahmetb/kubectx/master/completion/kubectx.zsh -o ~/.oh-my-zsh/completions/_kubectx.zsh
curl -L https://raw.githubusercontent.com/ahmetb/kubectx/master/completion/kubens.zsh -o ~/.oh-my-zsh/completions/_kubens.zsh
```
