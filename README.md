# Gitで色々(Gitリポジトリ作成～Pullまで)

## 1. お試しプロジェクト作成(typescipt実行まで)

環境作成
```
mkdir -p work_dir

npm init -y

npm install typescript ts-node

npm run tsc -- --init

```
tscconfig.jsonは色々弄れる。(npm run tsc -- --initで作成)

package.jsonを編集してTypescriptコマンドを利用できるように

tscがコンパイルコマンド

```
 "scripts": {
    "tsc": "tsc",
    "ts-node": "ts-node",
 
```

## 2. Repository 作成
GitHubへGo
https://github.com/shiriajp

右上の＋ボタンからNew Repository
- とりあえず適当な名前20191104
- パブリック
- Add ignoreとかは一旦なし

CreateしたらGitHubのURLをコピーしておく

## 3. ダミーメアドの設定
https://github.com/shiriajp


右上のアイコンからsetting
・Keep my email addresses private ←チェックついているか確認
・57060562+shiriajp@users.noreply.github.com をコピーしておく

## 4. とりあえず簡単なTypescript作成

helloworld.ts
```
console.log("helloworld")
```



## 5. Gitの設定（プロジェクトフォルダへ）

node_moduleがこみっとにふようなので
```
touch .gitignore

.gitignore
>node_modules/ (node_moduleは多いからいらない。お仕事とかなら環境ごと持っていくので入れる))
```
gitに反映する

```
git init
sit status
 
git config --global user.name shiriajp
git config --global user.email 57060562+shiriajp@users.noreply.github.com

shiriajp@DESKTOP-QMP86VA:~/A$ ls -l
total 12
-rw-rw-rw- 1 shiriajp shiriajp    0 Nov  4 15:57 README.md
-rw-rw-rw- 1 shiriajp shiriajp   61 Nov  4 15:41 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 15:34 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 15:34 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  334 Nov  4 15:39 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5746 Nov  4 15:41 tsconfig.json

git add .

shiriajp@DESKTOP-QMP86VA:~/A$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   .gitignore
        new file:   README.md
        new file:   helloworld.ts
        new file:   package-lock.json
        new file:   package.json
        new file:   tsconfig.json

shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ git commit -m "first commit"
[master (root-commit) c03191a] first commit
 6 files changed, 150 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
 create mode 100644 helloworld.ts
 create mode 100644 package-lock.json
 create mode 100644 package.json
 create mode 100644 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ git remote add origin https://github.com/shiriajp/20191104.git
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ git push -u origin master
Username for 'https://github.com': shiriajp
Password for 'https://shiriajp@github.com': 

```
これでGitに新規反映OK

## 6. Gitクローンして更新してみる

```
shiriajp@DESKTOP-QMP86VA:~$ mkdir -p B
shiriajp@DESKTOP-QMP86VA:~$ 
shiriajp@DESKTOP-QMP86VA:~$ git clone https://github.com/shiriajp/20191104.git
shiriajp@DESKTOP-QMP86VA:~$ cd 20191104/
shiriajp@DESKTOP-QMP86VA:~/20191104$ ls -l
total 12
-rw-rw-rw- 1 shiriajp shiriajp    0 Nov  4 16:15 README.md
-rw-rw-rw- 1 shiriajp shiriajp   61 Nov  4 16:15 helloworld.ts
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 16:15 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  334 Nov  4 16:15 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5746 Nov  4 16:15 tsconfig.json

shiriajp@DESKTOP-QMP86VA:~/20191104$
shiriajp@DESKTOP-QMP86VA:~/20191104$
shiriajp@DESKTOP-QMP86VA:~/20191104$
```

ファイル作成

allow.ts

```
const myfunc=(arg:number)=>{

    return arg+1
}
```

