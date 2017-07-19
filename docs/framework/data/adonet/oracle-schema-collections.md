---
title: "Oracle スキーマ コレクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89a75de8-dee8-45e2-a97f-254d7e62e7e1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Oracle スキーマ コレクション
Microsoft .NET Framework Data Provider for Oracle は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。  
  
-   列  
  
-   Indexes  
  
-   IndexColumns  
  
-   手順  
  
-   シーケンス  
  
-   Synonyms  
  
-   \[テーブル\]  
  
-   Users  
  
-   ビュー  
  
-   関数  
  
-   パッケージ  
  
-   PackageBodies  
  
-   引数  
  
-   UniqueKeys  
  
-   PrimaryKeys  
  
-   ForeignKeys  
  
-   ForeignKeyColumns  
  
-   ProcedureParameters  
  
## 列  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|テーブル、ビュー、またはクラスターの所有者。|  
|TABLE\_NAME|String|テーブル、ビュー、またはクラスターの名前。|  
|COLUMN\_NAME|String|列名。|  
|ID|Decimal \(10 進数型\)|作成された列のシーケンス番号。|  
|DATATYPE|String|列のデータ型。|  
|LENGTH|Decimal \(10 進数型\)|列の長さ \(バイト単位\)。|  
|PRECISION|Decimal \(10 進数型\)|NUMBER データ型の場合は 10 進有効桁数、FLOAT データ型の場合はバイナリ有効桁数、その他のデータ型の場合は NULL になります。|  
|SCALE|Decimal \(10 進数型\)|数値の小数点の右側にある数字。|  
|NULLABLE|String|列に NULL を許可するかどうかを指定します。  列に NOT NULL 制約がある場合、または列が PRIMARY KEY の一部である場合、値は N になります。|  
  
