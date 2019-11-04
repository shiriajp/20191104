# Gitで色々(Gitリポジトリ作成～Pullまで)

## 1. お試しプロジェクト作成(typescipt実行まで)

環境作成
```
mkdir -p work_dir

npm init -y

npm install typescript ts-node

npm run tsc -- --init

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
>node_modules/
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