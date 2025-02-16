# Git Workflow and Development Structure Guide

This guide explains how to effectively organize your development workflow using Git. We'll explore the relationship between your central Git directory, working copies, and GitHub repositories, using practical examples and common scenarios.

## Understanding the Three-Tier Structure

Think of your Git workflow like a library system with three main components:

1. Central Collection (`~/git/`): Like a library's main collection, this is where you maintain organized, clean copies of all your repositories.

2. Working Space: Like a study room where you actively work on books, this is where you create and modify code.

3. GitHub: Like a global library network, this is where you share your work and collaborate with others.

## Directory Organization

### The Central Git Directory
```
~/git/                      # Your local "library"
    programming/           # Section for programming projects
        c-programming/    # Individual repository
        cpp-programming/  # Another repository
    guides/               # Documentation section
        git-setup/       # Setup documentation
        git-workflow/    # Workflow documentation
```

### Working Directory Structure
```
~/projects/                 # Or any workspace you prefer
    current/              # Active projects
        c-programming/   # Working copy of your C project
    experiments/          # For testing new ideas
        feature-test/    # Experimental features
```

## Practical Workflow

### Initial Setup

When starting a new project, first create it in your central Git directory:

```bash
# Create in central directory
cd ~/git/programming
mkdir new-project
cd new-project
git init

# Set up basic structure
mkdir src docs tests
touch README.md

# Initial commit
git add .
git commit -m "Initial project setup"

# Connect to GitHub
git remote add origin git@github.com:username/project-name.git
git push -u origin main
```

### Creating a Working Copy

Instead of working directly in your ~/git directory, create a working copy:

```bash
# Navigate to your working space
cd ~/projects/current

# Clone from your central git directory
git clone ~/git/programming/new-project

# Or clone directly from GitHub
git clone git@github.com:username/project-name.git
```

### Daily Development Workflow

1. Start your work day:
```bash
# Navigate to working copy
cd ~/projects/current/new-project

# Get latest changes
git pull origin main
```

2. Make your changes and commit regularly:
```bash
# Create a feature branch
git checkout -b feature-name

# Work on your changes...
git add .
git commit -m "Implement feature X"
```

3. Push your changes:
```bash
# Push to GitHub
git push origin feature-name

# After review and merge, update local main
git checkout main
git pull origin main
```

4. Synchronize central copy (optional but recommended):
```bash
# Navigate to central copy
cd ~/git/programming/new-project
git pull origin main
```

## Benefits of This Structure

### Organization Benefits
- Clean separation between storage and workspace
- Multiple working copies possible for different features
- Central directory stays organized and clean
- Easy to maintain overview of all projects

### Development Benefits
- Freedom to experiment in working copies
- Clean central copy as backup
- Easy to start fresh by re-cloning
- Multiple working copies for different features

### Collaboration Benefits
- Clear separation between personal and shared code
- Easy to manage multiple versions of the same project
- Simple to sync across different computers

## Common Scenarios and Solutions

### Starting a New Feature

```bash
# In your working copy
cd ~/projects/current/project-name
git checkout main
git pull origin main
git checkout -b new-feature

# Work on feature...
git add .
git commit -m "Implement new feature"
git push origin new-feature
```

### Handling Experiments

```bash
# Clone a fresh copy for experiments
cd ~/projects/experiments
git clone ~/git/programming/project-name experiment-name
cd experiment-name

# Create experimental branch
git checkout -b experimental-feature

# If experiment fails, simply delete the directory
# If successful, push to GitHub and update central copy
```

### Working Across Multiple Computers

```bash
# On first computer
cd ~/projects/current/project-name
git push origin feature-branch

# On second computer
cd ~/projects/current
git clone git@github.com:username/project-name.git
cd project-name
git checkout feature-branch
```

## Best Practices

1. Never work directly in your ~/git directory. This keeps your central collection clean and organized.

2. Always create feature branches in your working copy, not in the central copy.

3. Regular synchronization:
   - Push working copy changes to GitHub
   - Pull GitHub changes to working copy
   - Occasionally sync central copy with GitHub

4. Use meaningful branch names:
   - feature/add-login
   - bugfix/fix-memory-leak
   - experiment/new-algorithm

5. Keep working copies organized:
   - Delete them when done with a feature
   - Create new ones for new features
   - Regularly clean up old working copies

## When to Sync Central Copy

Your central copy in ~/git doesn't need to be updated as frequently as your working copy. Good times to sync include:

- After completing major features
- Before starting new feature branches
- When you want to ensure a clean backup
- Before sharing code with others

## Conclusion

This three-tier structure (Central, Working, GitHub) provides a robust framework for development. It combines the benefits of organized storage, flexible development, and reliable backup. While it might seem like extra work at first, this structure will save time and prevent problems as your projects grow in size and complexity.

Remember: Your central Git directory is like a clean library, your working directory is like a workshop, and GitHub is your connection to the wider world. Keep each in its proper role, and your development workflow will be more organized and efficient.