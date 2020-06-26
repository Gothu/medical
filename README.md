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

# DB設計

##  usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :posts

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|content|string||
### Association
- belongs_to :user
- has_many :checks, through: :posts_checks

## checksテーブル
|Column|Type|Options|
|------|----|-------|
|name|string||
### Association
- has_many :posts, through: :posts_checks

## posts_checksテーブル
|Column|Type|Options|
|------|----|-------|
|post_id|integer|null: false, foreign_key: true|
|check_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :post
- belongs_to :check