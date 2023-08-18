---
theme: uncover
class:
  - lead
  - invert
marp: true
---

![bg left:40% 80%](../assets/icons/git.svg)

# Git

Free and open source distributed version control system.

https://git-scm.com/

---

## Getting Started

1. Install Git
   ```shell
       choco install git
       brew install git
       sudo apt install git
   ```
1. (Optional) Setup the ssh key for the hosting service

1. Setup Git

   ```shell
   git config --global user.name "John Doe"
   git config --global user.email "john.doe@companyemail.com"
   ```

   ```shell
   git config user.name "John Doe"
   git config user.email "john.doe@email.com"
   ```

---

## Getting Started

```shell
git config user.name
git config user.email
```

```shell
git config --global core.editor "code --wait"
git config --global init.defaultBranch develop
```

---

## Clone or initialize a repository

```shell
git clone git@github.com:mozilla-mobile/firefox-ios.git
```

```shell
git clone https://github.com/atom/atom.git
```

```shell
echo "# repo-example" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/brenobattaglin/repo-example.git
git push -u origin main
```

---

## Git branch & log

```shell
git branch forgot-my-password
```

```shell
git branch -m forgot-my-password feature/forgot-my-password
git branch -m feature/forgot-my-password
```

```shell
git branch -r
```

```shell
git branch
```

```shell
git log
```

---

## Git checkout

```shell
git checkout feature/sign-in-google-account
```

```shell
git checkout /src/model/User.js
git checkout .
```

```shell
git checkout -b forgot-my-password
```

---

## Git stash

```shell
git stash
```

```shell
git stash list
```

```shell
git stash pop
```

```shell
git stash pop 0
```

---

## Commiting changes

```shell
## Helpful
git status
git log
```

```shell
git add .
git commit
git push origin main
```

```shell
git status
git add lib/main.dart
git commit -m "This is the title/header" -m "This is the body"
git push
```

---

## Git fetch & pull

```shell
git fetch
git fetch origin feature/sign-in-apple-account
git fetch --all
```

```shell
git pull
git pull origin feature/sign-in-apple-account
```

---

## Git merge

```shell
git pull
git checkout feature/sign-in-apple-account
git pull
git merge master
```

---

## Git aliases

```shell
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

```shell
git co -b feature/sign-in-apple-account
git br feature/forgot-my-password
git ci -m "This is the title"
git st
```

---

Terminals

Windows:

```shell
choco install cmder
```

```shell
choco install microsoft-windows-terminal ## Setup Git bash
```

Linux distros:

```shell
sudo apt install zsh
```

MacOS:

- zsh comes natively

Linux distros and MacOS:

- https://ohmyz.sh/
