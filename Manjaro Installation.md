# Manjaro Installation (VM)
## Shell Commands
```bash
sudo pacman -Syu

# --- These steps only for VMWare workstation
# look at installing mqtt explorer
sudo pacman -R thunderbird onlyoffice-desktopeditors
sudo pacman -S open-vm-tools
sudo pacman -Su xf86-input-vmmouse xf86-video-vmware mesa gtk2 gtkmm
sudo echo needs_root_rights=yes >>/etc/X11/Xwrapper.config
sudo systemctl enable vmtoolsd
sudo systemctl start vmtoolsd
sudo systemctl restart vmtoolsd
# ---

sudo pacman -S go jq vim 
sudo ln -s /var/lib/snapd/snap /snap
sudo snap install google-cloud-sdk --classic

# visual studio code
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/visual-studio-code-bin.git
cd visual-studio-code-bin
makepkg -si

# golang installation
sudo pacman -S go
go install gotests gomodifytags impl goplay dlv staticcheck gopls
# in vscode, add go plugin

# docker config
sudo pacman -S docker docker-compose
sudo systemctl start docker.service
sudo systemctl enable docker.service
sudo usermod -aG docker $USER
# in vscode, add Docker plugin

# k8s config
sudo snap install microk8s --classic
sudo usermod -a -G microk8s $USER
mkdir ~/.kube
sudo chown -f -R $USER ~/.kube
sudo microk8s config > ~/.kube/config
echo 'source <(kubectl completion zsh)' >> ~/.zshrc
echo 'alias k=kubectl' >> ~/.zshrc
echo 'alias helm="microk8s helm3"' >> ~/.zshrc
sudo microk8s enable dns ha-cluster ingress metallb registry storage openfaas helm3
# in vscode, add Kubernetes plugin

# configure vue
sudo pacman -S nvm
echo 'source /usr/share/nvm/init-nvm.sh' >> ~/.zshrc
source ~/.zshrc
nvm install --lts
mkdir ~/vue
cd ~/vue
npx degit web2033/vite-vue3-tailwind-starter first-app
cd ~/vue/first-app
npm i
# in vscode, add Vue Language Features (Volar)

# c/c++ dev
sudo pacman -S cmake
# https://github.com/friendlyanon/cmake-init
pip install cmake-init
# in vscode, add the c/c++ tool suite

# github
sudo pacman -S github-cli
gh auth login
# use Github.com
# select HTTPS
# select 'Yes' for 'Authenticate Git with your GitHub credentials?'
# select User personal access token
# create a PAT in GitHub
# authorize the PAT
# copy it into cli

# fix powerline 10k bug
sudo vim /usr/share/zsh/p10k.zsh
# then find this lines of code in the file:
`# If local branch name or tag is at most 32 characters long, show it in full. # Otherwise show the first 12 … the last 12. # Tip: To always show local branch name in full without truncation, delete the next line. (( $#where > 32 )) && where[13,-13]="…" res+="${clean}${where//\%/%%}"  # escape %`
# next is you add a little space at the end of the `res` variable.
`res+="${clean}${where//\%/%%} "  # escape %`

reboot 
```

## Shortcuts Replacement
Navigate: System Settings > Shortcuts > Kwin
1. Disable second window:
	1. In search bar: ctrl+f2
	2. uncheck the box 
2. Change shortcut for Maximize Window
	1. Search for Maximize Window
	2. Unlick "Meta+PgUp"
	3. Click button "Add custom shortcut"
	4. Hit keys "Meta+Up"
3. Click "Apply" button

## VM-Specific Settings
1. Disable screen locking:
	1.  System Settings > Workspace Behavior > Screen Lock
	2.  Uncheck both "Lock screen automatically" checkboxes

## Upgrade VSCode
1. navigate to the vscode pkg git repo dir
2. makepkg -sif