Git更新
```
shiriajp@DESKTOP-QMP86VA:~/A$ git add .
shiriajp@DESKTOP-QMP86VA:~/A$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   .gitignore
        new file:   arrow.ts
        modified:   helloworld.ts
        modified:   package.json
        modified:   tsconfig.json

shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ git commit -m "add arrow.ts"
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ git push
Username for 'https://github.com': shiriajp     
Password for 'https://shir@github.com': 
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/shiriajp/20191104.git/'


```

更新した分をDL
```
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ cd ../20191104/
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ ls -la
total 12
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:16 .
drwxr-xr-x 1 shiriajp shiriajp  512 Nov  4 16:15 ..
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:18 .git
-rw-rw-rw- 1 shiriajp shiriajp   14 Nov  4 16:15 .gitignore
-rw-rw-rw- 1 shiriajp shiriajp    0 Nov  4 16:15 README.md
-rw-rw-rw- 1 shiriajp shiriajp   61 Nov  4 16:15 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:16 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 16:15 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  336 Nov  4 16:16 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5746 Nov  4 16:15 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git pull
```

## 7. その他 gitとか

git chekout . で変更全部破棄

下の例は npm install時点で、ファイルの中身は結果的に変わってないけど、オブジェクトやら色々別物なのでDiffが出てる。

```
shiriajp@DESKTOP-QMP86VA:~/20191104$ npm install
npm WARN A@1.0.0 No description
npm WARN A@1.0.0 No repository field.

audited 9 packages in 0.97s
found 0 vulnerabilities

shiriajp@DESKTOP-QMP86VA:~/20191104$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   package.json

no changes added to commit (use "git add" and/or "git commit -a")
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git diff
diff --git a/package.json b/package.json
index c753598..78479b8 100644
--- a/package.json
+++ b/package.json
@@ -4,8 +4,8 @@
   "description": "",
   "main": "index.js",
   "scripts": {
-    "tsc":"tsc",
-    "ts-node":"ts-node",
+    "tsc": "tsc",
+    "ts-node": "ts-node",
     "build": "npm run tsc",
     "test": "echo \"Error: no test specified\" && exit 1"
   },
shiriajp@DESKTOP-QMP86VA:~/20191104$ git checkout .
shiriajp@DESKTOP-QMP86VA:~/20191104$ ls -l
total 16
-rw-rw-rw- 1 shiriajp shiriajp    0 Nov  4 16:15 README.md
-rw-rw-rw- 1 shiriajp shiriajp  138 Nov  4 16:22 arrow.ts
-rw-rw-rw- 1 shiriajp shiriajp  484 Nov  4 16:22 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:16 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 16:15 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  362 Nov  4 16:23 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5749 Nov  4 16:22 tsconfig.json

```

