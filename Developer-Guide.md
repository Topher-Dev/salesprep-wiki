# Developer's Guide for SalesPrep

Welcome to the SalesPrep Developer's Guide. This document provides essential information to get started with development, contribute effectively to the project, and maintain a high-quality codebase.

## Getting Started
#### Initial Setup Instructions

1. **Get a Fresh Installation of Ubuntu**
   - Ensure you're starting with a clean and updated installation of Ubuntu (latest) to avoid any compatibility issues. If you're setting up a new environment, download the Ubuntu (latest) LTS image from the official [Ubuntu website](https://ubuntu.com/download/desktop) and follow the installation guide.
   - After installation login as root user, update your system to make sure all the default software is up to date. Open a terminal and run:
     ```bash
     apt update && apt upgrade -y
     ```
2. **Create an Admin User**
   - To improve security and avoid using the root account, create a new admin user. This user will have complete access to the app and naming should follow the convention of appname(abbrev)_admin eg "sp_admin":
     ```bash
     adduser sp_admin
     ```
   - Follow the prompts to set a password and provide additional information.
   - Grant administrative privileges, add the new user to the `sudo` group:
     ```bash
     usermod -aG sudo sp_admin
     ```
   - You can now log out of the root account and log in with your new admin user.

3. **Install Git**
   - Git is essential for version control and collaborating on the FightView project. Install Git by opening your terminal and entering:
     ```bash
     sudo apt install git -y
     ```
   - Verify the installation by checking the Git version:
     ```bash
     git --version
     ```
     This command should return the installed version of Git, confirming it's correctly installed on your system.


4. **Set Up SSH Keys**
   - To securely connect to remote server hosting the app code, you’ll need to generate SSH keys (if they don't already exist). Open your terminal and run:
     ```bash
     ssh-keygen -t ed25519 -C "your_email@example.com"
     ```
     - Press Enter to accept the default file location, or specify a different one if desired.
     - When prompted, enter a passphrase for added security, or leave it blank for no passphrase.
   - After generating your keys, you can add the public key to the authorized keys of the remote server. First, display your public key with:
     ```bash
     cat ~/.ssh/id_ed25519.pub
     ```
     - Copy the output and paste it to the remote server. Ensure the permissions are correct. In the case of github utilize their online GUI portal to upload.

5. **Test the SSH Connection**
   - Once your keys are set up, you can test the SSH connection without entering the remote terminal by executing:
     ```bash
     ssh -T git@github.com
     ```

6. **Clone the FightView Repository**
   - clone the repo
     ```bash
     git clone git@github.com:Topher-Dev/salesprep.git
     ```

After cloning the FightView repository, the next step is to set up your development environment by running the installation script included in the repository. This script will install all necessary dependencies, configure your environment, and prepare the application for use.

#### Running the Installation Script


1. **Execute the Install Script**
   - navigate into the repo and run the install script with the  `full` argument to start the installation and configuration process.
     ```bash
     cd salesprep;
     sudo sbin/install.sh full
     ```
     - Respond to prompts for necessary configuration details:
       - app_runmode dev|prod (choice)
       - jwt_secret Application Private Key: Used for JSON Web Tokens (JWT). ( Input Validated for length)
       - database_password: For PostgreSQL database access. (Input Validated for complexity)

2. **Execute the system script**
   - Run `sbin/system.sh`, this will validate that all core technologies / servers are running and expected
     ```bash
     sudo sbin/system.sh
     ```

#### Branches

1. **master**
   - Production branch, only updated by merging from a develop branch


2. **develop**
   - Contains updates / upgrades




