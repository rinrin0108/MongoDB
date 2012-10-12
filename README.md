### 【丸の内MongoDB勉強会】 Lightning Talk by 林田敦
# ”スキーマレス”って本当にいいの？
----
## みなさんはどう思いますか？
- 「○○○○だからスキーマレス最高！」
- 「××××だからスキーマレスやめられないとまらない！」

## よく耳にするお話
- 「カラムを固定できない場合に便利」
    - RDBでもできるよ！例えば・・・

    ```sql
CREATE TABLE user (data TEXT);
INSERT INTO user(data) VALUES ('{"user_id":1,"screen_name":"rinrin0108","age":24}');
    ```

- 「開発時などスキーマの変更が頻繁に行われる場合に便利」
    - RDBでもALTER TABLEするだけ！例えば・・・

    ```sql
ALTER TABLE user ADD nickname TEXT;
    ```

- 「データを分散しやすい」
    - RDBでも

素朴な疑問
    : なにより、表形式でスキーマかっちりの方がわかりやすくないですか？


## ACIDの観点からの評価
<table border=1>
<tr><td></td><td>RDB</td><td>スキーマレス</td></tr>
<tr><td>atomicity（原子性）</td><td></td><td></td></tr>
<tr><td>consistency（一貫性）：稼働率の高さ</td><td></td><td></td></tr>
<tr><td>isolation（独立性）：障害復旧やメンテナンスのし易さ</td><td></td><td></td></tr>
<tr><td>durability（永続性）：データの破壊や不整合のおきにくさ</td><td></td><td></td></tr>
</table>



## RASISの観点からの評価
<table border=1>
<tr><td></td><td>RDB</td><td>スキーマレス</td></tr>
<tr><td>Reliability（信頼性）：障害の発生しにくさ</td><td></td><td></td></tr>
<tr><td>Availability（可用性）：稼働率の高さ</td><td></td><td></td></tr>
<tr><td>Serviceability（保守性）：障害復旧やメンテナンスのし易さ</td><td></td><td></td></tr>
<tr><td>Integrity（保全性・完全性）：データの破壊や不整合のおきにくさ</td><td></td><td></td></tr>
<tr><td>Security（機密性）：外部からの侵入・改ざんや機密漏洩の起きにくさ</td><td></td><td></td></tr>
</table>


## 分散の観点からの評価

<table border=1>
<tr><td></td><td>RDB</td><td>スキーマレス</td></tr>
<tr><td>分散化のコスト</td><td>×</td><td>◎</td></tr>
<tr><td>負荷分散</td><td>△</td><td>◎</td></tr>
<tr><td>高可用性</td><td>△</td><td>◎</td></tr>
<tr><td>複雑な検索や集計</td><td>◎</td><td>△</td></tr>
<tr><td>トランザクション</td><td>◎</td><td>△</td></tr>
</table>
