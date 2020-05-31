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


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|user|text|null: false|
|email|text|null: false, add_index:user,:email,unique|
|password|text|null: false|
|groups_id|integer|null: false,foreign_key: true|



### Association
- has_many :groups_users
- has_many :groups, dependent: :destroy, through:groups_users
- has_many :masseages,  dependent: :destroy



## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|text|null: false|
|users_id|integer|null: false, foreign_key: true|



### Association
- has_many :groups_users
- has_many :users, through:groups_users
- belongs_to :masseages ,dependent: :destroy




## masseagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|text||
|groups_id|integer|foreign_key: true|
|users_id|integer|foreign_key: true|


### Association
- belongs_to :groups
- belongs_to :users


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :groups
- belongs_to :users