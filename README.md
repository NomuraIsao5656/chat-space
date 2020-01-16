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
## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|stringstring|null: false|


### Association
- has_many :users,  through:  :groups_users
- has_many :messages,  through:  :groups_messages
- has_many :groups_users

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
|group_id|integer||
### Association
- has_many :groups,  through:  :groups_users
- has_many :messages,  through:  :users_messages

## users_messagesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|string|null: false|
|message_id|string|null: false|
### Association
- belongs_to :message
- belongs_to :user

## groups_messagesテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|string|null: false|
|message_id|string|null: false|
### Association
- belongs_to :message
- belongs_to :group