## 8. （最後に）このReadmeをPushした履歴...この書き込みもこのあとPUSH
更新の流れ
```
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ ls -l
total 16
-rw-rw-rw- 1 shiriajp shiriajp    0 Nov  4 15:57 README.md
-rw-rw-rw- 1 shiriajp shiriajp  309 Nov  4 16:32 arrow.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:12 build
-rw-rw-rw- 1 shiriajp shiriajp  484 Nov  4 16:19 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 15:34 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 15:34 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  364 Nov  4 16:25 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5751 Nov  4 16:33 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/A$ cd ../20191104/
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ ls -l
total 16
-rw-rw-rw- 1 shiriajp shiriajp    0 Nov  4 16:15 README.md
-rw-rw-rw- 1 shiriajp shiriajp  138 Nov  4 16:22 arrow.ts
-rw-rw-rw- 1 shiriajp shiriajp  484 Nov  4 16:22 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:16 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 16:15 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  362 Nov  4 16:23 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5749 Nov  4 16:22 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git checkout .
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ cp /mnt/c/Users/SHIRIA/Desktop/\!\!__React___/20191104/README.md ./
shiriajp@DESKTOP-QMP86VA:~/20191104$ cp /mnt/c/Users/SHIRIA/Desktop/\!\!__React___/20191104/VsCodeLiveShare.md ./
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ ls -l
total 28
-rw-rw-rw- 1 shiriajp shiriajp 7215 Nov  4 17:27 README.md
-rwxrwxrwx 1 shiriajp shiriajp  531 Nov  4 17:27 VsCodeLiveShare.md
-rw-rw-rw- 1 shiriajp shiriajp  138 Nov  4 16:22 arrow.ts
-rw-rw-rw- 1 shiriajp shiriajp  484 Nov  4 16:22 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:16 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 16:15 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  362 Nov  4 16:23 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5749 Nov  4 16:22 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/20191104$ git add *.md
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
        new file:   VsCodeLiveShare.md

shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git commit -m 'Add .md file'
[master 61dc382] Add .md file
 2 files changed, 260 insertions(+)
 create mode 100755 VsCodeLiveShare.md
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ git push
Username for 'https://github.com': shirajp
Password for 'https://shirajp@github.com': 
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/shiriajp/20191104.git/'
shiriajp@DESKTOP-QMP86VA:~/20191104$ git push
Username for 'https://github.com': shiriajp
Password for 'https://shiriajp@github.com': 
Counting objects: 4, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 2.80 KiB | 1.40 MiB/s, done.
Total 4 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/shiriajp/20191104.git
   4405225..61dc382  master -> master
shiriajp@DESKTOP-QMP86VA:~/20191104$ ls -la
total 28
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 17:27 .
drwxr-xr-x 1 shiriajp shiriajp  512 Nov  4 16:15 ..
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 17:28 .git
-rw-rw-rw- 1 shiriajp shiriajp   20 Nov  4 16:22 .gitignore
-rw-rw-rw- 1 shiriajp shiriajp 7215 Nov  4 17:27 README.md
-rwxrwxrwx 1 shiriajp shiriajp  531 Nov  4 17:27 VsCodeLiveShare.md
-rw-rw-rw- 1 shiriajp shiriajp  138 Nov  4 16:22 arrow.ts
-rw-rw-rw- 1 shiriajp shiriajp  484 Nov  4 16:22 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:16 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 16:15 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  362 Nov  4 16:23 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5749 Nov  4 16:22 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/20191104$ 
shiriajp@DESKTOP-QMP86VA:~/20191104$ cd ../A
shiriajp@DESKTOP-QMP86VA:~/A$ 
shiriajp@DESKTOP-QMP86VA:~/A$ git pull
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 1), reused 4 (delta 1), pack-reused 0
Unpacking objects: 100% (4/4), done.
From https://github.com/shiriajp/20191104
   4405225..61dc382  master     -> origin/master
Updating 4405225..61dc382
Fast-forward
 README.md          | 245 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 VsCodeLiveShare.md |  15 +++++++++++++
 2 files changed, 260 insertions(+)
 create mode 100755 VsCodeLiveShare.md
shiriajp@DESKTOP-QMP86VA:~/A$ ls -la
total 28
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 17:28 .
drwxr-xr-x 1 shiriajp shiriajp  512 Nov  4 16:15 ..
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 17:28 .git
-rw-rw-rw- 1 shiriajp shiriajp   20 Nov  4 16:13 .gitignore
-rw-rw-rw- 1 shiriajp shiriajp 7215 Nov  4 17:28 README.md
-rwxrwxrwx 1 shiriajp shiriajp  531 Nov  4 17:28 VsCodeLiveShare.md
-rw-rw-rw- 1 shiriajp shiriajp  309 Nov  4 16:32 arrow.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 16:12 build
-rw-rw-rw- 1 shiriajp shiriajp  484 Nov  4 16:19 helloworld.ts
drwxrwxrwx 1 shiriajp shiriajp  512 Nov  4 15:34 node_modules
-rw-rw-rw- 1 shiriajp shiriajp 2601 Nov  4 15:34 package-lock.json
-rw-rw-rw- 1 shiriajp shiriajp  364 Nov  4 16:25 package.json
-rw-rw-rw- 1 shiriajp shiriajp 5751 Nov  4 16:33 tsconfig.json
shiriajp@DESKTOP-QMP86VA:~/A$ 
```
