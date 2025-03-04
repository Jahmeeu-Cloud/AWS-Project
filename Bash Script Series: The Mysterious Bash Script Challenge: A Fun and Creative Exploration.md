As a Cloud Engineer, I’ve always been fascinated by the power of automation. One of the tools I rely on heavily is **Bash scripting**. From automating cloud infrastructure management to monitoring system health, Bash scripting is an essential part of my toolkit. But sometimes, it's fun to take a step back and experiment with more creative challenges. Recently, I came across a script that intrigued me – a **mysterious Bash script** designed to transform and obfuscate text. Let's take a deeper look at what this script does, how it works, and how you can run it!


```
#!/bin/bash


#####################################
#
# Script Author: Jamiu
#
# Date: 03-01-2025
#
# Version: v1
#
# Mysterious Bash
#
#####################################



# Welcome to the Mysterious Script Challenge!
# Your task is to unravel the mystery behind this script and understand what it does.
# Once you've deciphered its objective, your mission is to improve the script by adding comments and explanations for clarity.

# DISCLAIMER: This script is purely fictional and does not perform any harmful actions.
# It's designed to challenge your scripting skills and creativity.

# The Mysterious Function

#!/bin/bash

# Welcome to the Mysterious Script Challenge!
# This script performs a series of transformations on a given input file.

# DISCLAIMER: This script is purely fictional and does not perform any harmful actions.

# The Mysterious Function
mysterious_function() {
    local input_file="$1"  # The input file to be processed
    local output_file="$2" # The file where the result will be saved

    # Step 1: Apply ROT13 cipher to the input file and save it to output file
    tr 'A-Za-z' 'N-ZA-Mn-za-m' < "$input_file" > "$output_file"

    # Step 2: Reverse the output file content
    rev "$output_file" > "reversed_temp.txt"

    # Step 3: Generate a random number between 1 and 10
    random_number=$(( ( RANDOM % 10 ) + 1 ))

    # Mystery loop: Reverse and apply ROT13 multiple times
    for (( i=0; i<$random_number; i++ )); do
        # Reverse the content of reversed_temp.txt
        rev "reversed_temp.txt" > "temp_rev.txt"

        # Apply ROT13 again to the reversed content
        tr 'A-Za-z' 'N-ZA-Mn-za-m' < "temp_rev.txt" > "temp_enc.txt"

        # Move the newly encoded file to replace reversed_temp.txt
        mv "temp_enc.txt" "reversed_temp.txt"
    done

    # Clean up temporary files
    rm "temp_rev.txt"
}

# Main Script Execution

# Check if two arguments are provided
if [ $# -ne 2 ]; then
    echo "Usage: $0 <input_file> <output_file>"
    exit 1
fi

input_file="$1"  # First argument: Input file
output_file="$2" # Second argument: Output file

# Check if the input file exists
if [ ! -f "$input_file" ]; then
    echo "Error: Input file not found!"
    exit 1
fi

# Call the mysterious function to begin the process
mysterious_function "$input_file" "$output_file"

# Display the mysterious output
echo "The mysterious process is complete. Check the '$output_file' for the result!"
```
#### What Does the Script Do?

At first glance, this script may seem simple, but it packs a punch with its mysterious transformations. Here’s a breakdown of the steps involved:

1. **ROT13 Cipher**: The script starts by applying a **ROT13** cipher to the text in the input file. ROT13 is a simple encryption method that shifts each letter by 13 positions in the alphabet (for example, 'A' becomes 'N'). This is often used in puzzles or forums to hide spoilers or sensitive information temporarily.

2. **Reverse the Text**: After the initial transformation, the script then **reverses** the content of the file. This adds an additional layer of obfuscation, making it harder to decipher at a glance.

3. **Randomization**: To add a bit of unpredictability, the script generates a random number between 1 and 10, determining how many times it will repeat the process of reversing the text and applying ROT13. This makes each run of the script slightly different, further complicating the result.

4. **Clean-up**: After performing the transformations, the script cleans up any temporary files it created during the process.

The result? A string of text that’s been scrambled multiple times and would require some effort to reverse-engineer.

#### Why is This Interesting?

You might be wondering, why go through all this trouble for something that looks so cryptic? Here are a few reasons why this exercise is worth exploring:

- **Text Transformation Basics**: This script gives a solid introduction to text transformations, using tools like `tr` (for ROT13) and `rev` (for reversing text). Understanding how these tools work is fundamental for automating tasks that involve text processing.

- **Randomization and Loops**: The script demonstrates how to use **randomization** and **loops** to make an operation more dynamic. These techniques are incredibly useful in real-world scripts, like retrying failed operations or applying multiple layers of security to sensitive data.

- **Creative Scripting**: Bash scripting doesn’t always have to be about mundane tasks like managing servers or backups. It can also be about experimenting and having fun while expanding your knowledge.

#### How to Run the Script

The process is simple and straightforward. Here’s how you can run the script on your machine:

1. **Prepare Your Input File**: 
   - Create a text file that you want to transform. For example, you can create a file named `input.txt` with the content you want to encrypt or obfuscate. You can do this using the following command:
     ```bash
     echo "This is a test" > input.txt
     ```

2. **Run the Script**: 
   - Now, execute the script with the following command:
     ```bash
     ./mystery.sh input.txt output.txt
     ```

3. **Check the Output**: 
   - Once the script completes, check the contents of the `output.txt` file:
     ```bash
     cat output.txt
     ```

4. **Reversing the Transformation**: 
   - If you want to "decode" the text back to its original form, you can apply ROT13 again using:
     ```bash
     tr 'A-Za-z' 'N-ZA-Mn-za-m' < output.txt
     ```
     This will give you back the original text.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wy734gur0aibpla7nfi1.png)


#### Why Automate with Bash?

Bash scripting is not just for simple tasks. It’s an invaluable tool for automating a wide variety of processes in the **cloud engineering** and **DevOps** worlds. Whether you're automating cloud deployments, server maintenance, or monitoring processes, Bash is often the go-to scripting language because of its simplicity and power.

By learning how to manipulate text, manage files, and automate tasks with Bash, you’ll be well-equipped to tackle more complex cloud automation challenges. Plus, it’s a great way to build a strong foundation for learning other automation tools like **Ansible**, **Terraform**, and **AWS CloudFormation**.

#### Stay Tuned for More!

I hope this mysterious script has sparked some interest in the world of Bash scripting and automation. It’s a fun way to dive deeper into scripting concepts while solving creative challenges. 




💡 Stay tuned for more updates and similar series coming soon!

Reference Articles:

Day 1: [Join Me on My 7-Day Bash Scripting Challenge](https://dev.to/jamiu_cloud/join-me-on-my-7-day-bash-scripting-challenge-4j6j)


Day 2: [Automating Backups with Bash Scripting](https://dev.to/jamiu_cloud/automating-backups-with-bash-scripting-day-2-3ahm)


Day 3: [Simplifying User Account Management with Bash Scripting](https://dev.to/jamiu_cloud/simplifying-user-account-management-with-bash-scripting-day3-371m)


Day 4: [Automating Process Monitoring and Restarting with Bash Scripting](https://dev.to/jamiu_cloud/automating-process-monitoring-restarting-with-bash-scripting-day4-5e0i)

Day 5: [Automating Log Analysis with Bash Script](https://dev.to/jamiu_cloud/bash-script-series-automating-log-analysis-with-bash-script-or-shell-script-25cn)
