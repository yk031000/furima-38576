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
| birthday           | date        | null: false               |
| last_name          | string      | null: false               |
| first_name         | string      | null: false               |
| last_name_kana     | string      | null: false               |
| first_name_kana    | string      | null: false               |


### Association

- has_many :items
- has_many :records


## items テーブル

| Column             | Type        | Options                        |
| --------------     | ----------- | ------------------------------ |
| name               | string      | null: false                    |
| text               | text        | null: false                    |
| status_id          | integer     | null: false                    |
| category_id        | integer     | null: false                    |
| delivery_charge_id | integer     | null: false                    |
| ship_region_id     | integer     | null: false                    |
| ship_date_id       | integer     | null: false                    |
| price              | integer     | null: false                    |


### Association

- has_one :record
- belongs_to :user

## records テーブル

| Column     | Type        | Options                        |
| ---------- | ----------- | ------------------------------ |
| user       | references  | null: false, foreign_key: true |
| item       | references  | null: false, foreign_key: true |


### Association

- belongs_to :user
- belongs_to :item
- has_one :customer

## customers テーブル

| Column     | Type       | Options                       |
| ---------- | ---------- | ----------------------------- |
| postcode   | string     | null:false                    |
| region     | string     | null:false                    |
| city       | string     | null:false                    |
| address    | string     | null:false                    |
| building   | string     |                               |
| telephone  | string     | null:false                    |
| record     | references | null:false, foreign_key: true |


### Association

- belongs_to :record