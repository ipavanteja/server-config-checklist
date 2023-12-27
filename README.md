# <p align="center"> Server Configuration Checklist </p>

<table align="center">
	<tr><th align="center"> S.No</th><th align="center">Server Configuration Checklist</th></tr>
	<tr><td align="center"> 1</td><td align="center">Connect to AWS Instance</td></tr>
	<tr><td align="center"> 2</td><td align="center">CPU & Operating System Info </td></tr>
	<tr><td align="center"> 3</td><td align="center">Install Speedtest tool and check Internet Speed in AWS Server</td></tr>
	<tr><td align="center"> 4</td><td align="center">Visual Studio Code (Remote-SSH) Plugin</td></tr>
	<tr><td align="center"> 5</td><td align="center">Set Root Password </td></tr>
	<tr><td align="center"> 6</td><td align="center">System Update & Upgrade (apt update && apt upgrade) - as root </td></tr>
	<tr><td align="center"> 7</td align="center"><td>Install Updated Node JS (LTS Version) & Install Updated NPM (LTS Version)</td></tr>
	<tr><td align="center"> 8</td ><td align="center">GCC Installation (LTS Version)</td></tr>
	<tr><td align="center"> 9</td><td align="center">Python 3 Installation</td></tr>
	<tr><td align="center"> 10</td><td align="center">Git Account Config in Linux</td></tr>
	<tr><td align="center"> 11</td><td align="center">Network Adapter Info (Static IP, Local IP and MAC Address) </td></tr>
	<tr><td align="center"> 12</td><td align="center">GitHub SSH Key Setup</td></tr>
	<tr><td align="center"> 13</td><td align="center">GitHub GPG Keys Setup </td></tr>
	<tr><td align="center"> 14</td><td align="center">Login as root in AWS Server - Ubuntu Linux </td></tr>
	<tr><td align="center"> 15</td><td align="center">Install Certbot and Generate SSL Certificate</td></tr>
	<tr><td align="center"> 15</td><td align="center">PM2 (Process Manager 2)</td></tr>
</table>


### 1. How to Connect to AWS Instance 

