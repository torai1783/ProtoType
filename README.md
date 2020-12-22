# 開発要件

## appname
- 

## ペルソナ
- 性別：問わない
- 職業：問わない
- 趣味：サブカルチャー、アート観賞、変わった物が好き、アニメ・漫画、ゲーム
- 日頃の生活：学生、社会人

## アプリケーション概要
- 因幡都頼による作品を素材にしたゲームをプラットフォームに、「実際の作品を見てみたい。」と感じさせ展示会などに足を運んでもらう。
- artに興味を持ってもらうための導入としてゲーム性のあるアプリケーションを作成する。

## URL
-

## テストアカウント
-

## 利用方法
- 

## 目指した課題解決
- artをもっと身近にする。

## 洗い出した要件
-

## 機能についてのGIFと説明
-
-

## 実装予定の機能
-
-

## ローカルでの動作方法
-


# テーブル設計

## users テーブル

| Column             | Type   | Option                    |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| family_name_jp     | string | null: false               |
| first_name_jp      | string | null: false               |
| family_name_kana   | string | null: false               |
| first_name_kana    | string | null: false               |
| birthday           | date   | null: false               |


family_name_kana
first_name_kana

### Association
- has_many :items
- has_many :users_items

## items テーブル

| Column             | Type      | Option            |
| -----------------  | --------- | ----------------- |
| user               | reference | foreign_key: true |
| name               | string    | null: false       |
| price              | integer   | null: false       |
| description        | text      | null: false       |
| category_id        | integer   | null: false       |
| status_id          | integer   | null: false       |
| charges_id         | integer   | null: false       |
| deliverysource_id  | integer   | null: false       |
| deliverydays_id    | integer   | null: false       |

### Association

- has_one :users_item
- belongs_to :user

## users_items　テーブル

| Column  | Type      | Option            |
| ------- | --------- | ----------------- |
| user    | reference | foreign_key: true |
| item    | reference | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item

## address　テーブル

| Column            | Type       | Option            |
| ----------------  |----------- | ----------------- |
| users_item        | reference  | foreign_key: true |
| postalcood        | string     | null: false       |
| deliverysource_id | integer    | null: false       |
| city              | string     | null: false       |
| address           | string     | null: false       |
| tel               | string     | null: false       |
| building          | string     |                   |

### Association

- belongs_to :users_item


