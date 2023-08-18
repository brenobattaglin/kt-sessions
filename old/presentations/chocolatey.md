---
theme: uncover
class:
  - lead
  - invert
marp: true
---

![bg left:40% 80%](../assets/icons/chocolatey.svg)

# Chocolatey

An open-source package manager for windows.

https://chocolatey.org/

---

## Searching and installing a package

```shell
choco search node
```

```shell
choco install nodejs
```

```shell
cinst nodejs
```

---

## Installing many packages

```shell
cinst nodejs androidstudio vscode googlechrome
```

---

## Installing package specific version

```shell
choco install flutter --version=2.0.2
```

---

## Upgrading packages

```shell
choco upgrade vscode
```

or

```shell
choco upgrade all
```

---

## Pinning package version

```shell
choco pin flutter
```

---

## Portable vs. Installers

```shell
choco install flutter
```

Directory: C:/tools/...

```shell
choco install googlechrome
```

Directory: C:/Program Files/...

---

## Listing installed packages

```shell
choco list --local-only
```

or

```shell
clist -l
```

---

## Uninstalling packages

```shell
choco uninstall androidstudio
```

or

```shell
cuninst androidstudio vscode
```

---

## Automating installs

install_packages.ps1

```shell
#Requires -RunAsAdministrator

choco feature enable -n allowGlobalConfirmation

cinst flutter --version=2.0.2
cinst vscode `
    androidstudio `
    docker-desktop `
```
