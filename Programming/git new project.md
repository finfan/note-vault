---
tags:
  - github
  - git
---
Make sure any computer you are using git on is set up with keys to [GitHub](https://github.com/)
for instructions use this link

[Setup Keys for GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

To Initialize a New Project do the following
In a command prompt cd into the project folder and enter the following commands.
```text
git init
git add .
git commit -m "Initial commit"

```

to clone a repo 
```text
git clone git@github.com:username/repository.git
```

After cloning or pulling a repo from [GitHub](https://github.com/) to new computer.
Run this command. This is only if it is an npm package.
```text
npm install
```

If you make changes enter the following commands to push the new changes.
```txt
git add .
git commit -m "you commit message"
git push
```