## Indexes  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|インデックスの所有者。|  
|INDEX\_NAME|String|インデックス名。|  
|INDEX\_TYPE|String|インデックスの型 \(NORMAL、BITMAP、FUNCTION\-BASED NORMAL、FUNCTION\-BASED BITMAP、または DOMAIN\)。|  
|TABLE\_OWNER|String|インデックス付きオブジェクトの所有者。|  
|TABLE\_NAME|String|インデックス付きオブジェクト名。|  
|TABLE\_TYPE|String|インデックス オブジェクトの型 \(TABLE、CLUSTER など\)。|  
|UNIQUENESS|String|インデックスが UNIQUE または NONUNIQUE のどちらであるかを指定します。|  
|COMPRESSION|String|インデックスが ENABLED または DISABLED のどちらであるかを指定します。|  
|PREFIX\_LENGTH|Decimal \(10 進数型\)|圧縮キーのプレフィックス内の列数。|  
|TABLESPACE\_NAME|String|インデックスを含むテーブルスペースの名前。|  
|INI\_TRANS|Decimal \(10 進数型\)|トランザクションの初期数。|  
|MAX\_TRANS|Decimal \(10 進数型\)|トランザクションの最大数。|  
|INITIAL\_EXTENT|Decimal \(10 進数型\)|初期エクステントのサイズ。|  
|NEXT\_EXTENT|Decimal \(10 進数型\)|セカンダリ エクステントのサイズ。|  
|MIN\_EXTENTS|Decimal \(10 進数型\)|セグメント内で許可されているエクステントの最小数。|  
|MAX\_EXTENTS|Decimal \(10 進数型\)|セグメント内で許可されているエクステントの最大数。|  
|PCT\_INCREASE|Decimal \(10 進数型\)|エクステントのサイズの増加率。|  
|PCT\_THRESHOLD|Decimal \(10 進数型\)|インデックスのエントリごとに許可されるブロック領域のしきい値のパーセンテージ。|  
|INCLUDE\_COLUMN|Decimal \(10 進数型\)|索引構成表の主キー \(オーバーフローなし\) のインデックスに含まれる最後の列の列 ID。  この列は、\*\_TAB\_COLUMNS データ辞書ビューの COLUMN\_ID 列にマップされます。|  
|FREELISTS|Decimal \(10 進数型\)|このセグメントに割り当てられているプロセスの空きリスト数。|  
|FREELIST\_GROUPS|Decimal \(10 進数型\)|このセグメントに割り当てられている空きリスト グループの数。|  
|PCT\_FREE|Decimal \(10 進数型\)|ブロックにある空き領域の最小のパーセンテージ。|  
|LOGGING|String|ログ情報。|  
|BLEVEL|Decimal \(10 進数型\)|B\*\-ツリー レベル: ルート ブロックからリーフ ブロックまでのインデックスの深さ。  深さ 0 は、ルート ブロックとリーフ ブロックが同一であることを示します。|  
|LEAF\_BLOCKS|Decimal \(10 進数型\)|インデックス内のリーフ ブロックの数。|  
|DISTINCT\_KEYS|Decimal \(10 進数型\)|個別にインデックスが付けられた値の数。  UNIQUE および PRIMARY KEY 制約を強制するインデックスの場合、この値はテーブルの行数 \(USER\_TABLES.NUM\_ROWS\) と同じです。|  
|AVG\_LEAF\_BLOCKS\_PER\_KEY|Decimal \(10 進数型\)|最も近い整数に丸められた、インデックスの個別の値が表示されるリーフ ブロックの平均数。  UNIQUE および PRIMARY KEY 制約を強制するインデックスの場合、この値は常に 1 になります。|  
|AVG\_DATA\_BLOCKS\_PER\_KEY|Decimal \(10 進数型\)|最も近い整数に丸められた、インデックス内の個別の値によってポイントされている、テーブル内のデータ ブロックの平均数。  この統計情報は、インデックス列の値を含む行があるデータ ブロックの平均数を示します。|  
|CLUSTERING\_FACTOR|Decimal \(10 進数型\)|インデックスの値に基づいて順序付けされている、テーブルの行数を示します。|  
|STATUS|String|分割されていないインデックスが VALID または UNUSABLE のどちらであるかを示します。|  
|NUM\_ROWS|Decimal \(10 進数型\)|インデックス内の行数。|  
|SAMPLE\_SIZE|Decimal \(10 進数型\)|インデックスの分析に使用されるサンプルのサイズ。|  
|LAST\_ANALYZED|DateTime|インデックスが最後に分析された日付。|  
|DEGREE|String|インデックスがスキャンされるインスタンスごとのスレッド数。|  
|INSTANCES|String|インデックスがスキャンされるインスタンス数。|  
|PARTITIONED|String|インデックスが分割されているかどうかを示します \(YES または NO\)。|  
|TEMPORARY|String|インデックスが一時テーブルにあるかどうかを示します。|  
|GENERATED|String|インデックスの名前がシステムが生成した名前かどうかを示します \(Y または N\)。|  
|SECONDARY|String|インデックスが Oracle9i Data Cartridge の ODCIIndexCreate メソッドによって作成されたセカンダリ オブジェクトであるかどうかを示します \(Y または N\)。|  
|BUFFER\_POOL|String|インデックス ブロックで使用される既定のバッファー プールの名前。|  
|USER\_STATS|String|統計情報がユーザーによって直接入力されたものかどうかを示します。|  
|DURATION|String|一時テーブルの存続期間を示します。1\) SYS$SESSION: セッションが存続している間、行が保持されます。2\) SYS$TRANSACTION: COMMIT 後に行が削除されます。3\) 永続テーブルの場合は NULL です。|  
|PCT\_DIRECT\_ACCESS|Decimal \(10 進数型\)|索引構成表のセカンダリ インデックスでは、VALID であると推測される行のパーセンテージを示します。|  
|ITYP\_OWNER|String|ドメイン インデックスでは、indextype の所有者を示します。|  
|ITYP\_NAME|String|ドメイン インデックスでは、indextype の名前を示します。|  
|PARAMETERS|String|ドメイン インデックスでは、パラメーターの文字列を示します。|  
|GLOBAL\_STATS|String|分割されたインデックスでは、統計情報がインデックス全体を分析して収集されたものか \(YES\)、または基になるインデックスのパーティションおよびサブパーティションから推測されたものであるか \(NO\) どうかを示します。|  
|DOMIDX\_STATUS|String|ドメイン インデックスのステータスが反映されます。  NULL: 指定されたインデックスはドメイン インデックスではありません。  VALID: インデックスは有効なドメイン インデックスです。  IDXTYP\_INVLD: このドメイン インデックスのインデックス型は無効です。|  
|DOMIDX\_OPSTATUS|String|ドメイン インデックス上で実行された操作のステータスが反映されます。NULL: 指定されたインデックスはドメイン インデックスではありません。  VALID: 操作がエラーなく実行されました。  FAILED: エラーによって操作が失敗しました。|  
|FUNCIDX\_STATUS|String|関数ベースのインデックスのステータスを示します。NULL: これは関数ベースのインデックスではありません。ENABLED: 関数ベースのインデックスが有効になっています。DISABLED: 関数ベースのインデックスが無効になっています。|  
|JOIN\_INDEX|String|結合インデックスかどうかを示します。|  
  
