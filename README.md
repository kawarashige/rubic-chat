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

# アプリケーション名

## Rubic Chat

# アプリケーション概要

## ルービックキューブを趣味として習慣化することができるようになります。

# heroku URL
## https://rubic-chat.herokuapp.com/

# 目指した課題解決

## ルービックキューブを趣味にしたいが、長続きしないという課題をもつ人に向けて共通の趣味を持つ人とのコミュニケーションの場としてこのアプリケーションを提供することでその課題解決を図ります。

# 洗い出した要件

| 機能 | 目的 | 詳細 | ストーリー |
| --- | ---- | --- | -------- |
| ユーザー新規登録機能 | ユーザーを登録する. | 新規登録をすることでDBにユーザーの情報を保存します。 | ・プロフィールの情報、email、password、ニックネーム、年齢、趣味歴を記入する欄を設けます。 |
| ログイン機能 | ユーザーがログイン・ログアウトを行えることができるようにします。 | ユーザーがログイン・ログアウトボタンを押すことでログイン・ログアウトが行えるようになります。 | ・ログイン画面において、DBに保存されているユーザーと一致するemailとpasswordを持つユーザーにアプリケーションの全ての機能を使えることのできる権限を付与します。 |
| ログイン出席簿 | ログイン日数の情報を表示する。 | ログインした場合に日に一度スタンプを押すことができるようになり、ログイン日数を視覚化します。 | ・ログインした際その日一度だけにスタンプを押すことができ、ログイン情報を視覚化することができます。 |
| チャット機能 | ユーザー同士がチャットを行えるようにする。 | ユーザーはコメント、画像、動画を投稿できるようになります。 | ・ユーザーはコメント、画像、動画を記入・添付し「投稿する」ボタンを押すことでチャット画面上に表示することができます。 |
| メンバー一覧表示機能 | グループに属する人を一覧表示する。 | メンバーという文字をクリックすることで、グループに属するメンバー全員を表示することができる。 | ・メンバーの隣に所属している人数が表示されていて、クリックすることにより所属しているユーザーの名前が縦に羅列されます。 |
| コメントへのgoodボタン | コメントにgoodアイコンを付けられるようにする。 | ユーザーはコメント一つに対して一つまでサムアップアイコンをつけることができます。 | ・コメントについて、色のついていないサムアップボタンを押すことで色付きのサムアップアイコンになることで隣に表示されているgoodされている数を表す数字のカウントが1足されます。 |
| リサイクル物品出品機能 | リサイクルに出したい商品を出品する。 | リサイクルに出しても良い物品を出品できます。 | ・出品ページの出品するボタンを押すことで、物品を出品することができます。・購入時期/経過年数/物品の状態/物品の情報/配達元の地域/配達までの日数の記入欄を設ける。 |
| リサイクル物品表示機能 | 出品機能により出品された商品を表示する。 | 出品されている商品を表示します。 | ・出品機能によって出品された物品をリサクルページに表示することが出来ます。 |
| リサイクル物品授受機能 | 出品された物品を受け取ります。 | 出品されている商品を受け取ることができます。 | ・出品しているユーザーと物品を受け取ることの出来るユーザーは同一ではないです。・出品されている商品を選択し、詳細ページを開くことで受け取るボタンを押すことが出来ます。 |
| マイページ情報表示機能 | ユーザーの情報を表示する。 | 自分自身の情報を他のユーザーに公開することができます。 | ・自身のプロフィール、新規登録の際に入力したニックネーム・年齢・趣味歴を表示します。・他のユーザーが自身のプロフィール情報を愛知ウランすることが出来ます。 |
| 趣味調べ記入機能 | 趣味についての情報を記入する。 | 趣味について調べた内容を記入することができます。 | ・歴史/著名人/関連する情報を記入するための欄を設けます。 |
| 趣味調べ表示機能 | 趣味についての情報を表示する。 | 趣味について調べた内容を他のユーザーに表示することができます。 | ・自身が記入した趣味についての情報を他のユーザーに公開出来ます。・編集するボタンを押すことで編集することが可能になります。 |
| フォロー・フォロワー機能 | 自身が興味ある人との繋がりを生みます。 | ユーザーは、自分以外をフォローすることができ、他のユーザーをフォローした場合、フォローしたユーザーのマイページにフォロワーとして表示されます。 | ・自身以外のマイページに表示されるフォローするボタンを押すことでそのユーザーをフォローすることができます。 |

