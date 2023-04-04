# usersテーブル

| Column             | Type     | Options                  |
|--------------------|----------|--------------------------|
| nickname           | string   | null: false              |
| email              | string   | null: false  unique: true|
| encrypted_password | string   | null: false              |
| last_name          | string   | null: false              |
| first_name         | string   | null: false              |
| birth_date         | date     | null: false              |

### Association
- has_many :whisky
- has_many :review


# whiskiesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| name               | string   | null: false                   |
| explanation        | text     | null: false                   |
| type_id            | integer  | null: false                   |
| country_id         | integer  | null: false                   |
| area_id            | integer  | null: false                   |
| price_range_id     | integer  | null: false                   |
| user               |references| null: false,foreign_key: true |

### Association
- belongs_to :user
- has_many :reviews


# reviewsテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| user               |references| null: false,foreign_key: true |
| whisky             |references| null: false,foreign_key: true |
| review             | text     | null: false                   |

### Association
- belongs_to :whisky



