. This guide covers essential steps for a smooth setup of Fedora, including system updates, essential software, and development tools for various languages.


---

# Fedora KDE Post-Installation Guide for Software Development

This documentation provides a step-by-step guide on setting up Fedora KDE for software development, aimed at optimizing your system, installing essential tools, and configuring a developer-friendly environment.

# 1. System Update and Upgrades

After a fresh Fedora installation, updating your system ensures that you have the latest security patches, software versions, and drivers.

Steps:

1. Open the Terminal (press Alt + Space and type "konsole" for the terminal).


2. Run the following commands to update the system:

```bash
sudo dnf upgrade --refresh
```bash
3. Reboot if the kernel or other core components were updated:

sudo reboot



 # 2. Enabling Repositories

Fedora includes multiple software repositories. However, for development, you may need access to non-free and third-party repositories.

Steps:

Enable RPM Fusion for additional software:

sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

Enable Flathub (optional, for Flatpak applications):

flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo


# 3. Installing Essential Development Tools

Fedora provides a variety of development tools across different languages and environments. Here’s a list of popular packages to install based on your needs.

Steps:

Install the Development Tools and Libraries groups:

sudo dnf groupinstall "Development Tools" "C Development Tools and Libraries"

Install general build tools (GCC, Make, etc.) and utilities:

sudo dnf install gcc g++ make cmake automake


# 4. Setting Up Programming Languages and Frameworks

Here is a setup for popular languages. You can install whichever suits your development needs:

# 4.1 Python Development

1. Install Python and essential packages:

sudo dnf install python3 python3-pip python3-virtualenv


2. Common packages (e.g., for data science, web dev):

pip install numpy pandas flask django jupyterlab


3. IDE and Editor: You can install PyCharm (available from Flathub) or VS Code (covered below).



# 4.2 Java Development

1. Install OpenJDK:

sudo dnf install java-17-openjdk-devel


2. Install Maven (if required):

sudo dnf install maven


3. IDE: Install IntelliJ IDEA from Flathub or VS Code.



# 4.3 JavaScript / Node.js Development

1. Install Node.js and npm:

sudo dnf install nodejs npm


2. Install common packages:

npm install -g typescript eslint yarn


3. IDE: Visual Studio Code is recommended (see installation below).



# 4.4 C/C++ Development

1. Install GCC and libraries:

sudo dnf install gcc gcc-c++ gdb


2. Install CMake (if needed for project builds):

sudo dnf install cmake


3. IDE: KDE's KDevelop is a solid choice, or use CLion from JetBrains.



# 4.5 Ruby Development

1. Install Ruby:

sudo dnf install ruby


2. Rails and other packages:

gem install rails bundler



# 4.6 Other Languages and Tools

For Go, Rust, and other languages, Fedora's repository includes up-to-date packages:

Rust: sudo dnf install rust cargo

Go: sudo dnf install golang

PHP: sudo dnf install php php-cli php-mbstring


# 5. Installing Essential Development Software

# 5.1 Visual Studio Code
 
Visual Studio Code is one of the most popular code editors, with support for extensions for virtually any language.

1. Add VS Code repository:

sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'


2. Install VS Code:

sudo dnf install code



# 5.2 Git and Version Control

Git is essential for source control management.

1. Install Git:

sudo dnf install git


2. Configure Git with your user details:

git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"


3. Optional: Install GitKraken or SmartGit for a GUI-based Git client (available on Flathub).



# 5.3 Docker

Docker is widely used for containerization, which is beneficial for development and deployment.

1. Install Docker:

sudo dnf install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io


2. Start and Enable Docker:

sudo systemctl start docker
sudo systemctl enable docker


3. Add your user to the docker group:

sudo usermod -aG docker $USER


4. Log out and back in to apply group changes.



# 5.4 Database Tools

Install databases as per your project requirements:

PostgreSQL: sudo dnf install postgresql-server postgresql-contrib

MySQL/MariaDB: sudo dnf install mariadb-server


To enable the database, start the service:

sudo systemctl enable --now postgresql

# 6. Development Environment Customization

KDE Customization

1. Change Theme:

Go to System Settings > Appearance > Global Theme to explore and apply themes.



2. Set Up Shortcuts:

Go to System Settings > Shortcuts to customize key bindings for your productivity.




# Terminal Customization

1. Install Zsh and Oh-My-Zsh for an enhanced terminal experience:

sudo dnf install zsh
chsh -s $(which zsh)

Log out and back in to switch to Zsh.

Install Oh-My-Zsh with custom themes and plugins:

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"



2. Install Tilix (optional terminal emulator with tiling features):

sudo dnf install tilix




---

# 7. Final Tips and Resources

KDE Discover: Use Discover, KDE’s software center, for installing and managing applications easily.

Additional Packages: For any additional packages, use the command sudo dnf search <package-name>.


With this setup, your Fedora KDE environment should be ready for a range of development tasks. Happy coding!

