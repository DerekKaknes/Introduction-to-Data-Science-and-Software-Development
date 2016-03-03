# Class Agenda

## Terminal - The Basics
The first item on the agenda is getting comfortable executing commands from the
command line through your terminal application.  Depending on your operating
system (Linux vs MacOSX), you will likely have a different terminal application;
however, the commands will be identical or very similar.

Start by opening your terminal application (search for 'terminal' if you cannot find
it) and try some basic navigational commands.

### The Directory Structure
Try typing `pwd` - short for "present working directory".  You should see
something like: `/Users/yourname`.  This output tells you where in your
computers directory structure your cursor is currently located.  The initial `/`
is called the `root` directory - it is the absolute roote of your directory
tree.  Every subsequent `/` represents a subdirectory or folder structure one
level 'down' the directory structure.  

### The List Command
You can see the contents of your present working directoy by typing command `ls`.  This
list function also has a few options that you can access by passing 'flagged'
arguments in the form `-f` or `--flag`.  For example, to see the contents listed
in a long vertical form, use the `-l` flag: `ls -l`.  

Now try using the `-a` flag to list all files, including 'hidden' files whose
names begin with a `.`. 

Finally, you can string flagged arguments together seqeuntially to pass multiple
options: try `ls -la` to list all files in long form.

### Navigating
Now that you know how to find where you are in the directory structure using
`pwd` and you know how to find the contents of your current directory using
`ls`, the natural next step is navigating around the directory structure.

In general, when describing navigating a directory structure, we will refer to
moving "up" towards the `root` of the directory and "down" towards branching
subdirectories.  To move around the directory structure, we use the `cd` or
"change directory" command.  Let's start by moving all the way up to the root
directory by using `cd /`.  Check that you successfully navigated to the root
directory using `pwd`, which should return just `/`.

Now use the `ls` command to view the subdirectories
within the root folder.  Now use the `cd` command to navigate into one of the
subdirectories listed by `ls`.  Next, use `pwd` to show your new working
directory.  Now try using the command `cd ..` followed by `pwd`.  Where did `..`
take you?  Using `cd ..` will navigate one directory up in the structure.  You
can navigate up multiple directories by using `cd ../..` or `cd ../../..` etc.
