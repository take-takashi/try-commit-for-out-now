# try-commit-for-out-now

外出先からiPhoneでMacにSSHして、git操作をする試み。

## 前提の環境

- 普段はmacからgit操作をしており、署名は1passwordの認証を用いている。

## やりたいこと

- 外出先のiPhoneからMacにSSH接続する。（`tailscale`+`terminus`でできている）
- SSH接続中でも`git commit`したい。  
  （SSH上でgit操作を行うとmacの画面上に1passwordの`TouchID`要求が出てしまい、対応できない）
