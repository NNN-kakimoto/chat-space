# DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|
|mail_addles|string|null: false|
|password|text|null: false|

### Association
- has_many: messages
- has_many: groups, through: :group_users
- has_many: group_users


## messaggesテーブル
|Column|Type|Options|
|------|----|-------|
|text|string||
|image|text||
|user_id|references|foreign_key: true|
|group_id|references|foreign_key: true|
|timestanps|string|null: false|

### Association
- belongs_to: user
- belongs_to: group


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|

### Association
- has_many: users, thorugh: :group_users
- has_many: messages
- has_many: group_users


## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to: user
- belongs_to: group