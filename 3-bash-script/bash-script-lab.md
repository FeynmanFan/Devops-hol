# 3. Bash script lab

The new T-800 model will be pulling a list of users authorized to give it admin commands. The list will be 
in an encrypted zip file - luckily the script to decrypt the file is already complete, and you will be working on 
the plaintext zip file that contains the file, *users.txt*. The problem is that the existing user parsing code uses
a single quote ' as a delimiter. Some names have a single quote, such as "Tim O'Reilly", and this name will break the parser.

Cyberdyne will update the parser eventually, but for now, if there is a name containing a single quote like O'Reilly, we want the script to execute the following steps:

<pre>
echo "Exception: Pattern ' found on line: $line"
exit 1
</pre>

Where $line is the line of the file that the single quote was found on.

## Lab Steps

1. Create a bash script with the following lines at the top:

<pre>#!/bin/bash

sudo apt-get install -y unzip
sudo apt-get install -y grep

unzip -o users.zip</pre>

This will insure that the unzip and grep packages that you will need to work with the zip file and the regular expression are installed.
The third line will unzip the file, overwriting any files already there so that you can run your script many times without having to delete the users.txt file.

2. Open the file, *users.txt* in script. If the file is not present for some reason, execute the following lines of code:
<pre>echo "Error: File 'users.txt' not found."

exit 1</pre>

3. Create a while loop that will loop through the lines in the file. You will probably need to search the Internet to learn how to do this.

4. Create an if statement to test the value of the line against the regex. The value of the regex is this:

<pre>'</pre>

Just a single quote.

5. If that value is found, execute the failure lines of code we specified above: 

<pre>
echo "Exception: Pattern ' found on line: $line"
exit 1
</pre>

6. When the file works correctly, it should output a warning about Bertram O'Grady. Save the file and commit it to your repo.

7. Paste the url of your forked repo into the **DevOps Hands-on Lab** Discord channel for review, making sure to mention which lab you have completed.

### Use the users.zip file found in this folder

###Hint###
Break the script into separate problems and solve them one at a time. The unzipping of the file, for example, is entirely separate from the problem of reading the lines from the file, and reading the lines from the file is entirely separate from the problem of examining a single line of text for the pattern.
