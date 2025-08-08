# try-commit-for-out-now

外出先からiPhoneでMacにSSHして、git操作をする試み。

## 前提の環境

- 普段はmacからgit操作をしており、署名は1passwordの認証を用いている。

## やりたいこと

- 外出先のiPhoneからMacにSSH接続する。（`tailscale`+`terminus`でできている）
- SSH接続中でも`git commit`したい。  
  （SSH上でgit操作を行うとmacの画面上に1passwordの`TouchID`要求が出てしまい、対応できない）

## 試み1（諦めた）

複数回の未署名コミットに対する後からの署名が面倒なため。

### 外出先（1passwordの署名を問われないようにする）

この時、`push`はせずに`commit`のみ実行するとする。

```bash
try-commit-for-out-now % git add .
try-commit-for-out-now % git commit --no-gpg-sign --allow-empty -m "Test WIP commit"
```

### 外出先から帰ってきたらmacで実行

```bash
try-commit-for-out-now % git commit --amend -S --no-edit
try-commit-for-out-now % git push --force-with-lease
```

### メモ

- 複数回WIPしたらどうなる？
- 最新のコミットのみ署名された。
- すべてのコミットを署名するには？

## 試み2

- 結局、パスフレーズ入力で実行できるGPGキーを発行して、外出先ではそのキーでcommitを署名することにした。
  - 結果、成功