## IndexColumns  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|INDEX\_OWNER|String|インデックスの所有者。|  
|INDEX\_NAME|String|インデックス名。|  
|TABLE\_OWNER|String|テーブルまたはクラスターの所有者。|  
|TABLE\_NAME|String|テーブルまたはクラスターの名前。|  
|COLUMN\_NAME|String|オブジェクト型列の列名または属性。|  
|COLUMN\_POSITION|Decimal \(10 進数型\)|インデックス内の列または属性の位置。|  
|COLUMN\_LENGTH|Decimal \(10 進数型\)|インデックスが付けられた列の長さ。|  
|CHAR\_LENGTH|Decimal \(10 進数型\)|列の最大コードポイント長。|  
|DESCEND|String|列が降順で並べ替えられるかどうかを示します。|  
  
## 手順  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|オブジェクトの所有者。|  
|OBJECT\_NAME|String|オブジェクト名。|  
|SUBOBJECT\_NAME|String|サブオブジェクト名 \(partition など\)。|  
|OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトの辞書オブジェクト数。|  
|DATA\_OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトを含むセグメントの辞書オブジェクト数。|  
|LAST\_DDL\_TIME|DateTime|DDL コマンド \(許可および取り消しを含む\) の実行結果として、最後に変更されたオブジェクトのタイムスタンプ。|  
|TIMESTAMP|String|オブジェクト \(文字データ\) の指定に対するタイムスタンプ。|  
|STATUS|String|オブジェクトのステータス \(VALID、INVALID、または N\/A\)。|  
|TEMPORARY|String|オブジェクトが一時的かどうかを示します \(現在のセッションでは、オブジェクト自体に置かれたデータだけが表示される\)。|  
|GENERATED|String|このオブジェクトの名前がシステムによって生成されたかどうかを示します   \(Y または N\)。|  
|SECONDARY|String|Oracle9i Data Cartridge の ODCIIndexCreate メソッドによって作成されたセカンダリ オブジェクトかどうかを示します \(Y または N\)。|  
|CREATED|DateTime|オブジェクトが作成された日付。|  
  
