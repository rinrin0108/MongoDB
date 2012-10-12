### 【丸の内MongoDB勉強会】 Lightning Talk by 林田敦
# スキーマレスって本当にいいの？

- 「カラムを固定できない場合に便利」
    - RDBでもできるよ！

    ```sql
create table practice (data text);
INSERT INTO user(data) VALUES ('{"user_id":1,"screen_name":"rinrin0108","age":24}');
    ```

- 「開発時などスキーマの変更が頻繁に行われる場合に便利」
    - RDBでもALTER TABLEするだけ！

    ```
ALTER TABLE user ADD nickname TEXT;
    ```

## RASISの観点からの評価
<table border=1>
<tr><td></td><td>RDB</td><td>スキーマレス</td></tr>
<tr><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td></tr>
</table>

|>|RDB|スキーマレス|
|Reliability（信頼性）：障害の発生しにくさ|||
|Availability（可用性）：稼働率の高さ|||
|Serviceability（保守性）：障害復旧やメンテナンスのし易さ|||
|Integrity（保全性・完全性：データの破壊や不整合のおきにくさ|||
|Security（機密性）：外部からの侵入・改ざんや機密漏洩の起きにくさ|||

