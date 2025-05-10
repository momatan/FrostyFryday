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

4. ワークシートでSELECTする
```sql
call SPY_ON_FIREY_FRIDEY.CORE.TOP_3_TOPICS();
```
![clear_week51](img/clear_week51.png)

# Snowflake Native App 小咄

Snowflake Native Appのことを遠い世界の話だと思っている人が多いですが、実はそんなことはありません。

Snowflakeユーザーはみんな気づかないうちに実はSnowflake Native Appを使っているのです。そのアプリの名前はSNOWFLAKE。

実はACCOUNT_USAGEやCORTEXはNative Appなんですね。

![account_usage_is_native_app](img/account_usage_is_native_app.png)

そう、SNOWFLAKEっていう名前のNative AppがデフォルトでインストールされているのがSnowflakeというサービスなんですね（紛らわしい）。我々は知らない間にNative Appに依存してたというわけです。

# Snowflake Native App の真骨頂
Snowflake Native AppはStreamlitアプリを共有できることがすごいのだと思っている方が多いと思うのですが、実はCLIの部分を共有できることがすごいのだというのが個人的な見解です。

CLIで使えるということは自動化できるということです。自動化のプロセスの中に差し込む関数やら何やらを共有できるということです。

Pythonなどのプログラミング言語でパッケージを公開している状況と近いですね。それをSQLでできるというのがSnowflake Native Appの真の凄さだと思います。

# 実演 Cortex

# 実演 Native App自作

# PODBの気象アプリの話
弊社は先日気象データを皆様がお持ちの住所や緯度経度と紐づけて作成するSnowflake Native Appをリリースしました。

ブログを参照して使ってみてください！！！
https://blog.truestar.co.jp/prepper/20250411/62507/
