
# Gentleman.Dots

## Description

This repository contains customized configurations for a complete development environment, including Neovim, Fish, Zsh, Tmux, Zellij, and terminal emulators like Alacritty, WezTerm, and Kitty. You can choose between automatic and manual installation methods, depending on your preference and operating system. **Important:** Windows users must follow the manual installation instructions before running the script.

## Installation Steps

### Step 1: Clone the Repository

Before proceeding with the configuration transfers, clone this repository and navigate into the cloned directory:

```bash
git clone https://github.com/Gentleman-Programming/Gentleman.Dots.git
cd Gentleman.Dots
```

All subsequent commands assume you are in the `Gentleman.Dots` directory.

**Important:** You must install the Iosevka Term Nerd Font for proper terminal display:

[Download Iosevka Term Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/IosevkaTerm.zip)

---


## Automatic Installation (Recommended)

### IF you feel lucky... Test the new automated process!!! Just execute `install-linux-mac.sh`, and it will do EVERYTHING for you 😘

This script will handle all the heavy lifting, but remember that you **must install the font** mentioned above before running it. The script is designed for macOS, Linux, and WSL systems. If you’re on Windows, you’ll need to follow the manual steps first before attempting to run this script.

```bash
curl -O https://raw.githubusercontent.com/Gentleman-Programming/Gentleman.Dots/main/install-linux-mac.sh

sudo chmod +x install-linux-mac.sh
bash ./install-linux-mac.sh
```

---


## Manual Installation


### For Windows

**Important:** Windows users must follow these manual installation steps before running the automated script.


#### 1. Install WSL

WSL (Windows Subsystem for Linux) allows you to run Linux on Windows. Install it and set it to version 2:


```bash
wsl --install
wsl --set-default-version 2

```


#### 2. Install a Linux Distribution

Install a Linux distribution (e.g., Ubuntu) in WSL:


```bash
wsl --install -d Ubuntu

```

To list available distributions:

```bash
wsl --list --online
```


Install your preferred distribution:

```bash

wsl --install -d <distribution-name>
```


#### 3. Launch and Configure the Distribution

Open the installed distribution to complete setup. Update it with:


```bash
sudo apt-get update

sudo apt-get upgrade
```


#### 4. Install a Terminal Emulator


Choose and install one of the following terminal emulators:


