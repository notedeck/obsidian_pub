---
tags:
  - git
created: 2025-05-15T20:39
updated: 2025-05-19T03:52
---
## トラブルが発生した際に戻るため

### 過去のコミット履歴

```
git log --oneline

```

```
0a42548 (**HEAD ->** **main**, **origin/main**, **origin/HEAD**) vault backup: 2025-05-17 14:14:11

b893c0b vault backup: 2025-05-17 14:09:08

179a27e vault backup: 2025-05-17 12:54:02

8b8c612 vault backup: 2025-05-17 12:49:00

b7dacf1 vault backup: 2025-05-17 12:43:58

a131415 vault backup: 2025-05-17 12:38:55

1881922 vault backup: 2025-05-17 12:33:53

52035eb vault backup: 2025-05-17 12:13:47

ab0629f vault backup: 2025-05-17 12:08:45

b73533e vault backup: 2025-05-17 03:54:38

0383ec7 vault backup: 2025-05-17 03:43:56

e642b55 vault backup: 2025-05-17 03:38:54

5e8d367 test

f611b70 vault backup: 2025-05-17 03:05:24

4c856b9 vault backup: 2025-05-17 03:00:22

d8f5174 update footer

09f193e vault backup: 2025-05-17 01:58:14

b4cb970 rename notes

e08d2c4 add notes

bf589f2 fix: symlink notes -> 0_pub

27981ac add index

4138cce upgdate readme

6690560 upgrade2

9403f8f upgrade

a4ea82c fix: downgrade upload-artifact to v2 due to v3 bug 2

66ab76e fix: downgrade upload-artifact to v2 due to v3 bug

b4c88a3 first commit
```


ログが見える

こういう時のためにコメントをつけておくんだと初めて知った

### 履歴を消して元に戻す

一例として*179a27e vault backup: 2025-05-17 12:54:02*に戻りたい場合

```
git reset --hard 179a27e
git push -f origin main

```

* --hard は作業中の変更も消える

