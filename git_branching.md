# How to Implement Git Branching 
🔹 Step 1: Check current branches
git branch

🔹 Step 2: Create a new branch
git branch feature-login


Or in one command (create + switch):

git checkout -b feature-login

🔹 Step 3: Switch to the new branch
git checkout feature-login

 OR 

 git swicth -c oasis (creating and swicthing to a new branch immediately)

🔹 Step 4: Work on your changes

Edit files, add features, fix bugs, etc.

After making changes:

git add .
git commit -m "Added login feature"

🔹 Step 5: Push the branch to GitHub (optional)

git push origin feature-login

🔹 Step 6: Merge the branch into main

First switch back to main:

git checkout main(old)  or git switch main(new)

Update main:

git pull

Merge:

git merge feature-login

🔹 Step 7: Delete the branch (optional)

After merging:

git branch -d feature-login


Or delete from GitHub:

git push origin --delete feature-login

# Pushing your work from the local repository to github

1.Get a file (or project) from GitHub to your local computer

2.Create a branch

3.Make changes

4.Push the changes back to GitHub

# PART 1: How to Get a File (Project) from GitHub to Your Local Machine
Step 1: Copy the GitHub Repository URL

On GitHub → Go to the repository → Click Code → Copy:

HTTPS URL (recommended)

Example:

https://github.com/username/repository-name.git

## Step 2: Clone the Repository

Open your terminal or Git Bash and run:

git clone https://github.com/username/repository-name.git


This downloads the entire project folder to your computer.

## Step 3: Enter the Project Folder
cd repository-name

# PART 2: Create a Branch From Your Local Repository
## Step 4: Create a New Branch
git checkout -b my-new-branch

This does two things:

Creates a branch called my-new-branch

Switches you to that branch

# PART 3: Make Changes to the File
## Step 5: Edit the files

Open the folder in:

VS Code

PyCharm

Notepad++

Any text editor

Make your required changes, save the file.

# PART 4: Add and Commit the Changes
## Step 6: Stage the changes
git add .


(Stages all modified files)

OR stage specific files:

git add file.txt

## Step 7: Commit the changes
git commit -m "Updated file with new changes"

# PART 5: Push the Branch Back to GitHub
## Step 8: Push the branch
git push origin my-new-branch

This uploads your work to GitHub under the branch name my-new-branch.

<!-- # PART 6: Create a Pull Request (Optional but recommended)

Go to GitHub → You will see:

"Compare & Pull Request"

Click it → Write a description → Submit. -->

# PART 6: Merge Your Branch After Pushing to GitHub

Once you have pushed your branch using:

git push origin my-new-branch


You can now merge it.

#  Merge Using GitHub 
## Step 1: Go to the Repository on GitHub

Open the repository page on GitHub.

## Step 2: Click “Compare & Pull Request”

GitHub will automatically detect your new branch.

You will see a yellow or green banner like:

"my-new-branch had recent pushes. Compare & pull request."

Click Compare & Pull Request.

## Step 3: Write a Pull Request Message

Add:

Title (e.g., "Added updated file")

Description of what you changed

## Step 4: Submit Pull Request

Click:

✔ Create Pull Request

This sends the request to merge your branch into main.

## Step 5: Review and Approve the PR

If you are working alone:

You simply review your changes.

If working in a team:

Another team member reviews and approves.

## Step 6: Merge the Pull Request

Once ready, click the green button:

✔ Merge Pull Request
then
✔ Confirm Merge

## Step 7: Delete the Branch (Optional)

After merging, GitHub will ask:

“Delete branch?”

Click Delete branch to clean up your repository.

OR 

git branch -d [the branch name to be dleted] =>locally
git push --delete origin [the branch name to be deleted] => remotely

# How to merge and update the local repository

## METHOD 1: Using git pull (Most Common & Recommended)

git pull downloads updates from the remote repository and merges them automatically into your local branch.

## Step-by-step:

1. Open your project folder
cd your-project-folder

2. Check your current branch
git branch

Make sure you're on the branch you want to update (usually main or master).

3. Switch to the correct branch (if needed)
git checkout main
or 
git switch main

4. Pull the latest changes
5. 
git pull origin main

Result:
Your local main branch is now updated with everything in the remote GitHub main branch.

## METHOD 2: Using git fetch + git merge (Safer Advanced Method)

This method is preferred when you want to review changes before merging.

Step 1: Fetch changes
git fetch origin


This downloads changes but does NOT merge them.

Step 2: View differences (optional)
git log HEAD..origin/main


or

git diff HEAD origin/main

Step 3: Merge the remote updates
git merge origin/main

# SHOW COMMAND
git show is a Git command used to display detailed information about commits, tags, and other Git objects. It is one of the most useful commands when you want to see exactly what changed in a specific commit.
## Output of the show command
1.git show displays:

2.The commit hash

3.Author information

4.Date/time

5.Commit message

6.The actual file changes (diff output)

## How to use the show commands

Basic Usage
### 1. Show the latest commit
git show

