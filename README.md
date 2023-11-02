# Vagrant Setup

**Step 1:** Run PowerShell as Administrator.

**Step 2:** Check the current execution policy. If it throws an error, proceed to change the execution policy.

```powershell
Get-ExecutionPolicy
```

**Step 3:** If the execution policy isn't "RemoteSigned" or higher, set it to "RemoteSigned" (use "RemoteSigned" or "Unrestricted" based on your security preferences). Answer "Yes" when prompted.

```powershell
Set-ExecutionPolicy RemoteSigned
```

**Step 4:** Install Chocolatey package manager by running the following command in PowerShell:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

**Step 5:** Install Git using Chocolatey:

```powershell
choco install git
```

**Step 6:** Install VirtualBox using Chocolatey:

```powershell
choco install virtualbox -y
```

**Step 7:** Install Vagrant using Chocolatey, specifying the desired version (e.g., 2.3.4):

```powershell
choco install vagrant --version 2.3.4 -y
```

Now that you've installed the necessary tools, you can proceed to set up a virtual machine using Vagrant:

**Step 8:** Open Git Bash, and navigate to the directory where you want to create your Vagrant environment.

**Step 9:** Create a new directory and change to it:

```bash
mkdir directory_name
cd directory_name
```

**Step 10:** Create another directory within the first one:

```bash
mkdir directory_name
cd directory_name
```


**Step 11:** Initialize a new Vagrant environment using the generic/centos7 box from https://app.vagrantup.com/generic/boxes/centos7:

```bash
vagrant init generic/centos7
```

**Step 12:** Start the virtual machine:

```bash
vagrant up
```

**Step 13:** SSH into the virtual machine:

```bash
vagrant ssh
```

If you encounter SSH connection issues, you may need to adjust settings in the Vagrantfile, such as enabling SSH forwarding.

**Step 14:** Within the virtual machine (CentOS 7), you can use the YUM package manager for tasks like updating packages, installing software (e.g., Apache HTTP server), and managing services:

```bash
# Update the package list
sudo yum update

# List available packages
sudo yum list available

# Install Apache HTTP server
sudo yum install httpd

# Check the status of the HTTP service
systemctl status httpd.service

# Start the HTTP service
systemctl start httpd.service

# Enable the HTTP service to start on boot
systemctl enable httpd.service
```

**Step 15:** You can change the index.html file inside the /var/www directory to customize your web server content.

**Step 16:** Find the IP address of the virtual machine:

```bash
# Display the IP addresses of network interfaces
ip a
```

**Step 17:** To test your Apache server, you can use curl or open a web browser and enter the IP address in the URL:

```bash
# Example using curl
curl <ip_address>
```
