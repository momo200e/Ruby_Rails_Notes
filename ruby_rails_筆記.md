# ruby_rails_筆記
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
