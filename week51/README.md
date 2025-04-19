# 回答

1. Projects -> App Packages から SPY_ON_FIREY_FRIDEY というアプリを作成する
2. Data -> Databases から　SPY_ON_FIREY_FRIDEY を選択し、COREというSchemaを作成する
3. COREの中にCreateからProcedureを作成する

```sql
create procedure TOP_3_TOPICS (
    )
returns string
language python
runtime_version = '3.11'
packages = ('snowflake-snowpark-python')
handler = 'main'
as 
$$
def main():
    message = "Oh, they are obsessed with Arrays, how weird. And then it's all about Graphs and Dynamic Programming. How pathetic!"
    return message
$$
;
```


# せっかくなのでデータ参照する関数を作ってみる

データの参照は2パターンある。

1. アプリ内にテーブルを持ってそれを参照する
2. アプリ外部のテーブルのデータを参照する

2のアプリ外部のテーブルを参照するのがアプリの真骨頂といえる。これができるとアプリをプライベートシェアした際にプロバイダー側で編集したデータはアプリから参照した場合も変更を追従する。
1の場合はアプリ自体がデータを保持した形でインストールされるため、共有したアプリをGetした時点でデータが固定される。

## 1. アプリ内にテーブルを持ってそれを参照する
1. SPY_ON_FIREY_FRIDEYの中にテーブルを作ってそれをSELECTする関数を作る
2. 誰かの環境に共有する
3. Kommy環境で変更したデータが、共有には追従されないことを確認する

## 2. アプリ外部のテーブルのデータを参照する
1. REFERENCEの概念を説明


# Streamlitアプリを足してみる
1. これSnowsightからやる方法なさそうなのでここまでやるならCLIでやるしかないか？


# 結局Snowflake Native Appって何がすごいの？
1. データだけじゃなくてデータを活用するための関数を共有できるのがすごい


# PODBの気象アプリの話
1. マーケットプレイスからダウンロードして使ってみる