# データベース設計

## users_allテーブル

| Column      | Type    | Option                   |
| ----------- | ------- | ------------------------ |
| nickname    | string  | null: false, default: "" |
| email       | string  | null: false, default: "" |
| password    | string  | null: false, default: "" |
| years_older | integer | null: false              |
| experience  | integer | null: false              |

### Association

- has_one :home
- has_one :study
- has_many :items
- has_many :recycles
- has_many :room_all_users_all
- has_many :rooms_all, through: room_all_users_all
- has_many :messages_all
- has_many :user_a_users_all
- has_many :users_a, through: user_a_users_all
- has_many :user_b_users_all
- has_many :users_b, through: user_b_users_all
- has_many :user_c_users_all
- has_many :users_c, through: user_c_users_all

## user_a_users_allテーブル

| Column   | Type       | Option                         |
| -------- | ---------- | ------------------------------ |
| user_all | references | null: false, foreign_key: true |
| user_a   | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all
- belongs_to :user_a

## user_b_users_allテーブル

| Column   | Type       | Option                         |
| -------- | ---------- | ------------------------------ |
| user_all | references | null: false, foreign_key: true |
| user_b   | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all
- belongs_to :user_b

## user_c_users_allテーブル

| Column   | Type       | Option                         |
| -------- | ---------- | ------------------------------ |
| user_all | references | null: false, foreign_key: true |
| user_c   | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all
- belongs_to :user_c

## user_aテーブル

| Column | Type | Option |
| ------ | ---- | ------ |
|        |      |        |

### Association

- has_many :room_a_users_a
- has_many :rooms_a, through :room_a_users_a
- has_many :messages_a

## user_bテーブル

| Column | Type | Option |
| ------ | ---- | ------ |
|        |      |        |

### Association

- has_many :room_b_users_b
- has_many :rooms_b, through :room_b_users_b
- has_many :messages_b

## user_cテーブル

| Column | Type | Option |
| ------ | ---- | ------ |
|        |      |        |

### Association

- has_many :room_c_users_c
- has_many :rooms_c, through :room_c_users_c
- has_many :messages_c

## message_allテーブル

| Column      | Type       | Option                         |
| ----------- | ---------- | ------------------------------ |
| content_all | text       | null: false, default: ""       |
| user_all    | references | null: false, foreign_key: true |
| room_all    | references | null: false, foreign_key: true |

### Association

- belongs_to :room_all
- belongs_to :user_all

## message_aテーブル

| Column    | Type       | Option                         |
| --------- | ---------- | ------------------------------ |
| content_a | text       | null: false, default: ""       |
| user_a    | references | null: false, foreign_key: true |
| room_a    | references | null: false, foreign_key: true |

### Association

- belongs_to :room_a
- belongs_to :user_a

## message_bテーブル

| Column    | Type       | Option                         |
| --------- | ---------- | ------------------------------ |
| content_b | text       | null: false, default: ""       |
| user_a    | references |              foreign_key: true |
| user_b    | references | null: false, foreign_key: true |
| room_b    | references | null: false, foreign_key: true |

### Association

- belongs_to :room_b
- belongs_to :user_a
- belongs_to :user_b

## message_cテーブル

| Column    | Type       | Option                         |
| --------- | ---------- | ------------------------------ |
| content_c | text       | null: false, default: ""       |
| user_a    | references |              foreign_key: true |
| user_b    | references |              foreign_key: true |
| user_c    | references | null: false, foreign_key: true |
| room_c    | references | null: false, foreign_key: true |

### Association

