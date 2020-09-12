# kojin-app DB設計

## usersテーブル
|Colum|Type|Option|
|-----|----|------|
|name|string|null: false|
|email|string|null: false|
|password|null:| false|
### Association
- has_many :users_groups
- has_many :groups,  through:  :users_groups
- has_many :tweets
- has_many :comments
- has_many :messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users_groups
- has_many :users,  through:  :users_groups
- has_many :messages

## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has many :comments

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :tweets

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group