## シーケンス  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|SEQUENCE\_OWNER|String|シーケンスの所有者の名前。|  
|SEQUENCE\_NAME|String|シーケンス名。|  
|MIN\_VALUE|Decimal \(10 進数型\)|シーケンスの最小値。|  
|MAX\_VALUE|Decimal \(10 進数型\)|シーケンスの最大値。|  
|INCREMENT\_BY|Decimal \(10 進数型\)|シーケンスがインクリメントされる値。|  
|CYCLE\_FLAG|String|限界に到達するとシーケンスはラップされるかを示します。|  
|ORDER\_FLAG|String|順に生成されたシーケンス番号。|  
|CACHE\_SIZE|Decimal \(10 進数型\)|キャッシュするシーケンス番号の数。|  
|LAST\_NUMBER|Decimal \(10 進数型\)|ディスクに書き込まれた最後のシーケンス番号。  シーケンスでキャッシュが使用される場合、ディスクに書き込まれた数はシーケンスのキャッシュに置かれた最後の番号になります。  この番号は多くの場合、使用された最後のシーケンス番号より大きくなります。|  
  
## Synonyms  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|シノニムの所有者。|  
|SYNONYM\_NAME|String|シノニムの名前。|  
|TABLE\_OWNER|String|シノニムが参照するオブジェクトの所有者。|  
|TABLE\_NAME|String|シノニムが参照するオブジェクトの名前。|  
|DB\_LINK|String|参照されるデータベース リンクの名前 \(参照される場合\)。|  
  
## \[テーブル\]  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|テーブルの所有者。|  
|TABLE\_NAME|String|テーブルの名前。|  
|TYPE|String|テーブルの型。|  
  
## Users  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|NAME|String|ユーザー名。|  
|ID|Decimal \(10 進数型\)|ユーザーの ID 番号。|  
|CREATEDATE|DateTime|ユーザーの作成日。|  
  
## ビュー  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|ビューの所有者。|  
|VIEW\_NAME|String|ビューの名前。|  
|TEXT\_LENGTH|Decimal \(10 進数型\)|ビュー テキストの長さ。|  
|TEXT|String|ビュー テキスト。|  
|TYPE\_TEXT\_LENGTH|Decimal \(10 進数型\)|型指定されたビューの TYPE 句の長さ。|  
|TYPE\_TEXT|String|型指定されたビューの TYPE 句。|  
|OID\_TEXT\_LENGTH|Decimal \(10 進数型\)|型指定されたビューの WITH OID 句の長さ。|  
|OID\_TEXT|String|型指定されたビューの WITH OID 句。|  
|VIEW\_TYPE\_OWNER|String|ビューが型指定されたビューである場合の、ビューの型の所有者。|  
|VIEW\_TYPE|String|ビューが型指定されたビューである場合の、ビューの型。|  
|SUPERVIEW\_NAME|String|スーパービューの名前。|  
  
## 関数  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|オブジェクトの所有者。|  
|OBJECT\_NAME|String|オブジェクト名。|  
|SUBOBJECT\_NAME|String|サブオブジェクト名 \(partition など\)。|  
|OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトの辞書オブジェクト数。|  
|DATA\_OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトを含むセグメントの辞書オブジェクト数。|  
|OBJECT\_TYPE|String|オブジェクトの型。|  
|CREATED|DateTime|オブジェクトが作成された日付。|  
|LAST\_DDL\_TIME|DateTime|DDL コマンド \(許可および取り消しを含む\) の実行結果として、最後に変更されたオブジェクトのタイムスタンプ。|  
|TIMESTAMP|String|オブジェクト \(文字データ\) の指定に対するタイムスタンプ。|  
|STATUS|String|オブジェクトのステータス \(VALID、INVALID、または N\/A\)。|  
|TEMPORARY|String|オブジェクトが一時的かどうかを示します \(現在のセッションでは、オブジェクト自体に置かれたデータだけが表示される\)。|  
|GENERATED|String|このオブジェクトの名前がシステムによって生成されたかどうかを示します   \(Y または N\)。|  
|SECONDARY|String|Oracle9i Data Cartridge の ODCIIndexCreate メソッドによって作成されたセカンダリ オブジェクトかどうかを示します \(Y または N\)。|  
  
