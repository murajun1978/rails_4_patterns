# Rails4 Patterns

I18n
---
多言語対応するときのアレ

- 基本形
  - I18n.t('posts.index.title') 

  * ViewとActionが同じ場合は省略できる
    ```ruby
    # config/locales/ja.yml
    ja:
      posts:                         # controller名
        index:                       # action名
          title: 'タイトル' 

    # views/posts/index.html.haml
    %table
      %thaed
        %tr
          %th= t('.title')
      %tbody 
   ```

- ページタイトル
  ```ruby
  # config/locales/ja.yml
  ja:
    posts:                         # controller名
      index:                       # action名
        page_title: 'Post index'
        title:           'タイトル'

  # views/layouts/application.html.haml
  !!!
    %html
      %head
        %title= yield :page_title
  [...]

  # views/posts/index.html.haml
  = content_for(:page_title) { t('.page_title') }
  ``` 