- Make sure you have the server's private key file: cs22-yourname.txt.
  
  - Copy the file to the path mentioned below.
                   
  - For Windows: `C:\Users\[user-name]\.ssh\`
    
  - For Mac/Ubuntu: `~/.ssh/`
    
  - If the `.ssh` folder does not exist, create and add a copy of the key file.
       
- Open the Terminal in Windows/mac, and use the commands given below to change file permissions and login with SSH protocol:

  - To change file permissions: `chmod 600 [file=name]`
    
  - To log in using SSH: `ssh -i [path-for-the-keyfile] user@server-ip`

### 2 CPU & Operating System Info

- `uname`: This command provides basic information about the operating system.

  - `uname -a`

- `lsb_release`: This command provides distribution-specific information about the operating system.

  - `lsb_release -a`

- `cat /etc/os-release`: This command displays information about the operating system from the `/etc/os-release` file.

  - `cat /etc/os-release`

- `cat /proc/cpuinfo`: This command displays detailed information about the CPU.

  - `cat /proc/cpuinfo`

- `lscpu`: This command provides a more structured and human-readable output for CPU information.

  - `lscpu`

- `free`: This command displays information about system memory usage.

  - `free -h`

-  `df`: This command shows disk space usage of file systems.
  
    - `df -lh`
 
- To Check the folder size in Linux 

    - `du -sh`

    - `du -lh`

- `htop`: Similar to top, this command provides an interactive view of system processes and resource usage.

  - `htop`

- `inxi`: This is a versatile command-line system information script that provides comprehensive details about your system. 

  - `sudo apt-get install inxi`   # Install `inxi` if not already installed

  - `inxi -F`

- **(Desktop Management Interface Decoder)**  `dmidecode`: This command provides detailed information about hardware components, including CPU, BIOS, memory, etc.

  - `sudo dmidecode`

### 3. Install Speedtest tool as root and check Internet Speed in AWS Server

- **Install speed test tool:** 

   - `sudo apt install speedtest-cli`

- **Check the internet speed:** 

   - `speedtest`

### 4. Visual Studio Code (Remote-SSH) Plugin 

- **Open Visual Studio Code:** If you don't have VS Code installed, you can download it from the official website: [Visual Studio Code](https://code.visualstudio.com/) 

- **Open Extensions:** Click on the Extensions icon in the sidebar or use the shortcut Ctrl+Shift+X (Windows/Linux) or Cmd+Shift+X (Mac) to open the Extensions view.

- **Search for the Extension:** In the Extensions view, search for "`Remote - SSH`" using the search bar.

- **Install the Extension:** Find the "`Remote - SSH`" extension in the search results and click the "`Install`" button next to it.

- **Wait for Installation:** After clicking "`Install`" the extension will be downloaded and installed. You'll see a progress indicator during the installation.

- **Reload VS Code:** Once the installation is complete, you might be prompted to reload Visual Studio Code to enable the extension. If not, you can manually reload VS Code using the "`Reload`" button in the Extensions view or by restarting VS Code.

- **Connect to a Remote Server:** With the extension installed and VS Code reloaded, you can now connect to a remote server via SSH:

  - Click on the "`Remote Explorer`" icon in the sidebar (it looks like a computer monitor with an arrow).

  - In the Remote Explorer, click on the green "`Connect to Host`" button (it looks like a "+") at the top.

  - Choose "Add SSH Host..." to configure a new SSH connection.

  - Enter the remote SSH address in the format: `ssh -i \[path-for-the-keyfile] user@server-ip`  You can also specify a custom port if needed.

  - Choose the authentication method (password or private key).

  - Once connected, you'll see your remote server listed in the Remote Explorer. You can click on it to explore and edit files on the remote server using VS Code.

### 5. Set Root Password 

- **Connect to the Server:** Use SSH to connect to your server as a user with administrative privileges. For example:

  - `ssh username@server_ip`

- **Set Root Password:** Use the `sudo passwd` command to set the root password:

  - `sudo passwd`

  - You'll be prompted to enter the new root password twice.

- **Exit Root Shell:** After setting the password, you can exit the root shell by typing exit and pressing Enter.

### 6. System Update & Upgrade (apt update && apt upgrade) - as root 

- **Open a Terminal:** Log in to your server via SSH or directly access the terminal if you have physical access.

- **Switch to Root User:** Start by switching to the root user using the `su` command or `sudo -i`:

  - `sudo -i`

- **Update Package Lists:** Update the package lists from the repositories. This command downloads the latest information about available packages and their versions:

  - `apt update`

- **Upgrade Packages:** After updating the package lists, you can proceed to upgrade the installed packages to their latest versions:

  - `apt upgrade`

  - You might be prompted to confirm the upgrade and the additional disk space required. Review the changes and type `Y` if you're comfortable proceeding.

- **Clean Unneeded Packages (Optional):** After the upgrade, you can clean up unneeded packages and free up disk space:

  - `apt autoremove`

### 7. Install Updated Node JS (LTS Version) and Updated NPM (LTS Version) 

- **Open a Terminal:** Log in to your system via SSH or access the terminal directly if you have physical access.

- **Install Node.js:** Use the following command to install Node.js and its associated package manager,  `npm`:

  - `sudo apt install nodejs npm`

- **Check Installation:** Verify that Node.js and npm have been installed correctly by checking their versions:

  - `node -v`

  - `npm -v`

- The command `sudo npm i n -g` is used to globally install the `n` package, which is a Node.js version manager. This package allows you to easily switch between different versions of Node.js on your system. Here's what each part of the command does:

- **`sudo npm i n -g`**

  - **`npm`:** This is the Node Package Manager, a command-line tool used to install and manage Node.js packages and dependencies.

  - **`i`** (or **`install`**): This is a command used with npm to install packages.

  - **`n`**: This is the name of the package you're installing. In this case, it refers to the `n` package, which is a Node.js version manager.

  - **`-g`**: This flag indicates that the package should be installed globally on your system, making it available from the command line for all users.

- **`n latest`** or **`n stable`**: The commands `n` latest or n stable are used with the `n` package (Node.js version manager) to install and use the latest or stable version of Node.js, respectively.

  - `sudo n latest`

  - `sudo n stable`
  
### 8. GCC Installation (LTS Version)

- **Open a Terminal:** Log in to your system via SSH or access the terminal directly if you have physical access.

- **Update Package Lists:** Before installing any software, it's a good idea to update your package lists to ensure you're getting the latest information:

  - `sudo apt update`

- **Install GCC:** Use the following command to install the GCC package:

  - `sudo apt install gcc`

- **Check Installation:** After installation, you can check the installed version of GCC using the following command:

  - `gcc --version`

### 9. Python 3 Installation 

- **Open a Terminal:** Log in to your system via SSH or access the terminal directly if you have physical access.

- **Update Package Lists:** Before installing any software, it's a good idea to update your package lists to ensure you're getting the latest information:

  - `sudo apt update`

- **Install Python 3:** Use the following command to install Python 3:

  - `sudo apt install python3`

- **Check Installation:** After Installation, you can check the installed version of python3 using the following command:

  - `python3 --version`

### 10. Git Account Config in Linux 

- **Open a Terminal:** Log in to your system via SSH or access the terminal directly if you have physical access.

- **Check Existing Configuration:** Before setting up your Git account, you can check your existing Git configuration by running:

  - `git config --list`

- **Set Your Name:** Use the following command to set your Git username:

  - `git config --global user.name "Your Name"`

  - Replace "`Your Name`" with your actual name.

- **Set Your Email:** Use the following command to set your Git email address:

  - `git config --global user.email "your@example.com"`

  - Replace "`your@example.com`" with your actual email address.

- **Check Configuration:** After setting your name and email, you can verify your Git configuration by running:

  - `git config --global --get user.name`

  - `git config --global --get user.email`

### 11. Network Adapter Info (Static IP, Local IP and MAC Address)

- **Local IP Address:** You can use the ip command or the ifconfig command (legacy) to get information about your network interfaces. The following examples show how to retrieve the local IP address:

  - **Using `ip` command**:

    - `ip addr show`

  - **Using `ifconfig` command:**

    - `ifconfig`

- **MAC Address:** You can use the  `ip command` or the `ifconfig` command (legacy) to obtain the MAC address:

  - **Using `ip` command:**

  - `ip link show`

  - The MAC address is typically labeled as "`ether`" in the output.

- **Note on `ip` and `ifconfig`:** The ifconfig command is being phased out in favor of the  `ip` command. It's recommended to use the `ip` command for modern Linux systems, as it provides more detailed and up-to-date information.

### 12. GitHub SSH Key Setup for AWS Server

- **Generate SSH Key Pair:** Open a terminal on your local machine and generate a new SSH key pair if you don't have one already. Replace `your_email@example.com` with your email address:

  - `ssh-keygen -t ed25519 -C "your_email@example.com"`

  - Press Enter to accept the default file location and set a passphrase when prompted. The passphrase adds an extra layer of security to your key.

- For more details refer official documentation link: [SSH-Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)

- **Copy Public Key:** Copy your SSH public key to the clipboard. Use the following command to display your public key:

  - `cat ~/.ssh/id_ed25519.pub`

  - Copy the entire output.

- **Add SSH Key to GitHub:**

  - Log in to your GitHub account.

  - Click on your profile picture in the top right and choose "Settings."

  - In the left sidebar, click "SSH and GPG keys."

  - Click the "New SSH key" button.
  
  - Give your key a title (e.g., "My Laptop") and paste the public key you copied earlier into the "Key" field.

  - Click the "Add SSH key" button.

### 13. GitHub GPG Keys Setup for AWS Server

- **Generate GPG Key Pair:** Open a terminal on your local machine and generate a new GPG key pair. 

  - `gpg --full-generate-key`

  - Follow the prompts to select key type, key size, expiration, and create a passphrase for the key.
  
  -  For more details refer official documentation link: [GPG-Key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key#generating-a-gpg-key)

- **List Your GPG Keys:** Use the following command to list your GPG keys and their IDs:

  - `gpg --list-secret-keys --keyid-format long`
 
   ```
    	$ gpg --list-secret-keys --keyid-format=long
	/Users/hubot/.gnupg/secring.gpg
	------------------------------------
	sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
	uid                          Hubot <hubot@example.com>
	ssb   4096R/4BB6D45482678BE3 2016-03-10
    ```

  - Look for the key ID (long format) associated with the key you just generated (usually starts with "sec" and is followed by a long alphanumeric string).

- **Export GPG Public Key:** Export your GPG public key to a file. Replace `YOUR_KEY_ID` with the actual key ID you obtained in the previous step:

- From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is `3AA5C34371567BD2`:

  - `gpg --armor --export YOUR_KEY_ID > gpg_public_key.asc`
    
  - This command exports the public key to a file named  `gpg_public_key.asc`.

- **Add GPG Key to GitHub:**

  - Log in to your GitHub account.

  - Click on your profile picture in the top right and choose "Settings."

  - In the left sidebar, click "SSH and GPG keys."

  - Scroll down to the "GPG keys" section and click the "New GPG key" button.

  - Open the `gpg_public_key.asc` file you generated earlier and copy the entire content.

  - Paste the content into the "Key" field.

  - Click the "Add GPG key" button.

- **Configure Git to Use GPG Key:** Tell Git to use your GPG key for signing commits:

  - **List Your GPG Keys:** Use the following command to list your GPG keys and their IDs:

  - `gpg --list-secret-keys --keyid-format long`
 
   ```
    	$ gpg --list-secret-keys --keyid-format=long
	/Users/hubot/.gnupg/secring.gpg
	------------------------------------
	sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
	uid                          Hubot <hubot@example.com>
	ssb   4096R/4BB6D45482678BE3 2016-03-10
    ```

  - Look for the key ID (long format) associated with the key you just generated (usually starts with "sec" and is followed by a long alphanumeric string).

- **GPG signing key**: To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is `3AA5C34371567BD2`:

  - Replace `YOUR_KEY_ID' with your new GPG from the list.
    
  - `git config --global user.signingkey YOUR_KEY_ID`
 
  - `git config --global user.signingkey 3AA5C34371567BD2`

