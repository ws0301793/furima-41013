# DB 設計

## users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| nickname           | string              | null: false               |
| email              | string              | null: false, unique: true |
| encrypted_password | string              | null: false               |
| name               | string              | null: false               |
| furigana_name      | string              | null: false               |
| birthday           | integer             | null: false               |

### Association

* has_many :items
* has_many :orders

## items table

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| items.name                          | string     | null: false                    |
| description                         | text       | null: false                    |
| category                            | string     | null: false                    |
| condition                           | string     | null: false                    |
| postage                             | string     | null: false                    |
| shipping_area                       | string     | null: false                    |
| shipping_date                       | string     | null: false                    |
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
| postcord                            | integer    | null: false                    |
| prefectures                         | string     | null: false                    |
| municipalities                      | string     | null: false                    |
| street                              | string     | null: false                    |
| building                            | string     |                                |
| telephone number                    | integer    | null: false                    |
| order                               | references | null: false, foreign_key: true |

### Association

- belongs_to :order