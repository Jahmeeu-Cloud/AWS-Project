### Automating User Account Management with Bash Scripting  

Managing user accounts efficiently is a critical task for system administrators and cloud engineers. Whether you’re working on a standalone server or managing a fleet of cloud-based instances, automating user account management can save time, reduce errors, and enhance system security.  

In this post, I’m sharing a Bash script I recently developed to simplify and automate user account management tasks on Linux systems.  

### **Here is the Bash Script code:** 

```
#!/bin/bash

# User Account Management Script
# This script provides options for managing user accounts on the system.

########################################
#
#
# Script Author: Jamiu
#
# Date: 31-12-2024
#
# Version: v1
#
#
########################################


# Function to display usage information
usage() {
    echo "Usage: $0 [OPTION]"
    echo "Options:"
    echo "  -c, --create      Create a new user account"
    echo "  -d, --delete      Delete an existing user account"
    echo "  -r, --reset       Reset the password of an existing user account"
    echo "  -l, --list        List all user accounts"
    echo "  -h, --help        Display this help message"
}

# Function to create a new user account
create_user() {
    read -p "Enter the new username: " username
    if id "$username" &>/dev/null; then
        echo "Error: The username '$username' already exists."
        exit 1
    fi
    read -s -p "Enter the password for the new user: " password
    echo
    sudo useradd -m "$username"
    echo "$username:$password" | sudo chpasswd
    echo "User '$username' created successfully."
}

# Function to delete a user account
delete_user() {
    read -p "Enter the username to delete: " username
    if ! id "$username" &>/dev/null; then
        echo "Error: The username '$username' does not exist."
        exit 1
    fi
    sudo userdel -r "$username"
    echo "User '$username' deleted successfully."
}

# Function to reset a user account password
reset_password() {
    read -p "Enter the username to reset the password for: " username
    if ! id "$username" &>/dev/null; then
        echo "Error: The username '$username' does not exist."
        exit 1
    fi
    read -s -p "Enter the new password: " password
    echo
    echo "$username:$password" | sudo chpasswd
    echo "Password for user '$username' updated successfully."
}

# Function to list all user accounts
list_users() {
    echo "Listing all user accounts:"
    awk -F: '{print "Username: " $1 ", UID: " $3}' /etc/passwd
}

# Main script logic
if [ $# -eq 0 ]; then
    usage
    exit 1
fi

case "$1" in
    -c|--create)
        create_user
        ;;
    -d|--delete)
        delete_user
        ;;
    -r|--reset)
        reset_password
        ;;
    -l|--list)
        list_users
        ;;
    -h|--help)
        usage
        ;;
    *)
        echo "Invalid option: $1"
        usage
        exit 1
        ;;
esac


```



### **Features of the Script**  

#### 1. **Create Accounts**  
The script allows administrators to quickly add new user accounts. It ensures that usernames are unique, prompts for secure password creation, and provides a success confirmation after the account is created.  


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y2ijwkgotfv3a5f8s14n.png)



#### 2. **Delete Accounts**  
Removing unnecessary user accounts is made effortless with this feature. The script verifies the existence of the account before deletion and safely removes the user, along with associated files.  


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vlbi1mcgedaw9kszsa27.png)




#### 3. **Reset Passwords**  
Resetting a user’s password is as simple as entering a username and the new password. The script ensures that only valid accounts are updated, maintaining system integrity.  

Check the above picture.


#### 4. **List User Accounts**  
This feature lists all existing system accounts along with their UIDs, offering administrators a quick overview of the system’s users.  


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kxzet9nt3hovygytf9jc.png)


#### 5. **Help Menu**  
An intuitive help menu guides users through the script’s functionality, making it accessible even for those with limited Bash scripting experience.  



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nkkwo41l5648l2cocwsh.png)



### **Code Walkthrough**  

Here’s a high-level overview of the script:  
- **Input Validation**: The script checks user input to ensure commands are used correctly.  
- **Error Handling**: It gracefully handles errors like missing or duplicate usernames.  
- **Built-in Variables**: Leveraging system variables ensures accurate and dynamic outputs.  
- **Case Statement**: A clean and modular design using a `case` statement makes the script easy to maintain and extend.  




### **Why Automate User Account Management?**  
Manual user account management is prone to errors and inefficiencies. This script:  
- Saves time by automating repetitive tasks.  
- Reduces security risks by enforcing proper account handling practices.  
- Enhances productivity by streamlining administrative workflows.  

Here is the snapshot of the code I pushed to my Github repository:



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bw1gp2piyjh7vd6si694.png)

Screenshot 1



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ftt3v0b04724v9wydjjz.png)


Screenshot 2



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2xm4snorct62bmx0t1vd.png)

Screenshot 3


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ghhhqp55t7qy0ey4jc3f.png)

Screenshot 4






### **Conclusion**  
This script is a practical example of how Bash scripting can empower administrators to handle system-level tasks with ease and precision. Whether you’re managing a personal server or part of a larger IT team, automating processes like user account management can significantly boost efficiency and security.  

I’d love to hear your thoughts or feedback on this project! Feel free to try the script and share how it works for you. Stay tuned for more automation tips and tricks in future posts.  


Reference 
Day 1: https://dev.to/jamiu_cloud/join-me-on-my-7-day-bash-scripting-challenge-4j6j

Day 2: https://dev.to/jamiu_cloud/automating-backups-with-bash-scripting-day-2-3ahm


💡 Have you automated your processes? What challenges have you faced? Let’s share insights and grow together!


#CloudEngineering #Automation #BashScripting #DataBackup #DevOps #CreateUser
