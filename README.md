# githints

0. create repo

…or create a new repository on the command line

echo "# testproject" >> README.md\
git init\
echo .git > .gitignore\
echo .gitignore >> .gitignore\
git add README.md\
git commit -m "first commit"\
git remote add origin https://github.com/LukaszKosc/testproject.git\
git push -u origin master

…or push an existing repository from the command line

git remote add origin https://github.com/LukaszKosc/testproject.git\
git push -u origin master

1. how to add .gitignore and rules to .gitignore if you forgot to do this and you already pushed/committed some code?
(https://stackoverflow.com/questions/11451535/gitignore-is-not-working)

git add .\
git commit -m "Initial commit"\

you forgot to add some reg-exps to .gitignore\
Run the following commands from the top folder of your git repo:

git rm -r --cached .\
echo .git >> .gitignore\
echo .gitignore >> .gitignore\
...
git add .\
git commit -m "fixed untracked files"

When you remove something from .gitignore file the above steps will not work for you. You can try this:

git add -f "filetype"\
git commit -m “Refresh removing filetype from .gitignore file.”

Without adding another commit to your project, one line will be enough to make .gitignore work as it is supposed to:

git rm -r --cached debug.log nbproject

2. rebase changes from your branch on some other branch

git checkout branch_name\
git log | grep ... (find latest COMMIT_ID which is not in branch_name commits list)\
git reset --soft COMMIT_ID\
git stash\
git pull --rebase origin branch_you_want_to_rebase_on\
git stash pop\
git add . # (all changed files)\
git commit -m "msg"\
git push --force origin branch_name

3. rebase branch to latest code from master branch

git checkout branch_name\
git pull master\
git checkout branch_name \
(to save work-in-progress code)\
git add path_to_file(s) / git add .\
git stash\
git pull --rebase origin master\
(resolve potential conflicts)\
git stash pop

4. move your local branch to latest commit from remote

git checkout local_branch_name\
git reset --hard origin/remote_branch_name

5. discard all changes in your working directory

git checkout local_branch_name\
do some change -> decide to abandon it all\
git checkout -- .\
or just single file:\
git checkout -- path_to_file

6. when you git add your file and already commit it and want to revert to previous (last from remote) commit:

git checkout local_branch_name\
do some changes...\
git add . \
git commit -m "Commit to be removed..."\
oh, I want to revert to previous commit:\
git log
- commitID1 - Message: Commit to be removed...
- commitID2 - Message: (this is the commit you want to get your local code to)

git reset --soft commitID2\
your code is in repo, last local commit vanished\
git reset --soft
