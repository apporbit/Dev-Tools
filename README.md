# Dev-Tools

# Git Commit Implementation Code

## Author: Keerthi Krishnan 

### User Instructions:

#### Purpose:

The primary purpose of the pre-commit script is to analyze code that is being attempting to be committed and notify the committer of the errors that are in the script. This script only applies for shellscript, python, and golang files. 

#### Objective:

Ultimately, the goal of this implementation is to reduce reviewing time on github and reduce developer time, which will, in turn, save money for the parties involved. 

#### File Types:
 
This script will only work for the following files attempting to be committed:

	**shellscript** - .sh
	**python** - .py
	**golang** - .go

#### User Interaction:

When user commits the following files to git, the respective debugger will go through the script and print out the errors found with the appropriate line numbers and error message. If there are errors found, then the code will not commit until the developer corrects those errors and the debugger does not find them. The developer can also override this process using the command **--no-verify**.  

The pre-commit script will also go through the developer script and if the debuggers involved in the pre-commit script are not downloaded on the user's machine, an error message will be printed, telling the user that the required debugger(s) is to be downloaded and will fail the commit. The user must download the required debugger(s) in order to continue the process of committing the code. There is a script that has been created in order to automatically download the necessary debuggers called "install.sh". For more information, refer to Requirements Section of Documentation. 

#### About the Debuggers:

The ShellCheck debugger will show the error ID of the error and will list out the error(s) that the developers script has. 

The Pylint debugger will present errors in the beginning and lists out the lines and errors that the developer code contains. After listing out the errors, the pylint debugger provides reports and statistics of your code. The reports consists of tables of the statistics of your script and at the end, the rating of the script is given according to pylint.

The GoImports debugger goes through the developers code and corrects any syntax errors present in the script. Then, it is immediately committed to the repository. 

After the debuggers go through the developer scripts and there seems to be no errors outputted from the debuggers, the developer scripts will be committed to the git repository and will be ready to be pushed to the repository. 

#### Behind the Scenes:

The script written for the commit testing is activated through the pre-commit hook, one of the committing-workflow hooks involved with git. Basically, the pre-commit hook is run first before the commit message is typed, using it to inspect the files that are about to be committed in order to make sure the developer did not forget anything. 

The script was written within the pre-commit hook itself so that it could be implemented during the git commit process. I called the debuggers within the script itself and created a loop to loop through the committed files.

**This script has only been tested on a Linux based OS.** 

#### Requirements:

There are some requirements in order for this script to work.

The required debuggers should be downloaded. The debuggers needed for this script are shellcheck(shellscript debugger), pylint(python debugger), and goimports(go debugger). The links to download are attached below.

		shellcheck: https://www.shellcheck.net/
		pylint: https://www.pylint.org/
		goimports: https://golang.org/doc/code.html (refer to GOPATH environment variable and Import paths section)

To install the required debuggers, I have created a script that can download the required debuggers needed. 

This script allows you to install any program or file that is needed. It is created as an executable file by running the file with the specific program needed to install. The program will then be installed on your machine, ready for use.

The command needed to be run is:

	./install.sh (program-name)

This script was made using the yum command in order to install the program needed. It first updates the program you require to be downloaded, given that you have it, and then, if the program does not exist, it starts to install the program.

#### Future Improvements:

1. To be able to implement instant installation of necessary programs needed to run the script.
	Integration of the installation script in the git commit process for automatic installation of neces	    sary debuggers

2. To integrate more languages in the pre-commit script in order to check a broader range of files.

3. To test the script in an OS other than Linux and make sure it runs and does not create errors.

