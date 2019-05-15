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

#DB設計

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|


### Association
- has_many :users, through: : group_users
- has_many :masseges
- has_many :group_users



##  usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|name|string|null: false, index: true|
|password|string|null: false|


### Association
- has_many :groups, through: :group_users
- has_many :masseges
- has_many :group_users



##  massagesテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|
|image|string|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
|timestamp|

### Association
- belogns_to :user
- belongs_to :group



##  group_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belogns_to :user
- belongs_to :group
