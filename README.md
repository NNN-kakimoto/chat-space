DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|
|mail_addles|string|null: false, add_index|
|pass_word|text|null: false|

### Association
- has_many: messages
- has_many: groups, through: :members


## messaggesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|text||
|user_id|integer|foreign_key: true|
|group_id|integer|foreign_key: true|
|timestanps|string|null: false|

### Association
- belongs_to: user
- belongs_to: group


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, add_index|

### Association
- has_many: users, thorugh: :members
- has_many: messages


## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to: user
- belongs_to: group