
# Introduction to Version Control, Git, and GitHub

This document gives a basic explanation of version control, what it is used for, and the difference between Git and GitHub. It is written in a clear and beginner-friendly manner for easy understanding.




## Table of Contents

1. What is Git?

2. What is GitHub?

3. Installing Git on Ubuntu/Linux

4. Setting Your Git Username and Email

5. Creating a GitHub Account

6. Generating SSH Keys on Your Laptop

7. Adding Your SSH Key to GitHub

8. Testing SSH Connection

9. Common Errors and How I Solved Them

10. Full Summary




## What is Version Control?

Version control is a system that helps you keep track of changes made to your files or projects over time. It allows you to go back to previous versions, see what was changed, and manage your work more effectively. It is especially useful when working on projects that are being updated frequently or by multiple people.



## What is Version Control Used For?


Version control is used to:

- Track changes made to files or code

- Restore previous versions of a project

- Collaborate with others without overwriting each other’s work

- Manage different versions of a project or feature



## What is Git?



Git is a free and widely-used version control tool that runs on your local machine. It allows you to save the history of your project, create separate branches for testing or new features, and switch between different versions of your work. Git works offline and gives you full control over your project’s change history.


## What is GitHub?


GitHub is a website (online platform) that lets you store your Git-managed projects in the cloud. It is commonly used to back up code, share projects with others, and collaborate with teammates. GitHub adds features like pull requests, issue tracking, and team management on top of Git.


You must create a GitHub account to use the platform. It works alongside Git by acting as a remote location where your projects can be pushed, pulled, and accessed from anywhere.


## Difference Between Git and GitHub


The table below explains the key differences between Git and GitHub:


| Git                                     | GitHub                                  |
|------------------------------------------|------------------------------------------|

| Local version control tool              | Cloud-based platform for Git repositories |

| Installed on your computer              | Used through a web browser (requires account) |

| Manages version history locally         | Hosts and shares Git projects online     |
| No                                      | Yes (for pushing and pulling code)       |

| Manual file sharing or merge            | Built-in tools for team collaboration    |
| Not required                            | Required to create and manage repos      |




## 3. Installing Git on Ubuntu (WSL or Linux)


## Step 1: Open your terminal and type:



sudo apt install git

Error You Might See:

Error:  Unable to locate package git



# HOW I SOLVED IT:

# Always remeber that before installing anything with apt, you need to update your package manager:


sudo apt-get update

Then install Git again:



sudo apt install git

To Confirm Git Installation type:

git --version ( or you can use git -v)
You should see something like:  git version 2.34.1


4. Setting Your Git Username and Email
These details will appear in your GitHub commit history.


git config --global user.name "iiceekiing"

git config --global user.email "myemail@example.com"
(Please replace the name and email with your real GitHub info.)

To verify:

type:  git config --list


### 5. Creating a GitHub Account
Visit https://github.com

Click Sign Up


Enter your email, username, and password


Verify your email and log in


Your GitHub account is ready.



### 6. Generating SSH Keys (So GitHub Can Recognize Your Laptop)
SSH allows you to push code without typing your username and password every time.


In your terminal:


ssh-keygen -t ed25519 -C "myemail@example.com"
When it asks where to save the file, press Enter to accept the default (~/.ssh/id_ed25519)


Press Enter again if it asks for a passphrase (or enter one if you want)


Then start the SSH agent and add your new key:


eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519

### 7. Adding the SSH Key to Your GitHub Account
First, display your public key:


cat ~/.ssh/id_ed25519.pub

Copy everything it shows (starts with ssh-ed25519).


Then:

Go to https://github.com/settings/keys

Click New SSH Key

Give it a title like: My Laptop SSH Key

Paste the key

Click Add SSH Key


### 8. Testing Your SSH Connection
Now confirm if SSH is working:


ssh -T git@github.com

You’ll see:

## The authenticity of host 'github.com (IP)' can't be established.
Are you sure you want to continue connecting (yes/no/[fingerprint])?

Type: # yes

If all is okay, it will say:

# Hi iiceekiing! You've successfully authenticated, but GitHub does not provide shell access.
This means your SSH key is working properly.



### 9. Cloning a GitHub Repo Using SSH
Go to your repository on GitHub.

Click the green Code button, and choose SSH.

Copy the link (it looks like this):  git@github.com:yourusername/my-repo.git



## Clone it:
git clone git@github.com:username/my-repo.git
Now you can push and pull code without PAT or password.



### 10. Common Errors I Faced (And How I Fixed Them)
Error 1: "Unable to locate package git"
Why: I didn’t update the system before installing.



sudo apt-get update

sudo apt install git

Error 2: "Permission denied (publickey). Could not read from remote repository."

Why: I cloned the repository using HTTPS instead of SSH.



I deleted the folder, went back to GitHub, copied the SSH link, and cloned again:



git clone git@github.com:iiceekiing/my-repo.git

Then it worked.



### 11. Summary of All Steps


Installed Git:

sudo apt update && sudo apt install git



Configured Git:
git config --global user.name and user.email

Created a GitHub account

Generated SSH key with ssh-keygen

Added SSH key to GitHub

Tested with ssh -T git@github.com

Solved two common beginner errors:

Package not found

Permission denied (used HTTPS instead of SSH)




#Final Note
If you're a beginner/techie  this guide is written to help you start using Git and GitHub without stress. Once you get this setup working, pushing your code and collaborating online becomes much easier.




## Conclusion

Git and GitHub are related but not the same. Git helps you manage your project history locally, while GitHub helps you store and collaborate on your projects online. Understanding how both work together is an essential skill for modern software development.


