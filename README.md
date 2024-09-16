# DB 設計

## users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| nickname           | string              | null: false               |
| email              | string              | null: false, unique: true |
| encrypted_password | string              | null: false               |
| lastname           | string              | null: false               |
| firstname          | string              | null: false               |
| furigana_lastname  | string              | null: false               |
| furigana_firstname | string              | null: false               |
| birthday           | date                | null: false               |

### Association

* has_many :items
* has_many :orders

## items table

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| item_name                           | string     | null: false                    |
| description                         | text       | null: false                    |
| category_id                         | integer    | null: false                    |
| condition_id                        | integer    | null: false                    |
| postage_id                          | integer    | null: false                    |
| prefecture_id                       | integer    | null: false                    |
| shipping_date_id                    | integer    | null: false                    |
| price                               | integer    | null: false                    |
| user                                | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :order

## orders table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| item        | references | null: false, foreign_key: true |
| user        | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :shipping

## shippings table

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| postcord                            | string     | null: false                    |
| prefecture_id                       | integer    | null: false                    |
| municipalities                      | string     | null: false                    |
| street                              | string     | null: false                    |
| building                            | string     |                                |
| telephone_number                    | string     | null: false                    |
| order                               | references | null: false, foreign_key: true |

### Association

- belongs_to :order