# Line APP 推薦系統


## 大綱
>* 範例資料描述
>* 開發工具與需求
>* 推薦系統
>>1. 過去消費紀錄推薦
>>2. 消費者族群推薦
>* APP 互動介面
>>* 概念說明
>>* 運作方式


## 範例資料描述
### 1. 欄位選擇:
>* 雖逐筆交易中以商品名稱作為品項，但因品項過多且交易筆數過少,遂以品牌與商品種類作為推薦品項。
>* 由數量呈單價而非數量作為逐筆訂單分數以避免總是推薦低價商品的問題。
### 2.  資料說明:
#### (1) all_data.csv
| **英文欄位** |  **中文欄位** || **英文欄位** |  **中文欄位** |
|---------|----------|---|---------|----------|
|cart_id|購物車id||member_id|會員編號|
|retailer|通路||address|通路地址|
|channel|訂單來源||category|商品類別|
|brand|商品品牌||item|商品名稱|
|cnt|商品數量||per_price|單價|
|shipping_fee|運費||discount|折扣|
|payment|付款方式||attribute|商品屬性|
|additional_purchase|加價購||age|顧客年齡|
|regist_days|註冊期長||last_purchaseday|最後消費間隔|
|tol_purchase_price|會員總消費金額||tol_purchase_time|會員總消費次數|
|gender|性別||membership_source|會員資料來源|

#### (2) 產品類別代號對照表:
|**類別**|**代號**||**類別**|**代號**|
|---|---|---|---|---|
|去角質|1||沐浴|2|
|其他|3||卸妝|4|
|底妝|5||保濕|6|
|持妝|7||洗髮|8|
|洗顏|9||眉毛|10|
|美白|11||眼線|12|
|睫毛|13||補妝|14|
|遮瑕|15||護唇|16|



## 開發工具與需求
>* Python 3.6
>* Python Modules: pandas, numpy, surprise
>* Vitural C++ 14.0以上版本
>* 資料輸出/入格式:  csv

## 推薦系統

### 1. 有過去消費紀錄推薦:
>* 由顧客對某一商品類別,品牌或類別品牌組合的累積消費額作為喜好分數。
>* 由逐筆訂單資料中整理得出資料後。以SVD推薦系統投影至50個隱藏因素計算得分後做推薦。
>> ![image](img/SVD.JPG)

§由逐筆訂單資料中整理得出。
### 2. 消費者族群推薦:
> 因顧客無過去消費紀錄，故將顧客依基本信息分群，找出族群偏好作為推薦。
