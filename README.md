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

テーブル設計

## users テーブル

| Column             | Type    | Options                   |
| ------------------ | --------| ------------------------- |
| email              | string  | null: false, unique: true |
| encrypted_password | string  | null: false               |
| store              | string  | null: false               |
| full_name          | string  | null: false               |
| full_name_kana     | string  | null: false               |

### Association

- has_many :items
- has_many :orders


## itemsテーブル
| Column                 | Type       | Options                        |
| ---------------------- | -----------| ------------------------------ |
| product                | string     | null: false                    |
| user                   | reference  | null: false, foreign_key: true |
| description            | text       | null: false                    |
| states                 | test       | null: false                    |
| shipping_fee_id        | integer    | null: false                    |
| region_id              | integer    | null: false                    |
| eta_id                 | integer    | null: false                    |
| price                  | integer    | null: false                    |

### Association

- has_one :order
- belongs_to :user


## orders テーブル

| Column  | Type     | Options                       |
| --------| -------- | ----------------------------- |
| user    | reference| null:false, foreign_key: true |
| item    | reference| null:false, foreign_key: true |


### Association

- belongs_to :user
- belongs_to :item
- has_one :address

## addresses テーブル

| Column           | Type       | Options                       |
| -----------------| ---------- | ----------------------------- |
| zip              | string     | null: false                   |
| region_id        | integer    | null: false                   |
| city             | string     | null: false                   |
| address          | string     | null: false                   |
| building         | string     | null: false                   |
| phone            | integer    | null: false                   |
| order            | reference  | null:false, foreign_key: true |

- belongs_to :order