- **Alacritty**: [Download from GitHub Releases](https://github.com/alacritty/alacritty/releases) and place `alacritty.exe` in your `PATH`.
- **WezTerm**: [Download and Install](https://wezfurlong.org/wezterm/installation.html).
- **Kitty**: [Download and Install](https://sw.kovidgoyal.net/kitty/#get-the-app).

#### 5. Configuration Transfer for Terminal Emulators


**Alacritty Configuration**

```powershell
mkdir %userprofile%\AppData\Roaming\alacritty
cp alacritty.toml %userprofile%\AppData\Roaming\alacritty\alacritty.toml

# Uncomment in alacritty.toml

[shell]
program = "wsl.exe"
args = ["--cd","~"]
```

**WezTerm Configuration**

```powershell
cp .wezterm.lua %userprofile%

# Uncomment for Windows settings

# config.default_domain = 'WSL:Ubuntu'

# config.front_end = "WebGpu"
# config.max_fps = 120

```

**Kitty Configuration**

```powershell
cp -r GentlemanKitty/* %userprofile%\.config\kitty
```


---

### For macOS/Linux/WSL


#### Step 1: Install a Terminal Emulator

Choose and install one of the following terminal emulators:

- **Alacritty**


  ```bash

  brew install --cask alacritty
  ```

- **WezTerm**

  [Download and Install](https://wezfurlong.org/wezterm/installation.html).


- **Kitty**

  ```bash
  brew install --cask kitty
  ```

#### Step 2: Configuration Transfer for Terminal Emulators


**Alacritty Configuration**


```bash
cp alacritty.toml ~/.config/alacritty/alacritty.toml
```


**WezTerm Configuration**


```bash
cp .wezterm.lua ~/.config/wezterm/wezterm.lua
```

**Kitty Configuration**


```bash
cp -r GentlemanKitty/* ~/.config/kitty
```


---


### Shared Steps (for macOS, Linux, or WSL)

#### Step 3: Shell Configuration (Fish and Zsh)


Depending on your preference, you can configure either `fish` or `zsh` as your default shell.


##### Fish Configuration


1. **Install Homebrew (if not installed)**


   Install Homebrew by running:


   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

   ```


2. **Install Fish**


   ```bash

   brew install fish
   ```


3. **Set Fish as the Default Shell**

   ```bash
   sudo sh -c "echo $(which fish) >> /etc/shells"
   sudo chsh -s $(which fish)

   ```


4. **Install Fisher**

   ```bash
   curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
   ```

5. **Install PJ Plugin**

   ```bash
   fisher install PatrickF1/fzf.fish
   fisher install oh-my-fish/plugin-pj
   ```

6. **Copy Fish Configuration**


   ```bash
   cp -r GentlemanFish/* ~/.config
   ```


7. **Set Project Paths**

   Modify `PROJECT_PATHS` in `~/.config/fish/config.fish`:


   ```fish
   set PROJECT_PATHS /your/work/path/
   ```

##### Zsh Configuration

1. **Install Homebrew (if not installed)**

   Install Homebrew by running:

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

   ```

2. **Install Zsh**


   ```bash

   brew install zsh
   ```

3. **Install Oh My Zsh**


   ```bash
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

4. **Install Required Plugins**

   ```bash
   brew install zsh-autosuggestions zsh-syntax-highlighting zsh-autocomplete
   ```

5. **Copy Zsh Configuration**


   ```bash

   cp .zshrc ~/
   ```


6. **Set Project Paths**

   Modify `PROJECT_PATHS` in `~/.zshrc`:


   ```bash

   export PROJECT_PATHS="/your/work/path/"
   ```


7. **Set Zsh as the Default Shell**


   ```bash
   sudo sh -c "echo $(which zsh) >> /etc/shells"

   sudo chsh -s $(which zsh)
   ```

8. **Apply Zsh Configuration**


   ```bash
   source ~/.zshrc
   ```


#### Step 4: Additional Configurations


##### Dependencies Install


1. **Install build-essentials for LINUX** (for Linux and WSL)

   ```bash
   sudo apt-get update
   sudo apt-get upgrade
   sudo apt-get install build-essential

   ```


2. **Install Starship**

   ```bash
   brew install starship
   ```


3. **Install NVIM**

   ```bash
   brew install nvim

   ```

4. **Install the following dependencies**

   ```bash
   brew install node npm git gcc fzf fd ripgrep coreutils bat curl lazygit
   ```

5. **Install Iosevka Term Nerd Font**

   [Download and install the Iosevka Term Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/IosevkaTerm.zip)


##### Neovim Configuration


```bash
cp -r GentlemanNvim/nvim ~/.config
```

Restart Neovim to apply the changes.

##### Tmux Configuration

1. **Install Tmux**

   ```bash
   brew install tmux
   ```

2. **Install TPM (Tmux Plugin Manager)**


   ```bash
   git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
   ```


3. **Copy Tmux Configuration**

   ```bash
   cp -r GentlemanTmux/.tmux ~/

   cp GentlemanTmux/.tmux.conf ~/
   ```


4. **Start Tmux and Load Configuration**


   ```bash
   tmux

   tmux source-file ~/.tmux.conf
   ```


5. **Install Tmux Plugins**


   Inside a Tmux session, press `Ctrl + a and then I` (capital I) to install the plugins.

6. **Start Tmux by Default**


For Fish, go to `~/.config/fish/config.fish`:

```bash

# Uncomment Tmux Code
exec tmux


# Comment Z


ellij Code
# exec zellij
```


For Zsh, go to `~/.zshrc`:


```bash
# Uncomment Tmux Code
if [[ $- == *i* ]] && [[ -z "$TMUX" ]]; then
  exec tmux
fi


# Comment Zellij Code
# exec zellij
```

##### Zellij Configuration


1. **Install Zellij**


   ```bash
   brew install zellij
   ```

2. **Copy Zellij Configuration**


   ```bash
   cp -r GentlemanZellij/zellij ~/.config
   ```


3. **Choose the Default Shell**

Go to `~/.config/zellij/config.kdl`:


```bash
# Uncomment the shell you want to use
default_shell "fish"
# default_shell "zsh"
```


4. **Start Zellij by Default**

For Fish, go to `~/.config/fish/config.fish`:

```bash

# Comment Tmux Code
# exec tmux


# Uncomment Zellij Code
exec zellij

```


For Zsh, go to `~/.zshrc`:

```bash
# Comment Tmux Code
# exec tmux


# Uncomment Zellij Code

if [[ $- == *i* ]] && [[ -z "$ZELLIJ" ]]; then

  exec zellij
fi
```

##### Starship Configuration

```bash

cp starship.toml ~/.config
```


### Note on Terminal Emulators

You can choose between Kitty, WezTerm, or Alacritty as your terminal emulator. This repository provides configurations for all three, but it is recommended to use Alacritty.
