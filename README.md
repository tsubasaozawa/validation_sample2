# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# 作成手順
①モデルにバリデーションを設定  
②helpersディレクトリに任意のhelperファイル（今回だと、form_helper.rb）を作成  
③ビュー側（今回だと_form.html.haml）に以下の記述を追加  
・form_with → 「:builder => FormHelper::CustomFormHelper)」  
④エラーメッセージを日本語化するため、config/localesにja.ymlを作成し、日本語化したい情報を追加  
今回は基本的な内容に加えて以下の内容を追加  
  attributes:  
      post: # モデル名  
        title: # カラム名  
        content: # カラム名  
        image: # カラム名  
⑤confing/application.rbに以下の記述を追加  
  config.i18n.default_locale = :ja # ja.ymlファイルの読み込み  
  config.action_view.field_error_proc = Proc.new { |html_tag, instance| html_tag } #エラーメッセージによるレイアウト崩れを防ぐ  
⑥必要に応じて該当classもしくはIDにCSSを設定  