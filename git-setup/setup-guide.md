# Git and GitHub Setup Guide

This guide documents the process of setting up Git and GitHub for a programming course repository. We'll cover everything from initial configuration to creating a well-structured repository.

## 1. Initial Git Configuration

First, let's ensure Git is configured correctly with our identity. These settings will be used for all Git repositories on your system.

```bash
# Configure user name and email
git config --global user.name "David Meister"
git config --global user.email "davidmeister90@gmail.com"

# Set the default branch name to 'main'
git config --global init.defaultBranch main

# Verify the configuration
git config --global --list
```

Expected output:
```
user.name=David Meister
user.email=davidmeister90@gmail.com
init.defaultbranch=main
```

## 2. Creating a Repository Structure

We'll create a logical directory structure for our programming course materials. This structure separates different types of content for better organization.

```bash
# Navigate to the git directory and create project folder
cd ~/git/informatics
mkdir c-programming
cd c-programming

# Initialize Git repository
git init

# Create directory structure
mkdir resources tools exercises projects

# Create README file with repository description
cat > README.md << 'EOF'
# C Programming Repository

This repository contains materials and code for C programming studies.

## Structure

- resources/: Collection of formulas, tutorials, notes, and documentation
- tools/: Executable code and utility programs
- exercises/: Programming exercises with templates and solutions
- projects/: Larger project assignments
EOF
```

## 3. Connecting to GitHub

Now we'll link our local repository with GitHub. We're using SSH for secure and convenient authentication.

```bash
# Add GitHub repository as remote
git remote add origin git@github.com:Master-D1990/mr_c-programming.git

# Verify remote configuration
git remote -v
```

Expected output:
```
origin  git@github.com:Master-D1990/mr_c-programming.git (fetch)
origin  git@github.com:Master-D1990/mr_c-programming.git (push)
```

## 4. Initial Commit and Push

Let's commit our directory structure and push it to GitHub.

```bash
# Stage all files
git add .

# Create initial commit
git commit -m "Create basic repository structure"

# Rename master branch to main (if needed)
git branch -M main

# Push to GitHub with upstream tracking
git push -u origin main
```

## Important Git Concepts Covered

1. **Repository Organization**: 
   - Using a clear directory structure
   - Separating different types of content (resources, tools, exercises, projects)
   - Creating informative README documentation

2. **Git Configuration**:
   - Global user settings
   - Default branch naming
   - Remote repository setup

3. **Best Practices**:
   - Using English for documentation and commit messages
   - Implementing clear folder structures
   - Following standard Git workflows

4. **SSH Authentication**:
   - Using SSH for secure GitHub connection
   - Understanding server fingerprint verification

## Next Steps

After this setup, you can:
1. Start adding content to each directory
2. Create specific README files for each section
3. Begin tracking your programming exercises
4. Collaborate with others through GitHub

Remember to commit changes regularly with clear, descriptive commit messages in English. This helps maintain a clean and understandable project history.

## Understanding Git vs. GitHub and Naming Conventions

Let's explore the fundamental differences between Git and GitHub, and how this affects our naming conventions and organization.

### Git vs. GitHub: The Local and Remote Relationship

Think of Git as your personal workshop and GitHub as a public exhibition space. They serve different purposes but work together seamlessly:

**Git (Local)**:
- Lives on your computer in the form of `.git` directories
- Manages version control of your files
- Uses local folder names that make sense for your workflow
- Example path: `~/git/programming/c-projects/`

**GitHub (Remote)**:
- Lives on the internet as a web service
- Provides a platform for sharing and collaboration
- Uses repository names that are meaningful to others
- Example path: `github.com/username/mr_c-programming`

### Naming Conventions and Their Purposes

**Local Directory Names (Git)**:
- Usually lowercase with hyphens for spaces (`c-programming`)
- Can be organized in hierarchical folders (`~/git/courses/programming/`)
- Focus on personal organization and clarity
- Names can be changed without affecting Git functionality
- Example structure:
  ```
  ~/git/
      programming/
          c-programming/
          cpp-programming/
      courses/
          mathematics/
          robotics/
  ```

**Remote Repository Names (GitHub)**:
- Often include prefixes for categorization (`mr_c-programming`)
- Use underscores or hyphens for spaces
- Focus on discoverability and project identification
- Names appear in URLs and should be web-friendly
- Example repositories:
  ```
  github.com/username/
      mr_c-programming
      mr_cpp-programming
      mr_mathematics
      mr_robotics
  ```

### Prefix Conventions and Their Meaning

Prefixes in GitHub repository names serve several purposes:

1. **Project Type Identification**:
   - `lib-` for libraries
   - `app-` for applications
   - `doc-` for documentation
   - `tool-` for utilities

