## userテーブル
| Columns  | Type   | Options     |
| -------- | ------ | ----------- |
| email    | string | null: false |
| nickname | string | null: false |
| password | string | null: false |

### Association
- has_many :profiles

## profileテーブル
| Columns       | Type      | Options           |
| ------------- | --------- | ----------------- |
| family_name   | string    | null: false       |
| first_name    | string    | null: false       |
| domicile      | string    | null: false       |
| address       | string    | null: false       |
| work_place    | string    |                   |
| qualification | string    |                   |
| hobby         | string    | null: false       |
| height        | integer   | null: false       |
| weight        | integer   | null: false       |
| health_id     | integer   | null: false       |
| user          | reference | foreign_key: true |

### Association
- belongs_to :user
- has_many :educational_backgrounds
- has_many :families

## educational_background
| Columns   | Type      | Options           |
| --------- | --------- | ----------------- |
| period_id | integer   | null: false       |
| year_id   | integer   | null: false       |
| month_id  | integer   | null:false        |
| school    | string    | null: false       |
| status_id | integer   | null: false       |
| profile   | reference | foreign_key: true |

### Association
- belongs_to :profile
- belongs_to_active_hash :period
- belongs_to_active_hash :year
- belongs_to_active_hash :month
- belongs_to_active_hash :status

## family
| Columns              | Type      | Options           |
| -------------------- | --------- | ----------------- |
| relative_family_name | string    |                   |
| relative_first_name  | string    | null: false       |
| period_id            | integer   | null: false       |
| year_id              | integer   | null: false       |
| month_id             | integer   | null: false       |
| day_id               | integer   | null: false       |
| detail               | string    |                   |
| profile              | reference | foreign_key: true |

### Association
- belongs_to :profile
- belongs_to_active_hash :period
- belongs_to_active_hash :year
- belongs_to_active_hash :month
- belongs_to_active_hash :day

## ActiveHash
- period
- year
- month
- day
- status
- health

## 要件定義（変更の可能性あり）
- 所定の項目を入力すると釣書が作成されること
- 作成された釣書は詳細ページにてpdf出力されること
- 作成された釣書は編集できること
- 作成された釣書はuserマイページからのみ閲覧できること
