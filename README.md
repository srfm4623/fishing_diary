# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| last_name          | string | null: false |
| first_name         | string | null: false |
| last_name_kana     | string | null: false |
| first_name_kana    | string | null: false |
| date               | date   | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :results
- has_many :comments

## results テーブル

| Column        | Type       | Options           |
| ------------- | ---------- | ----------------- |
| title         | string     | null: false       |
| length        | integer    | null: false       |
| weight        | integer    | null: false       |
| area          | string     |                   |
| text          | text       |                   |
| user          | references | foreign_key: true |

### Association

- belongs_to :user
- has_many   :comments

## comments テーブル

| Column | Type       | Options           |
| ------ | ---------- | ----------------- |
| text   | text       | null: false       |
| user   | references | foreign_key: true |
| posts  | references | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :result