2. **Course or Domain Markers**:
   - `mr_` for Mobile Robotics
   - `cs_` for Computer Science
   - `math_` for Mathematics

3. **Status or Purpose**:
   - `archived-` for inactive projects
   - `demo-` for demonstration purposes
   - `test-` for testing repositories

### Important Notes About Naming

1. **Local-Remote Independence**:
   Your local folder `c-programming` can perfectly connect to a remote repository named `mr_c-programming`. The connection is managed by Git's remote URL configuration, not by matching names.

2. **Consistency Matters**:
   While local and remote names can differ, maintaining a consistent naming scheme helps you stay organized. Consider using similar patterns in both places.

3. **Changing Names**:
   - Local directory names can be changed easily without affecting Git
   - GitHub repository names can be changed through settings, but this requires updating remote URLs
   - Always update your remote URLs after changing GitHub repository names:
     ```bash
     git remote set-url origin new-url
     ```

4. **Best Practices**:
   - Use lowercase letters for both local and remote names
   - Avoid spaces in both local and remote names
   - Keep names descriptive but concise
   - Use consistent separators (either hyphens or underscores)
   - Include relevant prefixes in GitHub names for better organization

### Practical Example

Let's say you're working on a mobile robotics course with multiple programming components:

Local Structure:
```
~/git/
    programming/
        c-programming/           # Local working directory
            resources/
            exercises/
            projects/
```

GitHub Structure:
```
github.com/username/
    mr_c-programming            # Remote repository
    mr_cpp-programming
    mr_robotics_simulation
    mr_project_documentation
```

The connection between them is maintained through Git's remote configuration, regardless of the different naming conventions used locally and remotely.

## Troubleshooting Guide

When working with Git, you might encounter various issues. Here's how to handle common problems:

### Branch Name Mismatch
If you see an error like:
```bash
error: src refspec main does not match any
error: failed to push some refs to 'github.com:username/repository.git'
```

This typically occurs when your local branch name doesn't match the remote branch. To fix this:

```bash
# Check your current branch name
git branch

# If you see 'master' instead of 'main', rename it:
git branch -M main

# Then try pushing again
git push -u origin main
```

### Authentication Issues
When you see:
```bash
The authenticity of host 'github.com' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
```

This is a security feature, not an error. You should:
1. Verify the fingerprint matches GitHub's official fingerprint
2. Type 'yes' to confirm and continue
3. The fingerprint will be saved for future connections

### Repository Already Exists
If you see:
```bash
Reinitialized existing Git repository in /path/to/directory/.git/
```

This means Git is already initialized in this directory. It's harmless, but you should:
1. Use `git status` to check the current state
2. Use `git remote -v` to verify remote connections
3. Continue with your intended commands

### HTTPS vs SSH Issues
If you're having authentication problems or want to switch between HTTPS and SSH:

```bash
# Check current remote URL
git remote -v

# Remove existing remote
git remote remove origin

# Add new remote with SSH
git remote add origin git@github.com:username/repository.git
# OR with HTTPS
git remote add origin https://github.com/username/repository.git
```

### File Changes Not Showing
If your changes aren't being tracked:

```bash
# Check the status of your files
git status

# If files aren't showing up, make sure they're added:
git add .

# Verify they're staged
git status

# Then commit
git commit -m "Your message here"
```

### Commit to Wrong Branch
If you accidentally commit to the wrong branch:

```bash
# Save your current changes
git stash

# Switch to the correct branch
git checkout correct-branch

# Apply your changes
git stash pop

# Then commit and push
git add .
git commit -m "Your message"
git push
```

### Undo Last Commit
If you need to undo your last commit but keep the changes:

```bash
git reset --soft HEAD~1
```

Or if you want to completely remove the last commit and its changes:

```bash
git reset --hard HEAD~1
```

### Fixing Git Global Configuration
If you need to modify your global Git settings:

```bash
# View current settings
git config --global --list

# Update settings
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main

# Remove a setting
git config --global --unset setting.name
```

### Wrong Remote URL
If you've added the wrong remote URL:

```bash
# Check current remote
git remote -v

# Remove incorrect remote
git remote remove origin

# Add correct remote
git remote add origin correct-url

# Verify
git remote -v
```

Remember: Before trying any correction commands, especially destructive ones like `reset --hard`, make sure you understand what they do and consider making a backup of your work.

## Notes About Git Structure

The repository structure we've created follows educational best practices:
- `resources/` holds reference materials and documentation
- `tools/` contains reusable code and utilities
- `exercises/` is for practice problems and their solutions
- `projects/` stores larger, more complex assignments

This structure helps maintain a clear separation of concerns and makes it easier to find specific materials when needed.
Empty folder aren't keept in Git. To keep them they can bei initialised with a README or a gitkeep file.