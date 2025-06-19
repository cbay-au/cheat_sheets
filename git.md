
### Work Flow
# 1. Check status
git status
git remote -v

# 2. Review changes (optional)
git diff README.md

# 3. Stage the README file
git add README.md
# Stage all modified files
git add .

# 4. Commit with a message
git commit -m "Update README.md with improved documentation"

# 5. Push to remote
git push origin main

# Check that your local branch is up to date with remote
git status

# View the commit history
git log --oneline -3

after git clone use;
 git remote set-url origin git@github.com:cbay-au/ngi
nx_serverblock_management.git