- **Set Global Git Commit Signing:** Configure Git to sign all your commits by default:

  - `git config --global commit.gpgsign true`

- **Test GPG Signature:** Make a test commit to a repository, and you'll be prompted for your GPG key passphrase when committing. Verify that your commits are now signed.

  - Remember that GPG keys are used for secure cryptographic operations. Keep your private key secure and do not share it with anyone. Back up your keys in a safe location. If you need to revoke your key for any reason, you can also do so through the GitHub settings.

  - GPG-signed commits enhance the security and trust of your contributions on GitHub by ensuring their authenticity and integrity.

### 14. Login as root in AWS Server - Ubuntu Linux

- **Connect to the Instance:**

  - Use SSH to connect to your instance as the default user (e.g., "ubuntu") using your private key:

  - `ssh -i /path/to/private/key.pem ubuntu@your-instance-ip`

- **Edit the Authorized Keys File:**

  - Edit the authorized_keys file for the "root" user. The file is typically located in the `/root/.ssh/` directory. You can use a text editor like nano:

  - `sudo nano /root/.ssh/authorized_keys`

**Remove the Restriction:**

  - Locate the specific line in the authorized_keys file that corresponds to the key you're using for SSH access. The line will contain the `no-port-forwarding... 10;exit 142"` restriction. Remove that part from the line, so it looks something like this:

    - **Before:**

      - `no-port-forwarding,no-agent-forwarding,no-X11-forwarding,command="echo 'Please login as the user \"ubuntu\" rather than the user \"root\".';echo;sleep 10;exit 142" ssh-rsa AAA...your-public-key... user@example.com`

    - **After:**

      - `ssh-rsa AAA...your-public-key... user@example.com`

