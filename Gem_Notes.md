# Ruby on Rails學習日誌 #一些好用的Gem
- [Bootstrap-sass](#bootstrap-sass)
- [Simple_form](#simple_form)
- [Devise使用者功能(會員機制)](#Devise)
- [Kaminari-分頁](#kaminari)
- [Bootstrap-Kaminari-Views-分頁樣式](#bootstrap-kaminari-views)
- [Awesome_print](#awesome_print)

## Bootstrap-sass
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

## Simple_form
Simple_form是一個表單快速生成框架，搭配bootstrap非常的強大XD

### 在RAILS上的安裝方法
#### Step.1 加入Simple_form
 ```ruby
# 先在gemfile裡面輸入

gem 'simple_form'
 ```
 並在終端機執行`bundle install`
 
#### Step.2 安裝生成Simple_form
##### 正常情況
```ruby
rails generate simple_form:install
 ```
 
##### 使用bootstrap
```ruby
rails generate simple_form:install --bootstrap
 ```



## Devise會員機制
有了Devise，實作使用者機制變成一件再容易不過的事

### 在RAILS上的安裝方法
#### Step.1 加入Bootstrap
 ```ruby
# Gemfile
gem 'devise'
 ```
並在終端機執行`bundle install`
#### Step.2 設定 Devise
 ```ruby
rails g devise:install
 ```
#### Step.3 建立使用者
```ruby
rails g devise user
 ```
 Devise非常的聰明，在這邊幫我們建立了model當作會員資料表，幫我們把相關設定都做好了，只需要一行指令 =V=
 (名稱當然不用是`user`)
 
 記得執行`rails db:migrate`，再重啟server

#### Step.4 Devise的應用-routes


## Kaminari
Kaminari是一個分頁的套件

### 在RAILS上的安裝方法
#### Step.1 加入Kaminari
 ```ruby
# 先在gemfile裡面輸入

gem 'kaminari'

#並在終端機執行bundle install
 ```
### 使用方式
#### Step.1 在controllers/xxxx_controller.rb 中，修改index的方法
 ```ruby
def index
  @books = Book.page(params[:page]).per(3)
end
 ```
#### Step.2 在views/xxxx/index.html.erb，畫面中加入分頁
 ```ruby
<%= paginate @books  %>
```


## Bootstrap-Kaminari-Views
一個分頁的樣式

### 在RAILS上的安裝方法
#### Step.1 加入Bootstrap-Kaminari
 ```ruby
# 先在gemfile裡面輸入

gem 'bootstrap-kaminari-views'

#並在終端機執行bundle install
 ```
### 使用方式
#### 修改分頁的語法
 ```ruby
<%= paginate @namecards ,:theme => 'twitter-bootstrap-3' %>
 ```


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
