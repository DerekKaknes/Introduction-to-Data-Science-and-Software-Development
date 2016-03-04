# Class Agenda
In this class, we will be getting introduced to `git` and the git workflow.
Normally, you will be using `git` to track changes to your code, but for now we
are going to demonstrate `git`'s functionality tracking changes to simpler text
files.  By the end of the class, we will using `git` in conjuction with github
to start pulling, reviewing, editing and suggesting updates for other students
files.  Ok, let's get started!

## Version Control
`git` was developed by the open source community to solve the problems arising
from multiple people working on the same overlapping project without overwriting
eachothers' work.  Traditionally, this problem was solved by a centralized
repository, where the most updated file versions were stored and contributors
could "check out" specific files, make changes to them, and then "check in"
those changes.  The problem with this method is obvious: only one person can be
making changes to a file at any given time.  That might work for small,
centralized development projects, but it would not work for massive open source
projects.

`git`'s solution is to act as a decentralized version control system.  Rather than
"checking out" a specific file, users instead "clone" an entire repository and
track any changes that they make to it.  Then, after those changes have been
finalized, `git` allows user to compare those changes to the original version
and determine whether or not those changes should be "merged" in to create a new
most-updated version.  The entire `git` process will seem complex, cryptic and
confusing at first, but with a little bit of practice you will be thinking
`git`-like in your sleep.

## The Git Workflow
To get your feet wet with `git`, we are going to start by using `git` to track
changes to a repository you create on your local machine.  Let's get started:
### Initializing a Git Repo
First, let's open a shell command prompt and navigate to a directory where we
want to save our work.  Next, let's create a directory called 'TestGit' by using
`mkdir TestGit`.  Now navigate into that directory with `cd TestGit`.  Great,
now we should be in a new and completely empty directory.  Let's double check
that by using `ls -la` to see if there are any hidden files.  You should see
only two files, `.` and `..`.  You can ignore those (they are shortcuts to help
you navigate).

