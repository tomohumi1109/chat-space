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

##  groupsテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|
|name|string|null: false, index: true|


### Association
- has_many :users
- has_many :masseges
- has_many :group_users



##  usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|
|email|string|null: false, unique: true|
|name|string|null: false, index: true|
|password|string|null: false|


### Association
- has_many :groups
- has_many :masseges
- has_many :group_users



##  massagesテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|
|text|text|
|image|string|
|user_id|reference|foreign_key: true||
|group_id|reference|foreign_key: true||
|timestamp|

### Association
- belogns_to :user
- belongs_to :group



##  group_usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer||
|user_id|reference|foreign_key: true||
|group_id|reference|foreign_key: true||

### Association
- belogns_to :user
- belongs_to :group
