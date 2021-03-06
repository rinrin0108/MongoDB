### 【丸の内MongoDB勉強会】 Lightning Talk by 林田敦
# ”スキーマレスDB”って本当にいいの？
----
## みなさんはどう思いますか？
- 「○○○○だからスキーマレス最高！」

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

- 「データを分散して保存する場合に便利」
    - RDBでもできるよ！例えば・・・
        - 水平分割：キーとなる値によってデータベースを分ける方法
        - 垂直分割：機能によってデータベースを分ける方法

**なにより、表形式でスキーマかっちりの方がわかりやすくない？**

というわけで、調査してみた。


## ACIDの観点
トランザクションの概念が無いスキーマレスDB
<table border=1>
<tr><td></td><td>RDB</td><td>スキーマレスDB</td></tr>
<tr><td>atomicity（原子性）：トランザクション処理は全て実行されるか、まったく実行されない状態のいずれかで終わる</td><td>○</td><td>×</td></tr>
<tr><td>consistency（一貫性）：トランザクション処理の前後でデータに矛盾を生じない</td><td>○</td><td>×</td></tr>
<tr><td>isolation（独立性）：他のトランザクション処理から影響されない</td><td>○</td><td>×</td></tr>
<tr><td>durability（永続性）：障害が発生しても更新結果は保持される</td><td>○</td><td>×</td></tr>
</table>

### ボトルネックにもなるACID特性
- RDBでは、ACID特性が確保されるが、データ量やアクセス頻度の増大に伴ってACID特性を維持するためのコストが無視できなくなる。そこで、スケールアウト（分散）が必要になる。
    - RDBでは「水平分割」や「垂直分割」ができるが、負荷分散や高可用性を低コストで実現することが困難。（レプリケーションやmemcachedも検索処理のスケールアウトには効果があるが、更新処理やテーブル結合のスケールアウトにはあまり効果がない）
        - RDBサーバのスケールアップ（大型サーバへの載せ替え）
        - DBのレプリケーションやシャード（パーティション）分割によるクラスタ構築
        - 分散キャッシュ（Oracle RACやmemcachedなど）によるクラスタ構築
- スキーマレスDBでは、ACID特性が確保されず、アプリケーション側でのフォローが必要。一方で、データ量やアクセス頻度の増大に伴ってデータストア全体をいくらでも多くのサーバにスケールアウト（分散）できる。
    - スキーマレスDBでは、「水平分散」が低コストで実現可能。

### BASEという考え方
- スキーマレスDBでは、BASEという考え方を取り入れ、consistency（一貫性）を維持するためのコストを抑えている。BASEは、不整合が発生することは滅多にないという考え方に基づいている。
    - BA：Basically Available
        - 可用性を重視する。
    - S：Soft-state
        - 状態の厳密性は追求しない。
    - E：Eventually consistent
        - 最終的に一貫性のつじつまがあえばよい。ある時点では更新されていないケースもある。


## 分散の観点

<table border=1>
<tr><td></td><td>RDB</td><td>スキーマレスDB</td></tr>
<tr><td>分散化のコスト</td><td>×</td><td>◎</td></tr>
<tr><td>負荷分散</td><td>△</td><td>○</td></tr>
<tr><td>高可用性</td><td>△</td><td>◎</td></tr>
<tr><td>複雑な検索や集計</td><td>○</td><td>△</td></tr>
<tr><td>トランザクション</td><td>○</td><td>△</td></tr>
</table>

### キーワードは「スケーラビリティ」
- RDBと比較して、スキーマレスDBは圧倒的にスケーラビリティが高い。
    - シャーディング（データベースの分散運用）が容易
        - オートシャーディング機能により、ダウンタイム無くスケールアウトが可能
    - （フェールオーバーのための）レプリケーションが容易

## 新しい技術との親和性
### アジャイル
- RDB
    - 厳密なスキーマ定義や動的なスケールアウトにコストがかかる
- スキーマレスDB
    - スキーマやデータボリュームの変化に柔軟に対応可能

### クラウド／ビッグデータ
中でも、SaaSのように扱うデータがどんどん増えていくようなものについて
- RDB
    - スケールアウトに多大なコストがかかる
- スキーマレスDB
    - 低コストでスケールアウトが可能

## まとめ
- スキーマレスDBなら、低コストでスケールアウトを伴うシステムを構築できる→**だから素晴らしい！**
    - ただし、一貫性（トランザクション）を保てない場合があるので注意が必要
- スキーマレスDBは、新しい技術との親和性が高い
    - 今後、スキーマレスDBの需要が高まるはず！


----
## 参考資料
- 分散Key-Valueストアの本命「Bigtable」
    - http://www.atmarkit.co.jp/fjava/rensai4/bigtable01/01.html
    - http://www.atmarkit.co.jp/fjava/rensai4/bigtable01/02.html
    - http://www.atmarkit.co.jp/fjava/rensai4/bigtable01/03.html
- CAP定理, BASEのまとめ（shmachid dot com）
    - http://shmachid.com/database/135/
- yohei-y:weblog
    - http://yohei-y.blogspot.jp/search/label/base
- NoSQLを知る
    - http://sssslide.com/www.slideshare.net/frsyuki/nosql-3213215