### 2. Show a specific commit
git show <commit-hash>


Example:

git show 7a3bd1f

### 3. Show a specific file change inside a commit
git show <commit-hash> -- <filename>

### 4. Show only the commit metadata (no diff)
git show --no-patch

# Understanding the Output of git show

You will typically see something like this:

commit 7a3bd1fadec12f492957109a4e1bd6c76f8ad271
Author: John Doe <john@example.com>
Date:   Thu Jan 23 12:45:31 2025 +0100

    Fixed bug in login authentication

diff --git a/login.py b/login.py
index 4f2e3ab..8a0bf22 100644
--- a/login.py
+++ b/login.py
@@ -24,7 +24,7 @@ def authenticate(user, password):
     if not user:
         return False
 
-    return password == user.password
+    return verify_password(password, user.password)


## Let's break it down:

### 1. Commit Header
Commit Hash
commit 7a3bd1fadec12f492957109a4e1bd6c76f8ad271


This uniquely identifies the commit.

Author
Author: John Doe <john@example.com>


Who made the commit.

Date
Date:   Thu Jan 23 12:45:31 2025 +0100


When the commit was created.

### 2. Commit Message
Fixed bug in login authentication


A short description of what was changed.

### 3. Diffstat + Patch (The Actual Changes)
File info
diff --git a/login.py b/login.py
index 4f2e3ab..8a0bf22 100644

Removed / Added lines
--- a/login.py
+++ b/login.py


Shows before (a/) and after (b/) versions of the file.

Line numbers affected
@@ -24,7 +24,7 @@


Meaning:

Old version: line 24, affected 7 lines

New version: line 24, affected 7 lines

Changes Inside the File
Removed line (marked with -)
-    return password == user.password

Added line (marked with +)
+    return verify_password(password, user.password)


This shows exactly what changed in the commit.

# Why is git show important?

Because it helps you:

✔ Understand what a commit actually did
✔ Review contributions before merging
✔ Debug issues caused by past commits
✔ Identify who changed what and why
✔ Inspect tags, annotated tags, and objects

# Other Useful Variants
Show only the name of files changed
git show --name-only <commit>

Show changes in a compact view
git show --stat <commit>

Show only part of the diff
git show --color-words <commit>

## Summary
Command	What it does
git show	Shows latest commit details
git show <hash>	Shows details of a specific commit
git show --no-patch	Show commit metadata only
git show --name-only	List changed files only
git show --stat	Summary of changes
git show <hash> -- <file>	Show changes for a specific file


# TERMS
Key GitHub Terms: Definitions, When to Use Them & How to Use Them
1️⃣ Repository (Repo)
What it is

A repository is a storage space on GitHub where your project files, code, documentation, and version history are kept.

When to use it

When starting a project

When storing code online

When collaborating with others

How to use it

Create a repo on GitHub

Clone it to your computer using:

git clone <repo-url>


Add/commit/push code.

2️⃣ Branch
What it is

A branch is a separate version of your code where you can make changes without affecting the main project.

When to use it

Adding new features

Fixing bugs

Testing new ideas safely

How to use it
git checkout -b feature-branch


After changes:

git add .
git commit -m "new feature"
git push origin feature-branch

3️⃣ Commit
What it is

A commit is a saved snapshot of your project at a specific point in time.

When to use it

After completing a task

When fixing a bug

When making any logical change

How to use it
git add .
git commit -m "Describe what you changed"

4️⃣ Push
What it is

Push sends your local commits to GitHub (remote repo).

When to use it

When you want your changes uploaded

When collaborating with others

How to use it
git push origin branch-name

5️⃣ Pull
What it is

Pull updates your local repository with the newest changes from GitHub.

When to use it

Before starting work each day

After someone merges a PR

When your repo is behind

How to use it
git pull origin main

6️⃣ Fork
What it is

A fork is your personal copy of someone else’s repository.

When to use it

Contributing to open-source

You cannot push directly to the original repo

How to use it

Click Fork on GitHub

Clone your fork

Make changes and then submit PRs

7️⃣ Pull Request (PR)
What it is

A request asking the project owner to review and merge your changes.

When to use it

When your branch or fork is ready to be merged

When contributing to a project

How to use it

Push your branch

Click New Pull Request

Describe the changes

Submit PR

8️⃣ Merge
What it is

Combining changes from one branch into another (usually feature → main).

When to use it

When PR is approved

After successful review

How to use it

On GitHub:

Open PR

Click Merge Pull Request

Or using Git:

git merge feature-branch

9️⃣ GitHub Issues
What it is

A tracking system used to report bugs, propose features, or manage tasks.

When to use it

You find a bug

You want to request an improvement

You want to assign tasks to team members

How to use it

Go to Issues → New Issue
Add title, description, labels, assignee.



# PUSHING YOUR WORK
Start locally first, then create GitHub repo

If your project was already started locally:

Step 1: Create an empty repo on GitHub (no README)
Step 2: Connect and push:
git remote add origin https://github.com/username/repo.git
git branch -M main
git push -u origin main