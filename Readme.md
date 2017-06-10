# Ruby on Rails學習日誌 

剛開始接觸Ruby時覺得非常的有趣，與php有著顯著的差異，更重要的是他有強大的rails框架讓開發速度更快了!
引起了我非常大的興趣，上過龍哥的課後決定要好好鑽研，並想以用部落格的方式，記錄下學到的新的東西


由於之前都沒寫過部落格，但是覺得常常很多東西用過後還是容易忘記，所以想把學到的新知識經過自己整理出來，除了讓自己加強印象，整理出來的筆記也可以和大家分享:)


## 第一站 rails框架及MVC
雖然之前PHP已經接觸過MVC的框架了~
可是還是有差異，有許多有趣的資料夾
我將資料夾名稱及用途整理了出來~

檔案/目錄 | 用途
-|-
app|放置 Rails 一些 MVC架構的目錄，底下會有 Controllers、models 和 views 目錄。
config/	|整個專案的運作設定檔、網址列的路由規則、資料庫帳號密碼的設定等等。
db/	|資料庫的結構概要，未來在多人開發的資料庫編修方面，在這裡就會變得很重要。
doc/	|說明文件放置處。
lib/	|若有自定的 Module 和類別檔案，放在這裡可以讓每個 controller 都用得到，不必再另外指定路徑 include file。
log/	|應用程式記錄檔。
public/	|圖檔、JavaScript、CSS 和其他靜態檔案擺放的地方。
script/	|執行 Rails 的指令。
test/	|用來執行臨時測試一些邏輯資料並不影響專案運行。
tmp/	|放置暫時性的檔案。
vendor/	|存放第三方外掛的目錄。
Gemfile	|設定 Rails 運作時會使用哪些 Gems 套件，用 bundle install 會依照裡頭的設置來安裝套件。
README	|讀我檔，一般簡要的說明安裝方法。
Rakefile	|載入一些 Rake 自動化處理的任務。
config.ru	|啟動伺服器設定。

#### 我們會常用到的部分有：
* Gemfile      
新增／移除／調整gem與其版本
* config/routes      
用來設定本專案的子網址會連到哪裡
* db/      
資料庫裡各個Class的設定檔
* app/      
我們專案裡要做的程式 90%都會放在這裡
* app/models/      
放置MVC中的 Model 的地方, 主要做Class歸屬與資料驗證等設定
* app/views/      
放置MVC中的 View 的地方, 所有要讓瀏覽器使用者看到的html碼都在這
* app/controllers/      
放置MVC中的 Controller 的地方, 所有action動作都在這設定
* app/assets/      
裡面有三個資料夾: images, javascripts, stylesheets
顧名思義就是放置靜態檔案: 圖片, .js, .css檔的地方
