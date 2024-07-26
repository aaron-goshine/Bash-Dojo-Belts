# Bash-Dojo-Belts
The official belt grading for bash, to determine your belt 
———

Certainly! Here are daily practice exercises for each belt level, combining all the mentioned concepts into one fluid task.

### White Belt (Beginner)
#### Exercise: File Management and Navigation
1. Open your terminal.
2. Create a directory called `WhiteBelt` and navigate into it.
    ```bash
    mkdir WhiteBelt
    cd WhiteBelt
    ```
3. Create three empty files named `file1.txt`, `file2.txt`, and `file3.txt`.
    ```bash
    touch file1.txt file2.txt file3.txt
    ```
4. List all files in the directory.
    ```bash
    ls
    ```
5. View the contents of `file1.txt` (it will be empty).
    ```bash
    cat file1.txt
    ```
6. Move `file1.txt` to a new directory called `Archive`.
    ```bash
    mkdir Archive
    mv file1.txt Archive/
    ```
7. Copy `file2.txt` to the `Archive` directory.
    ```bash
    cp file2.txt Archive/
    ```
8. Delete `file3.txt`.
    ```bash
    rm file3.txt
    ```
9. List the contents of the `Archive` directory to confirm the files are there.
    ```bash
    ls Archive/
    ```
10. Go back to the parent directory and remove the `WhiteBelt` directory and its contents.
    ```bash
    cd ..
    rm -r WhiteBelt
    ```

### Yellow Belt (Intermediate)
#### Exercise: Text Processing and Basic Scripting
1. Create a directory called `YellowBelt` and navigate into it.
    ```bash
    mkdir YellowBelt
    cd YellowBelt
    ```
2. Create a file named `text.txt` with the following content:
    ```
    Hello world
    Bash scripting is fun
    Learning new skills
    ```
    ```bash
    echo -e "Hello world\nBash scripting is fun\nLearning new skills" > text.txt
    ```
3. Search for the word "Bash" in `text.txt`.
    ```bash
    grep "Bash" text.txt
    ```
4. Count the number of lines in `text.txt`.
    ```bash
    wc -l text.txt
    ```
5. Sort the lines in `text.txt` alphabetically.
    ```bash
    sort text.txt
    ```
6. Create a simple script `process_text.sh` that performs the following:
    - Displays the content of `text.txt`.
    - Counts the number of lines.
    - Sorts the lines alphabetically and saves the result in `sorted_text.txt`.

    ```bash
    echo -e "#!/bin/bash\n\ncat text.txt\nwc -l text.txt\nsort text.txt > sorted_text.txt" > process_text.sh
    chmod +x process_text.sh
    ```
7. Run the script.
    ```bash
    ./process_text.sh
    ```

### Green Belt (Proficient)
#### Exercise: Advanced Text Processing and Functions
1. Create a directory called `GreenBelt` and navigate into it.
    ```bash
    mkdir GreenBelt
    cd GreenBelt
    ```
2. Create a file named `data.txt` with the following content:
    ```
    1,John,Doe
    2,Jane,Smith
    3,Alice,Jones
    4,Bob,Brown
    ```
    ```bash
    echo -e "1,John,Doe\n2,Jane,Smith\n3,Alice,Jones\n4,Bob,Brown" > data.txt
    ```
3. Use `awk` to print only the second and third fields (first and last names) from `data.txt`.
    ```bash
    awk -F',' '{print $2, $3}' data.txt
    ```
4. Use `sed` to replace all commas with tabs in `data.txt`.
    ```bash
    sed 's/,/\t/g' data.txt
    ```
5. Write a script `process_data.sh` that:
    - Prints the first and last names using `awk`.
    - Replaces commas with tabs using `sed` and saves the result to `tabbed_data.txt`.
    - Defines a function `count_lines` that counts and prints the number of lines in `data.txt`.

    ```bash
    echo -e "#!/bin/bash\n\nawk -F',' '{print \$2, \$3}' data.txt\nsed 's/,/\t/g' data.txt > tabbed_data.txt\n\ncount_lines() {\n  wc -l data.txt\n}\n\ncount_lines" > process_data.sh
    chmod +x process_data.sh
    ```
6. Run the script.
    ```bash
    ./process_data.sh
    ```

### Blue Belt (Advanced)
#### Exercise: Automation and Error Handling
1. Create a directory called `BlueBelt` and navigate into it.
    ```bash
    mkdir BlueBelt
    cd BlueBelt
    ```
2. Create a script `backup.sh` that:
    - Creates a backup of a specified directory.
    - The backup should be saved with a timestamp in its name.
    - Checks if the backup was successful and prints a message accordingly.
    - Schedules the script to run daily at midnight using `cron`.

    ```bash
    echo -e "#!/bin/bash\n\nSOURCE_DIR=\$1\nBACKUP_DIR=\"backup_\$(date +%Y%m%d%H%M%S)\"\n\nif [ -d \"\$SOURCE_DIR\" ]; then\n  cp -r \$SOURCE_DIR \$BACKUP_DIR\n  if [ \$? -eq 0 ]; then\n    echo \"Backup successful: \$BACKUP_DIR\"\n  else\n    echo \"Backup failed\"\n  fi\nelse\n  echo \"Source directory does not exist\"\nfi" > backup.sh
    chmod +x backup.sh
    ```

3. Schedule the script to run daily at midnight using `cron`.
    ```bash
    crontab -e
    # Add the following line to the crontab file:
    0 0 * * * /path/to/BlueBelt/backup.sh /path/to/source_directory
    ```

### Black Belt (Expert)
#### Exercise: Complex Scripting and Project Integration
1. Create a directory called `BlackBelt` and navigate into it.
    ```bash
    mkdir BlackBelt
    cd BlackBelt
    ```
2. Write a complex script `project.sh` that:
    - Accepts multiple arguments (file paths) and performs operations on them.
    - Checks if each file exists and prints an appropriate message.
    - Counts the total number of lines across all files.
    - Archives the files into a tarball.
    - Uses `git` to commit the tarball to a repository.

    ```bash
    echo -e "#!/bin/bash\n\nFILES=\$@\nTOTAL_LINES=0\n\nfor FILE in \$FILES; do\n  if [ -f \"\$FILE\" ]; then\n    echo \"Processing \$FILE\"\n    LINES=\$(wc -l < \"\$FILE\")\n    TOTAL_LINES=\$((TOTAL_LINES + LINES))\n  else\n    echo \"File \$FILE does not exist\"\n  fi\ndone\n\necho \"Total lines: \$TOTAL_LINES\"\n\nTARBALL=\"archive_\$(date +%Y%m%d%H%M%S).tar.gz\"\ntar -czf \$TARBALL \$FILES\n\ngit add \$TARBALL\ngit commit -m \"Added archive \$TARBALL\"\n" > project.sh
    chmod +x project.sh
    ```

3. Run the script with multiple file paths as arguments.
    ```bash
    ./project.sh file1.txt file2.txt file3.txt
    ```

These exercises are designed to be practiced daily to help students strengthen their command line and shell scripting skills progressively.
