### 🚀 Automating Process Monitoring & Restarting with Bash Scripting Day4! 🔧

System uptime is critical for any server, especially when running essential services such as **Nginx**. If a process unexpectedly stops, it can lead to downtime or service disruptions. One efficient way to solve this issue is by creating a **Bash script** that monitors the process and restarts it if needed.

In this post, I will walk you through a Bash script that monitors a specified process (e.g., Nginx) and automatically attempts to restart it if it stops running. This is a great way to ensure that your server remains up and running with minimal manual intervention.

---

### **The Bash Script: monitor_process.sh**

Below is the script you can use to monitor and restart a process if it's not running:

```bash
#!/bin/bash

#####################################
#
# Script Author: Jamiu
#
# Date: 01-01-2025
#
# Version: v1
#
# Nginx Monitor
#
#####################################

# Script to monitor a process and restart if not running.
# Usage: ./monitor_process.sh <process_name>

if [ "$#" -ne 1 ]; then
  echo "Usage: $0 <process_name>"
  exit 1
fi

PROCESS_NAME=$1
MAX_ATTEMPTS=3
ATTEMPT=0

while [ $ATTEMPT -lt $MAX_ATTEMPTS ]; do
  # Check if the process is running
  if pgrep -x "$PROCESS_NAME" > /dev/null; then
    echo "Process $PROCESS_NAME is running."
    exit 0
  else
    echo "Process $PROCESS_NAME is not running. Attempting to restart..."

    # Attempt to restart the process
    if command -v systemctl &> /dev/null; then
      sudo systemctl restart $PROCESS_NAME
    elif command -v service &> /dev/null; then
      sudo service $PROCESS_NAME restart
    else
      echo "No suitable command found to manage the service. Please check your init system."
      exit 1
    fi

    sleep 2
  fi

  # Check again if the process is running after restart attempt
  if pgrep -x "$PROCESS_NAME" > /dev/null; then
    echo "Process $PROCESS_NAME restarted successfully."
    exit 0
  fi

  ATTEMPT=$((ATTEMPT + 1))
done

echo "Maximum restart attempts reached. Please check the process manually."
```

---

### **How the Script Works:**

#### **1. Usage Check:**
- The script requires **one argument**: the name of the process you want to monitor (e.g., `nginx`).
- If no argument is provided, the script will show the correct usage and exit:
  
  ```bash
  Usage: $0 <process_name>
  ```

#### **2. Process Monitoring:**
- It uses the `pgrep -x` command to check if the specified process is running. The `-x` option ensures that the process name matches exactly, so you won’t get partial matches (e.g., "nginx-service" will not match "nginx").
  
  If the process is running, it prints a success message and exits the script.

#### **3. Restart Attempts:**
- If the process is not running, the script attempts to restart it. It first checks if `systemctl` or `service` commands are available, then restarts the process using the appropriate command.

  - `systemctl restart $PROCESS_NAME` (if systemd is available)
  - `sudo service $PROCESS_NAME restart` (if a non-systemd system is in use)

#### **4. Retry Logic:**
- If the process does not start after the first attempt, the script will retry up to **3 times**. After each attempt, it waits for **2 seconds** before checking again.

- If the process restarts successfully after any of the attempts, the script will output a success message and exit.
  
- If the script fails after 3 attempts, it will print an error message asking for **manual intervention** to check the process.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hx7zk3gocsi35j1qmswe.png)


#### **5. Automating with Cron Jobs (Optional):**
You can automate this script to run periodically by setting up a **cron job**. This is useful if you want to continuously monitor the process without having to run the script manually each time.

To run the script every **5 minutes**, do the following:

1. Open the crontab file for editing:
   ```bash
   crontab -e
   ```

2. Add this line to run the script every 5 minutes:
   ```bash
   */5 * * * * /path/to/monitor_process.sh nginx
   ```

---

### **Why This Script is Useful:**

- **Ensures Reliability:** This script helps to automatically restart services like **Nginx** if they stop, minimizing downtime and ensuring the service stays up.
- **Efficiency:** By automating the monitoring and restart process, you save time and eliminate the need for manual intervention.
- **Customization:** You can easily modify the script to monitor other services, like Apache, MySQL, or any custom processes. Simply pass the name of the process as an argument when running the script.

Here is the snapshot of the code I pushed to my Github repository.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ho3yg1yk4me8iajaxdv7.png)

Screenshot 1



![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cfaoq1un8cdjwy0f83lh.png)

Screenshot 2


### **Conclusion:**

By using this simple **Bash script**, you can ensure that your **critical services** like **Nginx** are automatically restarted if they stop running. Whether you're managing a single server or multiple servers, automating this process can significantly improve uptime and reduce manual oversight.

Feel free to modify the script for your needs, or automate it with cron jobs for continuous monitoring. If you have any questions or suggestions for improving the script, feel free to leave a comment below!

---

This write up makes the script more understandable and adds explanations of each section, making it easy to follow for readers, even those who may not be familiar with Bash scripting.


Reference
Day 1: https://dev.to/jamiu_cloud/join-me-on-my-7-day-bash-scripting-challenge-4j6j

Day 2: https://dev.to/jamiu_cloud/automating-backups-with-bash-scripting-day-2-3ahm

Day 3: https://dev.to/jamiu_cloud/simplifying-user-account-management-with-bash-scripting-day3-371m


💡 Have you automated your processes? What challenges have you faced? Let’s share insights and grow together!

CloudEngineering #Automation #BashScripting #DataBackup #DevOps #CreateUser #Monitoring #Nginx
