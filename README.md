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

# テーブル設計

## users テーブル

| Column             | Type        | Options                   |
| ------------------ | ----------- | ------------------------- |
| nickname           | string      | null: false               | 
| email              | string      | null: false, unique: true |
| encrypted_password | string      | null: false               | 

### Association

- has_many :items
- has_many :record


## items テーブル

| Column    | Type        | Options           |
| --------- | ----------- | ----------------- |
| image     | string      | null: false       |
| name      | string      | null: false       |
| text      | text        | null: false       |
| state     | text        | null: false       |
| category  | string      | null: false       |
| price     | integer     | null: false       |
| users_id  | references  | foreign_key: true |

### Association

- has_one :record
- belongs_to :users

## record テーブル

| Column     | Type        | Options           |
| ---------- | ----------- | ----------------- |
| user_id    | references  | foreign_key: true |
| items_id   | references  | foreign_key: true |


### Association

- belongs_to :users
- belongs_to :item
- has_one :address

## customers テーブル

| Column     | Type       | Options           |
| ---------- | ---------- | ----------------- |
| postcode   | integer    | null:false        |
| region     | string     | null:false        |
| city       | string     | null:false        |
| address    | integer    | null:false        |
| building   | string     |                   |
| telephone  | integer    | null:false        |
| record_id  | references | foreign_key: true |


### Association

- belongs_to :record