- **Save and Exit:**

  - After removing the `'no-port-forwarding...... upto exit 142'` restriction, save the file and exit the text editor.

- **Restart SSH Service:**

  - If you've made changes to the authorized_keys file for the "root" user, you should restart the SSH service for the changes to take effect

  - Check the status of SSH by using the below command:
    
	- `sudo service ssh status`
  
  - To Restart the SSH service:

 	- `sudo service ssh restart`

### 15. Install Certbot and Generete SSL Certificate

- **Certbot Installation:**

   - [Click here](https://certbot.eff.org/instructions?ws=other&os=ubuntufocal) and follow the instructions from Step-1 to Step-5 to install `certbot` in your AWS server.

      - **(Note: select the server as other and select the operating system as Ubuntu 20)**

- **`sudo certbot certonly --manual --preferred-challenges=dns`:** This command is used when user want to generate a certificate for a domain and have control over the DNS records for that domain. Here's a breakdown of the command:

    - **`sudo`**: This command is usually used to run a command as a superuser or with elevated privileges. It's used to ensure that you have the necessary permissions to perform the actions that follow.

    - **`certbot`**: Certbot is a tool for managing SSL certificate, primarily used with Let's Encrypt, a free and automated certificate authority.

    - **`certonly`**: This subcommand of Certbot is used to obtain a certificate without installing it. It's useful when you want to manually handle certificate installation.

    - **`--manual`**: This flag indicates that you want to use manual mode for certificate issuance. In manual mode, Certbot will guide you through the process of creating DNS TXT records that prove your control over the domain.

    - **`--preferred-challenges=dns`**: This option specifies that you prefer DNS challenges for certificate validation. With DNS challenges, you'll be required to add DNS TXT records to your domain's DNS configuration to prove ownership.

- Once we execute the above command, enter the domain name and if domains are more than one add it space separated.  

- After adding the domain it will generate the DNS TXT record and value then copy the DNS TXT generated before the domain and add it in new record as HOST as TXT record in the Domain registrar

- Again the copy the value that generated along with DNS TXT and add it as a value in new record
  
- Keep it to minimum time then save it and Press enter.

    - **(Note: After you updating the TXT record make sure you wait up to 5 min and press enter)**

- After some time user will successfully receives the certificate with absolute paths.

### 16. PM2 (Process Manager 2)

 **Overview:**
  
  PM2 (Process Manager 2) is a popular production process manager for Node.js applications. It simplifies the deployment and management of Node.js applications 
  in a production environment. PM2 provides features such as process monitoring, automatic restarts, log management, and more.

  - **Installation**

    - `npm install -g pm2`
  - **Running Applications**

    - `pm2 start <app.js or script> [--name <process_name>]`

       `<app.js or script>`: Specify the main script or application file.
      
       `--name <process_name>` (Optional): Assign a custom name to the process for easy identification.

   - **To run your Node.js application with PM2, you can add a script to your package.json file.**

     For example:
     ```
     "scripts": {
  	    "start": "pm2 start <app.js or script> --name <process_name>"
     }
     ```
   - **Common PM2 Commands**

     - **List Processes:**
       - `pm2 list`
     - **Show Detailed Process Info:**
       - `pm2 show <process_name>`
     - **Display Logs:**
       - `pm2 logs <process_name>`
     - **Restart Process:**
       - `pm2 restart <process_name>`
     - **Stop Process:**
       - `pm2 stop <process_name>`
     - **Delete Process:**
       - pm2 `delete <process_name>`
      