## パッケージ  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|オブジェクトの所有者。|  
|OBJECT\_NAME|String|オブジェクト名。|  
|SUBOBJECT\_NAME|String|サブオブジェクト名 \(partition など\)。|  
|OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトの辞書オブジェクト数。|  
|DATA\_OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトを含むセグメントの辞書オブジェクト数。|  
|LAST\_DDL\_TIME|DateTime|DDL コマンド \(許可および取り消しを含む\) の実行結果として、最後に変更されたオブジェクトのタイムスタンプ。|  
|TIMESTAMP|String|オブジェクト \(文字データ\) の指定に対するタイムスタンプ。|  
|STATUS|String|オブジェクトのステータス \(VALID、INVALID、または N\/A\)。|  
|TEMPORARY|String|オブジェクトが一時的かどうかを示します \(現在のセッションでは、オブジェクト自体に置かれたデータだけが表示される\)。|  
|GENERATED|String|このオブジェクトの名前がシステムによって生成されたかどうかを示します   \(Y または N\)。|  
|SECONDARY|String|Oracle9i Data Cartridge の ODCIIndexCreate メソッドによって作成されたセカンダリ オブジェクトかどうかを示します \(Y または N\)。|  
|CREATED|DateTime|オブジェクトが作成された日付。|  
  
## PackageBodies  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|オブジェクトの所有者。|  
|OBJECT\_NAME|String|オブジェクト名。|  
|SUBOBJECT\_NAME|String|サブオブジェクト名 \(partition など\)。|  
|OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトの辞書オブジェクト数。|  
|DATA\_OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトを含むセグメントの辞書オブジェクト数。|  
|LAST\_DDL\_TIME|DateTime|DDL コマンド \(許可および取り消しを含む\) の実行結果として、最後に変更されたオブジェクトのタイムスタンプ。|  
|TIMESTAMP|String|オブジェクト \(文字データ\) の指定に対するタイムスタンプ。|  
|STATUS|String|オブジェクトのステータス \(VALID、INVALID、または N\/A\)。|  
|TEMPORARY|String|オブジェクトが一時的かどうかを示します \(現在のセッションでは、オブジェクト自体に置かれたデータだけが表示される\)。|  
|GENERATED|String|このオブジェクトの名前がシステムによって生成されたかどうかを示します   \(Y または N\)。|  
|SECONDARY|String|Oracle9i Data Cartridge の ODCIIndexCreate メソッドによって作成されたセカンダリ オブジェクトかどうかを示します \(Y または N\)。|  
|CREATED|DateTime|オブジェクトが作成された日付。|  
  
## 引数  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|オブジェクトの所有者の名前。|  
|PACKAGE\_NAME|String|パッケージ名。|  
|OBJECT\_NAME|String|プロシージャまたは関数の名前。|  
|ARGUMENT\_NAME|String|引数の名前。|  
|POSITION|Decimal \(10 進数型\)|引数リスト内の位置。関数の戻り値の場合は NULL。|  
|SEQUENCE|Decimal \(10 進数型\)|入れ子になったすべてのレベルを含む引数シーケンス。|  
|DEFAULT\_VALUE|String|引数の既定値。|  
|DEFAULT\_LENGTH|Decimal \(10 進数型\)|引数の既定値の長さ。|  
|IN\_OUT|String|引数の方向 \(IN、OUT、または IN\/OUT\)。|  
|DATA\_LENGTH|Decimal \(10 進数型\)|列の長さ \(バイト単位\)。|  
|DATA\_PRECISION|Decimal \(10 進数型\)|小数桁数 \(NUMBER\) またはバイナリ桁数 \(FLOAT\) の長さ。|  
|DATA\_SCALE|Decimal \(10 進数型\)|数値の小数点の右側にある数字。|  
|DATA\_TYPE|String|引数のデータ型。|  
  
