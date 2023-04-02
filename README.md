# テンパイ塾 DB設計

## usersテーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |

### Association

- has_many :answers

## questionsテーブル
| Column              | Type | Options     |
| ------------------- | ---- | ----------- |
| correct_answer      | json | null: false |
| explanation         | text | null: false |

### Association

- has_many :answers

## answersテーブル

| Column   | Type       | Options                        |
| -------- | ---------- | ------------------------------ |
| user     | references | null: false, foreign_key: true |
| question | references | null: false, foreign_key: true |
| answer   | json       | null: false                    |

### Association

- belongs_to :user
- belongs_to :question
- has_one :score

## scoresテーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| answer | references | null: false, foreign_key: true |
| score  | float      | null: false                    |

### Association

belongs_to :answer