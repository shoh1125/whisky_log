# アプリケーション名	
Whisky LOG
# アプリケーション概要
ウイスキーの感想やおすすめの飲み方などレビューを投稿し、シェアできる。
# URL
*鋭意制作中です。
# テスト用アカウント	
- メールアドレス：test1@test.com  
- パスワード：testtest1
# 利用方法	
1.トップページ（一覧ページ）のヘッダーからユーザー新規登録を行う。  
2.ウイスキー投稿ボタンから、ウイスキーの内容（名前・説明・ウイスキーの種類・国・地域・価格帯）を入力し投稿する。  
3.ウイスキー詳細ページから、レビューの内容（タイトル・レビュー本文・飲み方・合うおつまみ）を入力し投稿する。  
4.ウイスキー詳細ページから、蒸留所の内容（蒸留所の概要）を入力し投稿する。  
5.ウイスキー詳細ページから、タグ付けを行う。  

# アプリケーションを作成した背景
自分の趣味であるウイスキーをネット上で検索していると、個人やお店のブログ記事が主な情報収集源となっており、知らないウイスキーを知れる機会がそれほど多くないことに気がついた。「ウイスキーを詳細に、かつ一覧で表現できる場がない」ことが真因であると仮説を立てた。膨大な種類があるウイスキーの特徴を簡単に情報収集でき、新たなウイスキーに出会える機会を増やし、苦手なウイスキーを誤って購入しないようにしたいと考え、アプリケーションを開発することにした。
# 洗い出した要件
[要件定義_WHISKY LOG](https://docs.google.com/spreadsheets/d/1BSuU7G0e_jjpQ7l9BhHZBtMpmZQ0W1za_axvA6ZOQP0/edit#gid=982722306)
# 実装した機能についての画像やGIFおよびその説明
*鋭意制作中です。
# 実装予定の機能

# データベース設計
[![Image from Gyazo](https://i.gyazo.com/2ca74166c9a77265576e614dbc46c9e8.png)](https://gyazo.com/2ca74166c9a77265576e614dbc46c9e8)
# 画面遷移図
[![Image from Gyazo](https://i.gyazo.com/537317dd6faa900ade3175d9f9b3f5b5.png)](https://gyazo.com/537317dd6faa900ade3175d9f9b3f5b5)
# 開発環境
- Ruby on rails 6.0.0



# ローカルでの動作方法
*鋭意制作中です。
# 工夫したポイント
*鋭意制作中です。  















# usersテーブル

| Column             | Type     | Options                  |
|--------------------|----------|--------------------------|
| nickname           | string   | null: false              |
| email              | string   | null: false  unique: true|
| encrypted_password | string   | null: false              |
| birth_date         | date     | null: false              |

### Association
- has_many :whiskies
- has_many :reviews


# whiskiesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| name               | string   | null: false                   |
| explanation        | text     | null: false                   |
| type_id            | integer  | null: false                   |
| country_id         | integer  | null: false                   |
| area_id            | integer  | null: false                   |
| price_range        | string   | null: false                   |
| user               |references| null: false,foreign_key: true |


### Association
- belongs_to :user
- has_many :reviews
- has_many :distilleries


# distilleriesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| user               |references| null: false,foreign_key: true |
| review             |references| null: false,foreign_key: true |
| distillery_name    | text     | null: false,foreign_key: true |
| distillery_text    | text     | null: false,foreign_key: true |
| distillery_text    | text     | null: false,foreign_key: true |

### Association
- has_many :whiskies

# whisky_distilleriesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| distillery         |references| null: false,foreign_key: true |
| whisky             |references| null: false,foreign_key: true |

### Association
- belongs_to :whisky
- belongs_to :distillery


# reviewsテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| user               |references| null: false,foreign_key: true |
| whisky             |references| null: false,foreign_key: true |
| title              | string   | null: false                   |
| review_text        | text     | null: false                   |
| how_to_drink       | text     | null: false                   |

### Association
- belongs_to :user
- belongs_to :whisky
- has_many :tags

# tagsテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| review             |references| null: false,foreign_key: true |
| tag_name           | string   | null: false                   |

### Association
- has_many :reviews

# review_tagsテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| review             |references| null: false,foreign_key: true |
| tag                |references| null: false,foreign_key: true |

### Association
- belongs_to :review
- belongs_to :tag
