# Ruby on Rails學習日誌 #一些好用的Gem
- [Bootstrap-sass](#bootstrap-sass)
    - [畫面美化(常用class)](#畫面美化)
- [Simple_form](#simple_form)
- [Devise使用者功能(會員機制)](#devise會員機制)
- [Cancancan](#cancancan)
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

### 畫面美化
**畫面內容**
```ruby
#layouts/application.html.erb
<div class="container">
<%= yield %>  
</div>
```
用`<div class="container">`包著內文

**表格美化**
表格標籤加上`class="table"`
```ruby
#student/index.html.erb
<h1>成績列表</h1>

<%= link_to '新增學生', new_student_path, class:"btn btn-success"  %>


<table class="table">
  <thead>
    <tr>
      <th>姓名</th>
      <th>學號</th>
      <th>分數</th>
      <th>處理</th>
      <th colspan="3"></th>
    </tr>
  </thead>

  <tbody>
    <% @students.each do |student| %>
      <tr>
        <td><%= student.name %></td>
        <td><%= student.student_id %></td>
        <td><%= student.grade %></td>
        <td><%= link_to '編輯', edit_student_path(student), class:"btn btn-primary"  %></td>
        <td><%= link_to '刪除', student, method: :delete, data: { confirm: 'Are you sure?' }, class:"btn btn-danger" %></td>
      </tr>
    <% end %>
  </tbody>
</table>

<br>

```
**按鈕美化**
- 綠色按鈕加上`class:"btn btn-success"`
- 藍色按鈕加上`class:"btn btn-primary"`
- 紅色按鈕加上`class:"btn btn-danger"`


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
 
##### 當有使用bootstrap
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



## Cancancan
Cancancan是一個角色管理權限的套件，配合Devise一起使用可以快速的長出完整的會員管理機制

### 在RAILS上的安裝方法
#### Step.1 加入Bootstrap
 ```ruby
# 先在gemfile裡面輸入
gem 'cancancan', '~> 1.10'
 ```
並在終端機執行`bundle install`
#### Step.2 加入專案
接下來執行`rails g cancan:ability`，你就會得到一個`aibility.rb`

**全部的權限都可以放在裡面太方便啦~~~~ OAO**


#### Step.3 cancancan的應用
  ```ruby
# aibility.rb
user ||= User.new
if user.staff?
 can :manage, :all
else
 can :read, :all
end
```
其中`can :manage, :all`意思是此使用者，擁有所有資料的變更權限

`can :read, :all`意思是此使用者，只能讀資料



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