- belongs_to :room_c
- belongs_to :user_a
- belongs_to :user_b
- belongs_to :user_c

## room_all_users_allテーブル

| Column | Type | Option |
| ------ | ---- | ------ |
| user_all | references | null: false, foreign_key: true |
| room_all | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all
- belongs_to :room_all

## room_a_users_aテーブル

| Column | Type       | Option                         |
| ------ | ---------- | ------------------------------ |
| user_a | references | null: false, foreign_key: true |
| room_a | references | null: false, foreign_key: true |

### Association

- belongs_to :user_a
- belongs_to :room_a

## room_b_users_bテーブル

| Column | Type       | Option                         |
| ------ | ---------- | ------------------------------ |
| user_b | references | null: false, foreign_key: true |
| room_b | references | null: false, foreign_key: true |

### Association

- belongs_to :user_b
- belongs_to :room_b

## room_c_users_cテーブル

| Column | Type       | Option                         |
| ------ | ---------- | ------------------------------ |
| user_c | references | null: false, foreign_key: true |
| room_c | references | null: false, foreign_key: true |

### Association

- belongs_to :user_c
- belongs_to :room_c

## room_allテーブル

| Column   | Type   | Option                   |
| -------- | ------ | ------------------------ |
| name_all | string | null: false, default: "" |

### Association

- has_many :room_all_users_all
- has_many :users, through :room_all_users_all
- has_many :messages_all

## room_aテーブル

| Column | Type   | Option                   |
| ------ | ------ | ------------------------ |
| name_a | string | null: false, default: "" |

### Association

- has_many :room_a_users_a
- has_many :users, through :room_a_users_a
- has_many :messages_a

## room_bテーブル

| Column | Type   | Option                   |
| ------ | ------ | ------------------------ |
| name_b | string | null: false, default: "" |

### Association

- has_many :room_b_users_b
- has_many :users, through :room_b_users_b
- has_many :messages_b

## room_cテーブル

| Column | Type   | Option                   |
| ------ | ------ | ------------------------ |
| name_c | string | null: false, default: "" |

### Association

- has_many :room_c_users_c
- has_many :users, through :room_c_users_c
- has_many :messages_c

## homesテーブル

| Column    | Type       | Option                         |
| --------- | ---------- | ------------------------------ |
| history   | text       |              default: ""       |
| celebrity | text       |              default: ""       |
| info      | text       |              default: ""       |
| user_all  | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all

## studiesテーブル

| Column   | Type       | Option                         |
| -------- | ---------- | ------------------------------ |
| user_all | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all

## itemsテーブル 

| Column         | Type       | Option                         |
| -------------- | ---------- | ------------------------------ |
| old            | integer    | null: false                    |
| item_info      | string     | null: false, default: ""       |
| item_status_id | integer    | null: false, default: 0        |
| prefecture_id  | integer    | null: false, default: 0        |
| schedule_id    | integer    | null: false, default: 0        |
| user_all       | references | null: false, foreign_key: true |


### Association

- belongs_to :user_all
- has_one :recycle

## recyclesテーブル

| Column   | Type       | Option                         |
| -------- | ---------- | ------------------------------ |
| user_all | references | null: false, foreign_key: true |
| item     | references | null: false, foreign_key: true |

### Association

- belongs_to :user_all
- belongs_to :item
- has_one :address

## addressesテーブル

| Column   | Type       | Option                              |
| ------------- | ---------- | ------------------------------ |
| postal_code   | string     | null: false, default: ""       |
| prefecture_id | integer    | null: false, default: 0        |
| city          | string     | null: false, default: ""       |
| addresses     | string     | null: false, default: ""       |
| building      | string     | null: false, default: ""       |
| phone         | string     | null: false, default: ""       |
| recycle       | references | null: false, foreign_key: true |

### Association

- belongs_to :recycle

![ER図](https://i.gyazo.com/a16541b06ae298a3b578cc06eaf565a3.png)

# ローカルリポジトリでの動作方法

% git clone https://git.heroku.com/rubic-chat.git

ruby 2.6.5