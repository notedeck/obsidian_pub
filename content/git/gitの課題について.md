---
created: 2025-07-02T21:28
updated: 2025-07-03T07:22
---
## 目的
- **開発用リポジトリ（developer）** で機能を作成
- **管理用リポジトリ（maintainer）** でレビュー＆マージ
- プルリクエスト作成時に「履歴を直線で残す」か「マージコミットを残す」かを使い分ける
- **リベースで最新の main に追いつくパターンを実践する**

## 初期セットアップ

### 1. リポジトリ作成と初期セットアップ

```
echo "# git" >> README.md #README.md内に# gitと追加
git init -b main 
git remote add origin <リポジトリURL>
code .
```

コミットしてプッシュする

### 2. developer 環境で作業開始

```
cd ..
git clone <リンク> <フォルダー名>　#ダウンロードしたフォルダー名を指定できる(今回はdeveloper)
cd <フォルダー名>
code .
```


## 開発・マージの手順（具体例）

### パターン1：履歴を直線で残す

#### 開発者(developer)の操作

- `a-add` ブランチ作成
- README.md に `a` を追加
- コミット＆プッシュ

```README.md
# git 

a
```



![](https://i.imgur.com/OTZFIAk.png)

#### 管理者(maitainer)の操作

- フェッチ
- マージする(一番上のチェックを必ず外すこと)
![](https://i.imgur.com/3pZqWBg.png)
- リモートブランチ削除
- main をプッシュ

![](https://i.imgur.com/7GqjP7q.png)

#### 詳細

fast-forwardでマージ
#### 開発者
```
git checkout -b a-add
echo -e "\na" >> README.md
git add README.md
git commit -m "aを追加"
git push origin a-add #リモートリポジトリにa-addブランチを追加
```
#### 管理者

```
git fetch
git merge --ff a-add
git push --delete origin a-add
```

### パターン2：マージコミットを残す

#### 開発者の操作

- フェッチ(prune)
- `b-add` ブランチ作成
- README.md に `b` を追加
- コミット＆プッシュ


```README.md
# git 

a
b
```


![](https://i.imgur.com/t8uSpCe.png)

#### 管理者の操作

- フェッチ
- マージする(**「マージコミットを作成」のチェックを入れる**)
![](https://i.imgur.com/4AMWPSU.png)
- リモートブランチ削除
- main をプッシュ

![](https://i.imgur.com/V0RCoCH.png)

#### 詳細

non fast-forwardでマージ

```
git fetch prune
git checkout -b b-add
echo "b" >> README.md
git add README.md
git commit -m "bを追加"
git push origin b-add
```

```
git fetch
git merge --no-ff a-add
git push --delete origin b-add
```

### パターン3：複数ファイル追加

#### 開発者の操作

- フェッチ(prune)
- `add-test.txt` ブランチ作成
- `test.txt` ファイルに `c` を追加
- コミット＆プッシュ

```test.txt
c
```

- add-test2.txt ブランチ作成
- `test2.txt` ファイルに `c` を追加
- コミットのみする(プッシュはしない)

```test2.txt
c
```

![](https://i.imgur.com/Np0nnOB.png)

#### 管理者の操作
- フェッチ
- マージする(**「マージコミットを作成」のチェックを入れる**)
- リモートブランチ削除
- main をプッシュ


![](https://i.imgur.com/aTs1Vq1.png)

#### 開発者の操作
* フェッチする
* add-test2に移動する
* `add-test2.txt` を main に対して rebase

##### rebase前

![](https://i.imgur.com/eOHe73u.png)


##### rebase後

![](https://i.imgur.com/t5UVBzo.png)

*  add-test2をプッシュする
#### 管理者の操作

- フェッチ
- マージする(**「マージコミットを作成」のチェックを入れる**)
- リモートブランチ削除
- main をプッシュ


![](https://i.imgur.com/wrgKbho.png)
