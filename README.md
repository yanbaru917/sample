# README

#  DB設計
## userテーブル
|column|Type|Option|
|------|----|------|
|nick_name|string|null: false|
|e-mail|string|null: false|
|password|string|null: false|
### Association
- has_many : items
- has_one : profile, dependent: :destroy
- has_one : credit_card, dependent: :destroy

## profileテーブル
|column|Type|Option|
|------|----|------|
|phone_number|integer|unique:true|
|first_name|string|null: false|
|family_name|string|null: false,|
|first_name_kana|string|null: false|
|family_name_kana|string|null: false|
|birthday|integer|null: false|
|post_number|integer|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|house_number|string|null: false|
|building_name|string||

### Association
- belongs_to : user
- has_many : items 

## credit_cardテーブル
|column|Type|Option|
|------|----|------|
|user|references|null: false, foreign_key: true|
|card_number|integer|null: false ,unique: true|
|expiration_year|integer|null: false|
|expiration_month|integer|null: false|
|security_code|integer|null: false|

### Association
- belongs_to : messages

## itemテーブル
|column|Type|Option|
|------|----|------|
|item_name|string|null: false,|
|introduction|text|null: false,|
|price|integer|null: false|
|shipment_date|string|null: false|
|shipment_pref|string|null: false|
|category_name|string|null: false, foreign_key: true|
|brand|string|null: false|
|item_status|string|null: false|
|shipment_fee|string|null: false|
|seller|reference|null: false, foreign_key: true|
|buyer|reference|foreign_key: true|
|prefecture|string|null: false|
|item_img|integer|null: false, foreign_key: true|
### Association
- belongs_to : seller class_name: "User"
- belongs_to : buyer class_name: "User"
- belongs_to : category
- had_many: item_imgs, dependent::destroy

## item-imageテーブルテーブル
|column|Type|Option|
|------|----|------|
|url|string|null:false|
|item|reference|null:false,foregin_key:true|
### Association
- belongs_to : item

## categoryテーブルテーブル
|column|Type|Option|
|------|----|------|
|name|string|null:false|
|ancestry|string|null:false|
### Association
- has_many: items