## UniqueKeys  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|制約定義の所有者。|  
|CONSTRAINT\_NAME|String|制約定義の名前。|  
|TABLE\_NAME|String|制約定義を持つテーブル \(またはビュー\) に関連付けられた名前。|  
|SEARCH\_CONDITION|String|CHECK 制約の検索条件のテキスト。|  
|R\_OWNER|String|参照制約で参照されるテーブルの所有者。|  
|R\_CONSTRAINT\_NAME|String|参照テーブルの UNIQUE 制約の定義の名前。|  
|DELETE\_RULE|String|参照制約の削除規則 \(CASCADE または NO ACTION\)。|  
|STATUS|String|制約の強制ステータス \(ENABLED または DISABLED\)。|  
|DEFERRABLE|String|制約を遅延可能にするかどうかを示します。|  
|VALIDATED|String|すべてのデータが制約に従うかどうかを示します \(VALIDATED または NOT VALIDATED\)。|  
|GENERATED|String|制約の名前がユーザーとシステムのどちらによって生成されたかを示します。|  
|BAD|String|値 YES は、この制約が世紀をあいまいに指定していることを示します。  このあいまいさによるエラーを回避するには、TO\_DATE 関数に 4 桁の西暦を使って制約を定義し直します。|  
|RELY|String|有効な制約が強制されたものであるかどうかを示します。|  
|LAST\_CHANGE|DateTime|制約が最後に有効または無効になった日時を示します。|  
|INDEX\_OWNER|String|インデックスを所有するユーザーの名前。|  
|INDEX\_NAME|String|インデックス名。|  
  
## PrimaryKeys  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|制約定義の所有者。|  
|CONSTRAINT\_NAME|String|制約定義の名前。|  
|TABLE\_NAME|String|制約定義を持つテーブル \(またはビュー\) に関連付けられた名前。|  
|SEARCH\_CONDITION|String|CHECK 制約の検索条件のテキスト。|  
|R\_OWNER|String|参照制約で参照されるテーブルの所有者。|  
|R\_CONSTRAINT\_NAME|String|参照テーブルの UNIQUE 制約の定義の名前。|  
|DELETE\_RULE|String|参照制約の削除規則 \(CASCADE または NO ACTION\)。|  
|STATUS|String|制約の強制ステータス \(ENABLED または DISABLED\)。|  
|DEFERRABLE|String|制約を遅延可能にするかどうかを示します。|  
|VALIDATED|String|すべてのデータが制約に従うかどうかを示します \(VALIDATED または NOT VALIDATED\)。|  
|GENERATED|String|制約の名前がユーザーとシステムのどちらによって生成されたかを示します。|  
|BAD|String|値 YES は、この制約が世紀をあいまいに指定していることを示します。  このあいまいさによるエラーを回避するには、TO\_DATE 関数に 4 桁の西暦を使って制約を定義し直します。|  
|RELY|String|有効な制約が強制されたものであるかどうかを示します。|  
|LAST\_CHANGE|DateTime|制約が最後に有効または無効になった日時を示します。|  
|INDEX\_OWNER|String|インデックスを所有するユーザーの名前。|  
|INDEX\_NAME|String|インデックス名。|  
  
## ForeignKeys  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|PRIMARY\_KEY\_CONSTRAINT\_NAME|String|制約定義の名前。|  
|PRIMARY\_KEY\_OWNER|String|制約定義の所有者。|  
|PRIMARY\_KEY\_TABLE\_NAME|String|制約定義を持つテーブル \(またはビュー\) に関連付けられた名前。|  
|FOREIGN\_KEY\_OWNER|String|制約定義の所有者。|  
|FOREIGN\_KEY\_CONSTRIANT\_NAME|String|制約定義の名前。|  
|FOREIGN\_KEY\_TABLE\_NAME|String|制約定義を持つテーブル \(またはビュー\) に関連付けられた名前。|  
|SEARCH\_CONDITION|String|CHECK 制約の検索条件のテキスト。|  
|R\_OWNER|String|参照制約で参照されるテーブルの所有者。|  
|R\_CONSTRAINT\_NAME|String|参照テーブルの UNIQUE 制約の定義の名前。|  
|DELETE\_RULE|String|参照制約の削除規則 \(CASCADE または NO ACTION\)。|  
|STATUS|String|制約の強制ステータス \(ENABLED または DISABLED\)。|  
|VALIDATED|String|すべてのデータが制約に従うかどうかを示します \(VALIDATED または NOT VALIDATED\)。|  
|GENERATED|String|制約の名前がユーザーとシステムのどちらによって生成されたかを示します。|  
|RELY|String|有効な制約が強制されたものであるかどうかを示します。|  
|LAST\_CHANGE|DateTime|制約が最後に有効または無効になった日時を示します。|  
|INDEX\_OWNER|String|インデックスを所有するユーザーの名前。|  
|INDEX\_NAME|String|インデックス名。|  
  
