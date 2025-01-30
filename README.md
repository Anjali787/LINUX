# LINUX
# Azure Account Setup  
1. Created a Microsoft Azure account using my university-provided email address.  
2. Learned about cloud computing and its importance.  
3. Activated student benefits and set up a student account, receiving **$100** in Azure credits for use within the platform.  

# Virtual Machine Setup  
1. Created a virtual machine for coursework.  
2. Selected **Ubuntu Server 24.04 LTS Gen 2** from the Marketplace, published by Canonical.  
3. Named the virtual machine **"lab-robotics"**.  
4. Chose the **Standard_B2ls_v2** configuration from the B-series.  
5. Created a new resource group and subnet for organizing and allocating the machine.  

# GitHub Configuration  
1. Created a new repository named **"LINUX"** for the assignment.  
2. Added my HAMK email address as a secondary email to my GitHub account for version control.  
![mail](image.png)




# Assignment 3: User Management and File System Access

## Step 1: Creating Users  
- First, I created two users: **tupu** and **lupu**.  
- Then, I set **passwords** and other necessary details to ensure only they can access their files.  
- I used the `sudo` and `adduser` commands for this:  

        sudo adduser tupu  

## Step 2: Creating the `lupu` User  
- Next, I created the `lupu` user using the `useradd` command:  

        sudo useradd -m -d /home/lupu -s /bin/bash -G lupu lupu  

  Explanation of flags:  
  - `-m`: Creates the user's home directory.  
  - `-d /home/lupu`: Specifies the home directory path.  
  - `-s /bin/bash`: Sets the login shell to Bash.  
  - `-G lupu`: Adds the user to the `lupu` group.  

## Step 3: Creating the `hupu` System User  
- Additionally, I created a system user named `hupu`, with the login shell set to **/bin/false** to prevent login:  

        sudo useradd --system --shell /bin/false hupu  

  Explanation of flags:  
  - `--system`: Creates a system account.  
  - `--shell /bin/false`: Prevents the user from logging in.  

## Step 4: Granting Sudo Privileges  
- I used **visudo** to edit the sudoers file:  

        sudo visudo  

- Then, I added the following lines to grant sudo access to both users:  

        tupu ALL=(ALL:ALL) ALL  
        lupu ALL=(ALL:ALL) ALL  

- There are alternative methods to do this, but I chose this approach while testing both.  


## Step 5:
- I create directory in **/opt/projekti** and add both users

        sudo mkdir /opt/projekti

- Then crete a group called projekti and assign both tupu and lupu into the group and the commands are:

        sudo groupadd projekti
        sudo usermod -aG projekti tupu
        sudo usermod -aG projekti lupu

- And give ownership to projekti group.

        sudo chown :projekti /opt/projekti

- And **set permission** so that tupu and lupu can access the file in all three formate like read, write and execute files.

        sudo chmod 770 /opt/projekti

- The following command ensures that any new files created within the /opt/projekti directory inherit the group ownership of projekti, maintaining the desired permissions.

        sudo chmod g+s /opt/projekti

## Output:

        drwxrws--- 2 root projekti 4096 Jan 30 16:02 /opt/projekti

### Here is the screenshots of the practical.
![alt text](image-3.png)
![alt text](image-4.png)