Now, let's initalize a new git repository by using the `git init` command
([Documentation Here](https://git-scm.com/docs/git-init)).  You should see
something like the following as a result: `Initialized empty Git repository in
.../TestGit/.git/`.  Great! But what does that mean.  Let's find out by using
the `ls -la` command again - we should now see a new directory called `.git`
within our `TestGit` directory. Essentially, `git` uses the contents of this
hidden directory to record and manage all of the changes made within the
`TestGit` directory - which we would now call a 'git repository'.  
### Checking Status and Initial Commits
Ok, great.  So we've got our git repo setup and are ready to start developing.
The first thing we should do is check our status using `git status`.  You should
receive a message saying something to the effect of:
```
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```
There are a couple important pieces of information in this statement, so let's
take them line-by-line.  

`On branch master` tells you which branch of the git tree you are on.  Branching
is a critical concept in the `git` workflow, and one that most people find
confusing when first introduced (so don't worry if it seems strange now).  The
concept of branching is simple: each repository has a single `master` branch
from which all other users can copy from and suggest changes to.  However,
experimental changes and development is never done on this `master` branch,
those take place soley on offshooting branches, which are typically called `feature`
branches (because they usually correspond to added a specific new feature to the
application). Once these experimental changes have been thoroughly reviewed,
tested and amended, only then are those changes `merged` into the `master`
branch.  In this way, the `git` workflow ensures that the `master` branch is
always clean and up-to-date so that any new contributors know where to look for
the most recent versioning.

`Initial commit` tells us the most recent `commit` on our current branch, from
which we will be adding new changes and subsequent `commits`.  Because we just
created this git repo, we don't have a previous `commit` and so `git` tells us
that we are currenlty working on the `Initial commit`.  We will talk more
about `commit` in the next section.

`nothing to commit...` tells us that `git` has not found any changes made to the
`TestGit` directory since our last `commit`.  That makes sense, considering all
we have done is create the repo and have not added any files.  Let's change
that, by adding a new file called `test.txt`.  We can create this file by using
the command `touch test.txt`.  We can check that the new file exists by running
`ls` or `git status`, both of which should reference the newly created
`test.txt`. 

### Staging and Committing
Now that we have a new file in the repository, let's make sure that `git` is
tracking it and noting any changes.  As we saw with `git status`, `git` has
already recognized that a new file exists in the repo, but `git` has not yet
committed it to the repository.  We firmly commit changes to a repository in to
steps: `git add` to stage changes and `git commit` to confirm them.  

Let's start by staging `test.txt` by using `git add test.txt`.  If we re-run
`git status` we should see that `test.txt` now shows up under `Changes to be
committed:`.  

Now, to commit that file, use `git commit -m <message>`, where the `-m` flag
allows you to append a message describing the changes that you are committing.
Commit messages are extremely useful when reviewing past changes and
understanding the developer's motivation for each commit - particularly when
more than one person are working on the same repository.  Let's use this
practice by adding the message `Adding first test file` as a commit message.

So, your commit command should look like: `git commit -m "Adding first test
file."`

We can now check that our commit was received by using `git log`, which should
show the recent commit along with the message.
### Branching and Developing
Now that we have our first commit in the repo, let's start making some more
substantial additions to our repo.  But before we continue development, we first
need to learn about `git branch`.  We mentioned branching conceptually above,
but now let's put it to use.  First, call the `git branch` command, which will
return all existing branches.  In this case, you should only see the `master`
branch as we have not yet created any others.  Before we make any further
changes to our repo, let's create a new `branch` to develop and experiment on.

We can create a new branch  by using `git checkout -b <branch_name>`.  Let's create a new
branch called `my-first-branch` by calling the command `git checkout -b
my-first-branch`.  In response, you should have seen something like: `Switched
to a new branch 'my-first-branch'`.  We can confirm this change by using `git
status`, which now tells us that we are `On branch my-first-branch`.  Further,
if we run `git branch` a second time, we will now see that both `master` and
`my-first-branch` show up.

We can switch back and forth between branching by using the `git checkout
<branch_name>` command (the same one we used to create the branch, just without
the `-b` flag).  So if we want to hop back to the `master` branch, we can call
`git checkout master`.  For now, let's stay on `my-first-branch`.

Now that we have a new branch, let's start adding some additional features to
the code in our repo.  In this case, all we have is a single, empty text file -
`test.txt`.  Let's add some text to it.  Remembering back to last class, let's
use some shell commands to generate text and pipe it into the `test.txt` file.
Let's start by appending all of our environmental variables into the file using
the following commands (remember the difference between `>` and `>>`?):
```
echo "These are my environmental variables:\n" > test.txt
env >> test.txt
```
Let's check to see what we added by printing the contents to `stdout` using `cat
test.txt`.  You should see a series of `KEY=value` pairs printed on each
line.

Now that we made changes to `test.txt`, let's check to see if git has tracked
them by using `git status`.  You should now see that `test.txt` shows up under
`Changes not staged for commit:` and has a prefix of `modified:`.  Let's now
stage these changes by using `git add test.txt` and check its success with `git
status`.  We should now see that `test.txt` shows up under `Changes to be
committed:`.  Perfect, now let's commit those changes using `git commit -m
"Adding env variables"`.

Great, we've got another commit under our belt.  Now try on your own to make
another commit after completing the following additions to your repo:
1.  Append a new line of text to `test.txt` using the `echo <text> >> test.txt`
command.
2.  Create a new file called `processes.txt` using the `touch` command.
3.  Add a list of all your locally running processes by using `ps aux | grep
<username>` (remember that `|` is used to pipe the output from one shell command
into another.  If you don't recognize `ps aux` or `grep`, then use google to
quickly familiarize yourself).

### Merging into Master
`git checkout master`
`git merge my-first-branch`
`git branch -d my-first-branch`

## Github
