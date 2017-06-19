# Git 基本指令筆記


### 安裝


### 設定

* 基本資料設定
  * Username: `git config --global user.name "Your Name"`
  * User Email: `git config --global user.email "you@example.com"`


## 指令

* 初始化：`git init`
 
* 狀態檢查：`git status`

  > 看看有哪些檔案有更動（增、刪與改），卻還沒被快照的

  在剛剛那個資料下 `git status` 指令會看到：
  ```
  On branch master

  Initial commit

  Untracked files:
    (use "git add <file>..." to include in what will be committed)

          readme.md

  nothing added to commit but untracked files present (use "git add" to track)
  ```
  由上面可以看到 file1.py 這個檔案沒有被選定要進行快照

* 將檔案加入快照名單：`git add <filename>`

  > 將 `<filename>` 替換成你的檔案名稱

  在剛剛的 git_test 資料夾下：`git add file1.py`  
  然後我們在下一次 `git status` 看看狀態的改變，會看到：
  ```
  On branch master

  Initial commit

  Changes to be committed:
    (use "git rm --cached <file>..." to unstage)

          new file:   file1.py

  ```
  由上可以看到 readme.md 這個檔案已經被選取進快照名單了

  > 小技巧
  > `git add .`: add 所有的檔案
  > `git add -u`: add 所有更新或刪除的檔案（不包含新增的檔案）

* 快照：`git commit`  
  在將檔案加入快照的名單後就可以對檔案進行快照了  
  有兩種模式：
    1. 一行：`git commit -m "<write something here>"`
       > 將 <write something here> 取代成你想要在快照上寫的註解
       > 記得要寫點有意義的東西如果亂寫就不能一目了然到底改了哪些囉～

    2. 開啟編輯器：`git commit -a`
       > 上面這行指令會開啟你的編輯器，讓你在你的編輯器中編輯你的註解

  如果不小心寫錯註解了也不要緊張下 `git commit --amend` 來編輯你最近一次快照的註解

  在剛剛的資料夾下 `git commit -m "first commit"` 就會新增一次快照了  
  可以在下一次 `git status` 看一下狀態的改變，應該會看到：
  ```
  On branch master
  nothing to commit, working tree clean
  ```
  耶～所有檔案都加入快照了

* 看快照註解：`git log`  
  在剛剛的資料夾下 `git log` 可以看到你剛剛建立為快照建立的註解  
  是說畫面看起來真的有點醜，而且剛 commit 很多的時候會不方便檢視  
  所以還記得剛剛設定的 lg 指令嗎？  
  試試看，會看到比較棒的輸出唷～

> 更新一下檔案試著新增一下幾個版本的快照（下面是我做的，下面會用這個來做）
>
> 在剛剛的 readme.md 中加入一行東西（隨便你加）
> new.rb 檔案內容
> ```ruby
> # new.rb
>
> puts "安安大家好"
> ```
> 然後快照一下
> ```
> git add new.rb
> git commit -m "add puts hello"
> ```
> 最後 lg 一下：
> ```
> * 4df3c07 - (HEAD -> master) add puts hello (3 seconds ago) <Arthur Chang>
> * 262d478 - first commit (12 minutes ago) <Arthur Chang>
> ```

* `git checkout` 指令
  * 還原到最新的快照  
    比方說我在 new.rb 中隨便在一點東西（亂打），然後下 `git checkout -- new.rb`，這樣 new.rb 就會變回：
    ```ruby
    # new.rb

    puts "安安大家好"
    ```
  * 切換到某版本看看：`git checkout <版本號>`
    * 指令 `git lg` 列出所有的版本
    * 選擇想要看的版本號然後下 `git checkout <版本號>`，在打開檔案就會看到那時候的檔案樣子了
    * 要回到最新的狀態就下 `git checkout master`  
      P.S. 不要在這時候更動檔案，如果要更動記得建立分支

  * 建立新的分支 `git checkout -b <分支名稱>`

  * 切換到現有分支 `git checkout <分支名稱>`

* `git merge` 分支合併
  * `git merge <分支名稱>`：將 `<分支名稱>` 合併到現在的分支

* `git push`
  * 將更新的東西推到遠端

* `git fetch`
  * 將遠端的更新拉到本地端

* `git pull`
  * 將遠端的更新拉到本地端，並合並 (git fetch + git merge)

* `git diff <filename>`
  * 顯示目前工作區的檔案（尚未 commit ）與最後一次的 commit 有什麼差異

* `git show <filename>`
  * 顯示最後一次 commit 與倒數第二次的 commit 有什麼差異

* `git blame <filename>`
  * 顯示某一行是誰修改的
