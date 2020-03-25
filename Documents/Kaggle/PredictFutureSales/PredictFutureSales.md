# Predict Future Sales

## コンペの目的

ロシア最大のソフトウェア会社の1社である1C Companyから提供された、
毎日の販売データで構成される困難な時系列データセットを用いて、
来月のすべての商品と店舗の総売上高を予測する。

## 何をするコンペか

テストセットのすべてのショップで販売された製品の合計金額を予測すること。

## [RMSE](https://aizine.ai/rmse-rmsle1114/)（Root Mean Squared Error：平均平方二乗誤差）

RMSEは回帰タスクで最も代表的な評価指数。
各レコードの目的変数の真の値と予測値のさの二乗をとり,
それらを平均したあとに平方根をとることで計算される。
RMSEのポイントは以下。

- RMSEを最小化した場合に求まる解が、
誤差が正規分布に従うという前提のもとで求まる最尤解と同じになるなど、
統計学的にも大きな意味をもった評価指標。
- 仮に1つの代表値で予測を行う場合、
RSMEを最小化する予測値は平均値。
例えば、
[1,2,3,4,10]と値がある場合、
1点で予測したときに最もRMSEが小さくなる予測値は平均である4になる。
- MAEと比較すると外れ値の影響を受けやすいので、
あらかじめ外れ値を除く処理などをしておかないと外れ値に過剰に適合したモデルを作成してしまう可能性がある。

## どんなデータがあったのか

日ごとの過去の販売データ。ショップと製品のリストは毎月わずかに変更される。

### ファイルの説明

- sales_train.csv-トレーニングセット。2013年1月から2015年10月までの日次履歴データ。
- test.csv-テストセット。2015年11月のこれらのショップと製品の売上を予測する必要がある。
- sample_submission.csv-正しい形式のサンプル送信ファイル。
- items.csv-アイテム/製品に関する補足情報。
- item_categories.csv-アイテムのカテゴリに関する補足情報。
- shops.csv-ショップに関する補足情報。

### データフィールド

- ID-テストセット内の（ショップ、アイテム）タプルを表す。
- ID shop_id-ショップの一意の識別子。
- item_id-製品の一意の識別子。
- item_category_id-アイテムカテゴリの一意の識別子。
- item_cnt_day-販売された製品の数。このメジャーの月額を予測している。
- item_price-アイテムの現在の価格 日付-dd / mm / yyyy形式の日付。
- date_block_num-便宜上使用される連続した月番号。 2013年1月は0、2013年2月は1、...、2015年10月は33。
- item_name-アイテムの名前。
- shop_name-ショップの名前。
- item_category_name-アイテムカテゴリの名前。