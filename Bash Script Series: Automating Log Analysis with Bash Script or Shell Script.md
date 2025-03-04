### **Automating Log Analysis with Bash: A Simple Way to Manage System Logs**

If you've ever managed servers, you know how messy log files can get. Every day, these files record important events and errors, which are crucial for keeping your systems running smoothly. But let’s face it: going through logs manually is boring, time-consuming, and easy to mess up.

To make life easier, I created a **Bash script** that automates log analysis. Think of it as your assistant that sifts through the logs, picks out the important stuff, and hands you a clear, easy-to-read summary.

---

### **Why Did I Build This Script?**
Imagine you have a pile of logs that tell you things like:
- Errors when a disk is full.
- Services that failed to start.
- Critical problems like network failures.

Wouldn’t it be great if you could quickly get a summary instead of reading line by line? That’s exactly what my script does!

---

### **What Does the Script Do?**
Here’s how it works:
1. **Counts Errors**: It finds all the error messages in the log and gives you the total count.
2. **Finds Critical Issues**: It hunts down "CRITICAL" problems and tells you exactly where to find them in the log.
3. **Lists Top Errors**: It identifies the most common errors so you can prioritize fixing them.
4. **Generates a Report**: It creates a neat summary report with all this information for you to review.
5. **Moves Processed Logs**: After analyzing a log file, it moves it to a folder for safekeeping.

---

```
#!/bin/bash


#####################################
#
# Script Author: Jamiu
#
# Date: 02-01-2025
#
# Version: v1
#
# Automate Log Analysis
#
#####################################


# Check if the log file path is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 <log_file_path>"
    exit 1
fi

LOG_FILE=$1

# Check if the log file exists
if [ ! -f "$LOG_FILE" ]; then
    echo "Error: Log file '$LOG_FILE' does not exist."
    exit 1
fi

# Variables
REPORT_FILE="log_summary_report_$(date +%F).txt"
ERROR_KEYWORDS=("ERROR" "Failed")
CRITICAL_KEYWORD="CRITICAL"

echo "Analyzing log file: $LOG_FILE"

# Total lines processed
TOTAL_LINES=$(wc -l < "$LOG_FILE")

# Count errors
ERROR_COUNT=0
for keyword in "${ERROR_KEYWORDS[@]}"; do
    ERROR_COUNT=$((ERROR_COUNT + $(grep -c "$keyword" "$LOG_FILE")))
done

# Identify critical events
CRITICAL_EVENTS=$(grep -n "$CRITICAL_KEYWORD" "$LOG_FILE")

# Extract top 5 error messages
ERROR_MESSAGES=$(grep -E "${ERROR_KEYWORDS[*]}" "$LOG_FILE" | awk '{for(i=2;i<=NF;i++) printf $i " "; print ""}' | sort | uniq -c | sort -nr | head -n 5)

# Generate summary report
echo "Generating summary report: $REPORT_FILE"
echo "Log Analysis Report - $(date)" > "$REPORT_FILE"
echo "Log File: $LOG_FILE" >> "$REPORT_FILE"
echo "Total Lines Processed: $TOTAL_LINES" >> "$REPORT_FILE"
echo "Total Error Count: $ERROR_COUNT" >> "$REPORT_FILE"
echo -e "\nTop 5 Error Messages:" >> "$REPORT_FILE"
echo "$ERROR_MESSAGES" >> "$REPORT_FILE"
echo -e "\nCritical Events (Line Numbers):" >> "$REPORT_FILE"
if [ -z "$CRITICAL_EVENTS" ]; then
    echo "None" >> "$REPORT_FILE"
else
    echo "$CRITICAL_EVENTS" >> "$REPORT_FILE"
fi

# Optional: Archive or move the processed log file
ARCHIVE_DIR="processed_logs"
mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR/"
echo "Log file moved to $ARCHIVE_DIR/"

echo "Log analysis complete. Report saved to $REPORT_FILE."
exit 0

```


### **How to Use It**
1. Place your log file (e.g., `sample_log.log`) in the same folder as the script.
2. Run the script with:
   ```bash
   ./log_analyzer.sh sample_log.log
   ```
3. Check out the generated report:
   ```bash
   cat log_summary_report_<date>.txt
   ```
4. The original log file will be safely moved to a folder called `processed_logs`.

---

### **Sample Output**
Here’s what the report looks like:

```
Log Analysis Report - Thu Jan 2 2025
Log File: sample_log.log
Total Lines Processed: 4
Total Error Count: 3

Top 5 Error Messages:
1. ERROR: Disk full - 1 time
2. ERROR: Failed to start service - 1 time

Critical Events:
3: CRITICAL: Network down
```

It’s simple, clear, and gives you everything you need at a glance.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rt6lwz0it61ma7gxdf52.png)


---

### **Why This is Useful**
- **Saves Time**: No more wasting hours skimming through logs.
- **Organized**: All logs are stored neatly in a folder after processing.
- **Quick Insights**: You immediately know what went wrong and where to look.

---

### **What’s Next?**
I’m planning to improve this script by:
- Sending email alerts for critical issues.
- Allowing it to analyze multiple log files at once.
- Integrating it with real-time monitoring tools.

---

I plan to enhance the script with features like email notifications for critical issues and support for analyzing multiple log files simultaneously.

This has been a fun project to showcase the power of Bash scripting for automation and server management. If you’re managing logs, I’d love to hear your feedback or ideas for improvement.

### **Final Thoughts**
This script is a game-changer for anyone who manages servers or deals with logs regularly. It’s simple, effective, and can save you tons of time. If you’d like to try it out or have ideas for improvement, let me know in the comments!


💡 Stay tuned for more updates and similar series coming soon!

Reference
Day 1: https://dev.to/jamiu_cloud/join-me-on-my-7-day-bash-scripting-challenge-4j6j

Day 2: https://dev.to/jamiu_cloud/automating-backups-with-bash-scripting-day-2-3ahm

Day 3: https://dev.to/jamiu_cloud/simplifying-user-account-management-with-bash-scripting-day3-371m

Day 4:
https://dev.to/jamiu_cloud/automating-process-monitoring-restarting-with-bash-scripting-day4-5e0i