## ForeignKeyColumns  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|制約定義の所有者。|  
|CONSTRAINT\_NAME|String|制約定義の名前。|  
|TABLE\_NAME|String|制約定義を持つテーブル名。|  
|COLUMN\_NAME|String|制約定義で指定されているオブジェクト型列の列名または属性名。|  
|POSITION|Decimal \(10 進数型\)|オブジェクトの定義内の列または属性の元の位置。|  
  
## ProcedureParameters  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|OWNER|String|オブジェクトの所有者。|  
|OBJECT\_NAME|String|プロシージャまたは関数の名前。|  
|PACKAGE\_NAME|String|プロシージャまたは関数の名前。|  
|OBJECT\_ID|Decimal \(10 進数型\)|オブジェクトのオブジェクト番号。|  
|OVERLOAD|String|オーバーロードの一意識別子。|  
|ARGUMENT\_NAME|String|引数の名前。|  
|POSITION|Decimal \(10 進数型\)|引数リスト内の位置。関数の戻り値の場合は NULL。|  
|SEQUENCE|Decimal \(10 進数型\)|入れ子になったすべてのレベルを含む引数シーケンス。|  
|DATA\_LEVEL|Decimal \(10 進数型\)|複合型の引数の入れ子の深さ。|  
|DATA\_TYPE|String|引数のデータ型。|  
|DEFAULT\_VALUE|String|引数の既定値。|  
|DEFAULT\_LENGTH|Decimal \(10 進数型\)|引数の既定値の長さ。|  
|IN\_OUT|String|引数の方向 \(IN、OUT、または IN\/OUT\)。|  
|DATA\_LENGTH|Decimal \(10 進数型\)|列の長さ \(バイト単位\)。|  
|DATA\_PRECISION|Decimal \(10 進数型\)|小数桁数 \(NUMBER\) またはバイナリ桁数 \(FLOAT\) の長さ。|  
|DATA\_SCALE|Decimal \(10 進数型\)|数値の小数点の右側にある数字。|  
|RADIX|Decimal \(10 進数型\)|数値の引数の基数。|  
|CHARACTER\_SET\_NAME|String|引数の文字セットの名前。|  
|TYPE\_OWNER|String|引数の型の所有者。|  
|TYPE\_NAME|String|引数の型の名前。  パッケージ ローカル型である \(パッケージ指定で宣言されている\) 場合、この列にはパッケージ名が表示されます。|  
|TYPE\_SUBNAME|String|パッケージ ローカル型にのみ関係します。  TYPE\_NAME 列で特定されたパッケージで宣言された型の名前が表示されます。|  
|TYPE\_LINK|String|TYPE\_NAME 列で特定されたパッケージがリモート パッケージである場合は、パッケージ ローカル型のみに関係します。  この列には、リモート パッケージの参照に使用されるデータベース リンクが表示されます。|  
|PLS\_TYPE|String|数値引数の場合、引数の PL\/SQL 型の名前を示します。  その他の場合は NULL が返されます。|  
|CHAR\_LENGTH|Decimal \(10 進数型\)|文字列データ型の文字数制限。|  
|CHAR\_USED|String|文字列のバイト数制限 \(B\) または文字数制限 \(C\) が正式であるかどうかを示します。|  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)