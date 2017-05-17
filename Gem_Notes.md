# Ruby on Rails學習日誌 #一些好用的Gem

## Bootstrap
Bootstrap是一個網頁樣式框架，提供許多CSS樣式功能強化網頁前端的表現能力

### 在RAILS上的安裝方法
#### Step.1 加入Bootstrap
 ```ruby
# 先在gemfile裡面輸入

gem 'bootstrap-sass'

#並在終端機執行bundle install
 ```
#### Step.2 修改js
 ```ruby
# 在application.js加入
//= require bootstrap
 ```
#### Step.3 修改scss
  ```ruby
# 把application.css檔名改成 application.scss，加入
@import "bootstrap-sprockets";
@import "bootstrap";
 ```
*  注意：刪除所有的*= require_self和*= require_tree .語法。Sass中只能使用@import導入文件  


## Awesome_print
awesome_print是一個可以將Ruby的console輸出排版好看一點的外掛，如果你受不了擠在一起的排版，可以試試看這個套件喔。

### 在RAILS上的安裝方法
 ```ruby
# 在gemfile裡面輸入

gem 'awesome_print'

#並在終端機執行bundle install
 ```
### 使用方式
在Rails Console下，需要印出複雜的格式，只要在程式碼前加上'ap'即可
 ```ruby
ap Post.all
 ```
