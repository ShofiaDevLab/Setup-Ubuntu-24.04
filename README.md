# Setup My Ubuntu 24.04 Desktop

This guide provides essential steps to take immediately after installing Ubuntu. Follow the commands provided below to optimize and secure your system.

## 1. Update System

Ensure your system is up-to-date by updating the package lists and upgrading installed packages. Run the following commands:

```bash
sudo apt update && sudo apt upgrade -y
```

## 2. Configure Terminal with Zsh, Oh My Zsh, Powerlevel10k, and Plugins

Enhance your terminal experience by setting up Zsh with the following tools. Run these commands:

1. Install Git, Curl and Zsh:

   ```bash
   sudo apt install git curl zsh
   ```

2. Set Zsh as the default shell:

   ```bash
   chsh -s $(which zsh)
   ```

3. Install Oh My Zsh:

   ```bash
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

4. Install Powerlevel10k theme:

   ```bash
   git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
   sed -i 's/ZSH_THEME=".*"/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc
   source ~/.zshrc
   ```

5. Install useful plugins for Zsh:

   - Zsh Syntax Highlighting:

     ```bash
     git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
     echo "plugins+=(zsh-syntax-highlighting)" >> ~/.zshrc
     source ~/.zshrc
     ```

   - Zsh Autosuggestions:

     ```bash
     git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
     echo "plugins+=(zsh-autosuggestions)" >> ~/.zshrc
     source ~/.zshrc
     ```

   - Zsh Fast Syntax Highlighting:

     ```bash
     git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
     echo "plugins+=(fast-syntax-highlighting)" >> ~/.zshrc
     source ~/.zshrc
     ```

## 3. Install Ruby Using rbenv

Follow these steps to install Ruby using rbenv, as outlined in the [DigitalOcean guide](https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-ubuntu-20-04):

1. Install dependencies:

   ```bash
   sudo apt update
   sudo apt install -y build-essential libssl-dev libreadline-dev zlib1g-dev git
   ```

2. Install rbenv and ruby-build:

   ```bash
   git clone https://github.com/rbenv/rbenv.git ~/.rbenv
   echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
   echo 'eval "$(rbenv init - bash)"' >> ~/.zshrc
   source ~/.zshrc

   git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
   echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.zshrc
   source ~/.zshrc
   ```

3. Install Ruby:

   ```bash
   rbenv install 3.2.2 # Replace with the desired version
   rbenv global 3.2.2
   ```

4. Verify the installation:

   ```bash
   ruby -v
   ```

## 4. Install colorls Using gem

Enhance directory listings with colorls by installing it via gem:

1. Install colorls:

   ```bash
   gem install colorls
   ```

2. Add an alias to use colorls instead of ls:

   ```bash
   echo 'alias ls="colorls"' >> ~/.zshrc
   source ~/.zshrc
   ```

## 5. Configure System Settings

1. **Power Settings**:

   - Disable autosuspend to prevent unexpected suspensions.
     ```bash
     gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'
     ```

2. **Accounts**:

   - Add Google and Microsoft accounts through **Settings > Online Accounts**.

3. **Keyboard Shortcuts**:

   - Customize keyboard shortcuts via **Settings > Keyboard > Shortcuts** to enhance productivity.

4. **System Locale**:

   - Set the system locale to Indonesian:
     ```bash
     sudo localectl set-locale LANG=id_ID.UTF-8
     ```

## 6. Install NVM (Node Version Manager)

Install and manage multiple Node.js versions with NVM. Follow the instructions on the [NVM GitHub repository](https://github.com/nvm-sh/nvm).

## 7. Install Web Server (Nginx, MariaDB, PHP)

Set up a web server using Nginx, MariaDB, and PHP by following the steps outlined in this [YouTube tutorial](https://www.youtube.com/watch?v=cYrRby_trBk).

## 8. Install Composer

Install Composer to manage PHP dependencies by following the steps in the [official Composer installation guide](https://getcomposer.org/doc/00-intro.md).

## 9. Install Python

Set up Python 3 and create a programming environment by following the steps in this [DigitalOcean tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-an-ubuntu-20-04-server).

## 10. Setup Java

Install and configure Java on your Ubuntu system. Follow the instructions provided in the [DigitalOcean guide to installing Java](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04).