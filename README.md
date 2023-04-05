# usersテーブル

| Column             | Type     | Options                  |
|--------------------|----------|--------------------------|
| nickname           | string   | null: false              |
| email              | string   | null: false  unique: true|
| encrypted_password | string   | null: false              |
| birth_date         | date     | null: false              |

### Association
- has_many :whiskies
- has_many :reviews


# whiskiesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| name               | string   | null: false                   |
| explanation        | text     | null: false                   |
| type_id            | integer  | null: false                   |
| country_id         | integer  | null: false                   |
| area_id            | integer  | null: false                   |
| price_range        | string   | null: false                   |
| user               |references| null: false,foreign_key: true |


### Association
- belongs_to :user
- has_many :reviews
- has_many :distillery


# reviewsテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| user               |references| null: false,foreign_key: true |
| whisky             |references| null: false,foreign_key: true |
| title              | string   | null: false                   |
| review_text        | text     | null: false                   |

### Association
- belongs_to :whisky

# distilleriesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| user               |references| null: false,foreign_key: true |
| review             |references| null: false,foreign_key: true |
| distillery_name    | text     | null: false,foreign_key: true |
| distillery_text    | text     | null: false,foreign_key: true |
| distillery_text    | text     | null: false,foreign_key: true |

### Association
- has_many :whisky

# whisky_distilleriesテーブル

| Column             | Type     | Options                       |
|--------------------|----------|-------------------------------|
| distillery         |references| null: false,foreign_key: true |
| whisky             |references| null: false,foreign_key: true |



