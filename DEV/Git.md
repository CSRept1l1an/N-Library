1. Introduction to Git
2. Setting Up Git
3. Basic Commands  
## 1. Introduction to Gi
### What is Git?
Git is a distributed version control system designed to handle everything from small to very large projects with speed and efficiency. It allows multiple developers to work on a project simultaneously without overwriting each other's changes.

### Basic Concepts

- **Repository (Repo)**: A directory which contains your project work, including all files and folders, along with a special `.git` directory that stores the version control information.

- **Clone**: A copy of a repository. When you clone a repository, you get all the files, commit history, and branches of the original repository.

- **Commit**: A snapshot of your project at a point in time. Commits are the fundamental unit of change in Git, and each commit has a unique SHA-1 hash.

- **Branch**: A pointer to a specific commit. Branches allow you to work on different versions of your project simultaneously. The default branch name in Git is `main` (formerly `master`).

- **Merge**: Combining changes from different branches. Git's merge functionality allows you to integrate changes from different branches into a single branch.

- **Staging Area (Index)**: A place where you can group changes together before committing them. It acts as a buffer between the working directory and the repository.

- **Working Directory**: The directory on your computer where you make changes to your project files. These changes can be staged and then committed to the repository.

- **Remote**: A common repository that all team members use to exchange their changes. It can be hosted on a service like GitHub, GitLab, or Bitbucket.

- **Pull**: Fetching changes from a remote repository and merging them into your local repository.

- **Push**: Sending your committed changes to a remote repository.

- **Conflict**: Occurs when changes from different branches clash. Conflicts need to be resolved before merging can complete.

### Diagram: Basic Git Workflow

```
Local Repository                              Remote Repository

Working Directory  ->  Staging Area  ->  Local Repository  ->  Remote Repository
(edit)               (stage)             (commit)                (push)
									   |                     (fetch)
									   |<--------------------------------
										   (pull)
```

### Summary
Git is a powerful tool for version control, enabling collaboration and efficient project management through its core concepts of repositories, commits, branches, and remotes. Understanding these basic concepts is crucial for effectively using Git in any project.

## 2. Setting Up Git

### Installation

##### Windows
1. Download the Git installer from [git-scm.com](https://git-scm.com/download/win).
2. Run the installer and follow the setup instructions.
3. Open Git Bash to start using Git.

##### macOS
1. Open Terminal.
2. Install Homebrew if you haven't already:
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

3. Install Git using Homebrew:
```sh
brew install git
```

4. Verify the installation:
```sh
git --version
```

##### Linux
- **Debian/[[Ubuntu]]**:
```sh
sudo apt update
sudo apt install git
```

- **Fedora**:
```sh
sudo dnf install git
```

- **Arch**:
```sh
sudo pacman -S git
```

Verify the installation with:
```sh
git --version
```

### Configuration

After installing Git, you need to configure it with your user information, which will be used for your commits.

1. **Set Your Username**:
```sh
git config --global user.name "Your Name"
```

2. **Set Your Email**:
```sh
git config --global user.email "your.email@example.com"
```

3. **Set Your Default Text Editor**:
```sh
git config --global core.editor "your_editor"
```
Replace `"your_editor"` with your preferred text editor, e.g., `"vim"`, `"nano"`, or `"code"` for VS Code.

4. **Check Your Configuration**:
```sh
git config --list
```

#### Example
```sh
# Set global username and email
git config --global user.name "Jane Doe"
git config --global user.email "jane.doe@example.com"

# Set default editor to Vim
git config --global core.editor "vim"

# Verify configuration
git config --list
```

### Git Configuration File

Git stores configuration settings in three different files, depending on the scope:

- **System-wide** (all users and all repositories):
- Located at `/etc/gitconfig` on Linux systems.
- To configure: `git config --system`

- **User-specific** (all repositories for the current user):
- Located at `~/.gitconfig` or `~/.config/git/config`.
- To configure: `git config --global`

- **Repository-specific** (specific to the current repository):
- Located in the `.git/config` file in the root of the repository.
- To configure: `git config` without any `--global` or `--system` flags.

## 3. Basic Commands
### Initialize Repository

- **Command**: `git init`
- **Description**: Initialize a new Git repository in the current directory. Creates a `.git` directory that contains all the necessary metadata and version history.
- **Example**:
```sh
git init
```

### Clone Repository

- **Command**: `git clone <repository_url>`
- **Description**: Create a copy of an existing repository. This command downloads all the files, branches, and commit history from a remote repository.
- **Example**:
```sh
git clone https://github.com/user/repository.git
```

### Check Repository Status

- **Command**: `git status`
- **Description**: Show the status of the working directory and staging area. It displays which changes have been staged, which haven't, and which files are not being tracked by Git.
- **Example**:
```sh
git status
```

### View Changes

- **Command**: `git diff`
- **Description**: Show the differences between the working directory and the staging area, or between commits. Useful for reviewing changes before committing.
- **Example**:
```sh
git diff
```

### Add Changes

- **Command**: `git add <file_or_directory>`
- **Description**: Add changes in the working directory to the staging area. This command stages the changes you want to commit.
- **Examples**:
```sh
git add file.txt         # Add specific file
git add .                # Add all changes in the current directory
```

### Commit Changes

- **Command**: `git commit -m "Commit message"`
- **Description**: Record changes to the repository with a descriptive message. The commit captures the current state of the staged changes.
- **Example**:
```sh
git commit -m "Initial commit"
```

- **Command (Skip Staging)**: `git commit -a -m "Commit message"`
- **Description**: Stage and commit all changes in one step, bypassing the staging area.
- **Example**:
```sh
git commit -a -m "Updated README file"
```

### Remove Files

- **Command**: `git rm <file>`
- **Description**: Remove files from the working directory and stage the removal for commit.
- **Example**:
```sh
git rm file.txt
```

- **Command (Keep File Locally)**: `git rm --cached <file>`
- **Description**: Remove files from the staging area, but keep them in the working directory.
- **Example**:
```sh
git rm --cached file.txt
```

### Move/Rename Files

- **Command**: `git mv <old_filename> <new_filename>`
- **Description**: Move or rename a file and stage the change for commit.
- **Example**:
```sh
git mv old_name.txt new_name.txt
```
