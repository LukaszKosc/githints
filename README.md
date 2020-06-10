# githints

0. create repo

…or create a new repository on the command line

echo "# testproject" >> README.md
git init
echo .git > .gitignore
echo .gitignore >> .gitignore
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/LukaszKosc/testproject.git
git push -u origin master


…or push an existing repository from the command line

git remote add origin https://github.com/LukaszKosc/testproject.git
git push -u origin master


1. how to add .gitignore and rules to .gitignore if you forgot to do this and you already pushed/committed some code?
(https://stackoverflow.com/questions/11451535/gitignore-is-not-working)

git add .
git commit -m "Initial commit" 

you forgot to add some reg-exps to .gitignore

Run the following commands from the top folder of your git repo:

git rm -r --cached .

echo .git >> .gitignore
echo .gitignore >> .gitignore
...

git add .
git commit -m "fixed untracked files"

When you remove something from .gitignore file the above steps will not work for you. You can try this:
git add -f "filetype"
git commit -m “Refresh removing filetype from .gitignore file.”

Without adding another commit to your project, one line will be enough to make .gitignore work as it is supposed to:

git rm -r --cached debug.log nbproject

2. rebase changes from your branch on some other branch

git checkout branch_name
git log | grep ... (find latest COMMIT_ID which is not in branch_name commits list) 
git reset --soft COMMIT_ID
git stash
git pull --rebase origin branch_you_want_to_rebase_on
git stash pop
git add . # (all changed files)
git commit -m "msg"
git push --force origin branch_name

