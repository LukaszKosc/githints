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

2. ...
