---
title: "SQL Server スキーマ コレクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6403cc3-d78b-4f85-bab1-ada7a3446ec5
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# SQL Server スキーマ コレクション
Microsoft .NET Framework Data Provider for SQL Server は、共通のスキーマ コレクションに加えて追加のスキーマ コレクションをサポートしています。  スキーマ コレクションは、使用している SQL Server のバージョンによって多少異なります。  サポートされるスキーマ コレクションの一覧を確認するには、引数を指定しないで、またはスキーマ コレクション名に "MetaDataCollections" を指定して **GetSchema** メソッドを呼び出します。  これにより、サポートされるスキーマ コレクションの一覧、それぞれがサポートする制限数、および使用する識別子部分の数と共に、<xref:System.Data.DataTable> が返されます。  
  
## Databases  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|database\_name|String|データベース名。|  
|Dbid|Int16|データベース ID。|  
|create\_date|DateTime|データベースの作成日。|  
  
## Foreign Keys  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|constraint\_catalog|String|制約が属するカタログ。|  
|constraint\_schema|String|制約を含むスキーマ。|  
|constraint\_name|String|名前。|  
|table\_catalog|String|制約が含まれるテーブル名。|  
|table\_schema|String|テーブルを含むスキーマ。|  
|table\_name|String|テーブル名|  
|constraint\_type|String|制約の型。  "FOREIGN KEY" だけが許可されています。|  
|is\_deferrable|String|制約を遅延可能にするかどうかを指定します。  NO が返されます。|  
|initially\_deferred|String|制約を最初に遅延可能にするかどうかを指定します。  NO が返されます。|  
  
## Indexes  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|constraint\_catalog|String|インデックスが属するカタログ。|  
|constraint\_schema|String|インデックスを含むスキーマ。|  
|constraint\_name|String|インデックス名。|  
|table\_catalog|String|インデックスが関連付けられているテーブル名。|  
|table\_schema|String|インデックスが関連付けられているテーブルを含むスキーマ。|  
|table\_name|String|テーブル名。|  
  
### Indexes \(SQL Server 2008\)  
 .NET Framework 3.5 SP1 および SQL Server 2008 以降では、新しい空間型、ファイルストリーム、およびスパース列をサポートするために、以下の列が Indexes スキーマ コレクションに追加されています。  これらの列は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|type\_desc|String|インデックスの種類。次のいずれかの値になります。<br /><br /> -   HEAP<br />-   CLUSTERED<br />-   NONCLUSTERED<br />-   XML<br />-   SPATIAL|  
  
## IndexColumns  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|constraint\_catalog|String|インデックスが属するカタログ。|  
|constraint\_schema|String|インデックスを含むスキーマ。|  
|constraint\_name|String|インデックス名。|  
|table\_catalog|String|インデックスが関連付けられているテーブル名。|  
|table\_schema|String|インデックスが関連付けられているテーブルを含むスキーマ。|  
|table\_name|String|テーブル名。|  
|column\_name|String|インデックスが関連付けられている列名。|  
|ordinal\_position|Int32|列の位置を示す序数。|  
|KeyType|UInt16|オブジェクトの型。|  
  
## 手順  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|specific\_catalog|String|カタログ固有の名前。|  
|specific\_schema|String|スキーマ固有の名前。|  
|specific\_name|String|カタログ固有の名前。|  
|routine\_catalog|String|ストアド プロシージャが属するカタログ。|  
|routine\_schema|String|ストアド プロシージャを含むスキーマ。|  
|routine\_name|String|ストアド プロシージャの名前。|  
|routine\_type|String|ストアド プロシージャには PROCEDURE が返され、関数には FUNCTION が返されます。|  
|created|DateTime|プロシージャが作成された日時。|  
|last\_altered|DateTime|プロシージャの最終更新日時。|  
  
## Procedure Parameters  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|specific\_catalog|String|このパラメーターを受け取るプロシージャのカタログ名。|  
|specific\_schema|String|このパラメーターを受け取るプロシージャを含むスキーマ。|  
|specific\_name|String|このパラメーターを受け取るとるプロシージャ名。|  
|ordinal\_position|Int16|パラメーターの位置を示す 1 から始まる序数。  プロシージャの戻り値については 0 になります。|  
|parameter\_mode|String|入力パラメーターでは IN が返され、出力パラメーターでは OUT が返され、I\/O パラメーターでは INOUT が返されます。|  
|is\_result|String|プロシージャの結果が関数を表す場合には YES が返されます。  その他の場合は NO が返されます。|  
|as\_locator|String|ロケーターとして宣言された場合は YES が返されます。  その他の場合は NO が返されます。|  
|parameter\_name|String|パラメーターの名前。  関数の戻り値に相当する場合は NULL になります。|  
|data\_type|String|システムにより提供されるデータ型。|  
|character\_maximum\_length|Int32|バイナリまたは文字データ型の文字列の最大長。  その他の場合は NULL が返されます。|  
|character\_octet\_length|Int32|バイナリまたは文字データ型の最大バイト数。  その他の場合は NULL が返されます。|  
|collation\_catalog|String|パラメーター照合のカタログ名。  文字型の 1 つでない場合は、NULL が返されます。|  
|collation\_schema|String|常に NULL が返されます。|  
|collation\_name|String|パラメーター照合の名前。  文字型の 1 つでない場合は、NULL が返されます。|  
|character\_set\_catalog|String|パラメーターの文字セットのカタログ名。  文字型の 1 つでない場合は、NULL が返されます。|  
|character\_set\_schema|String|常に NULL が返されます。|  
|character\_set\_name|String|パラメーターの文字セット名。  文字型の 1 つでない場合は、NULL が返されます。|  
|numeric\_precision|Byte|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数。  その他の場合は NULL が返されます。|  
|numeric\_precision\_radix|Int16|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数の基数。  その他の場合は NULL が返されます。|  
|numeric\_scale|Int32|数値データの概数、正確な数値データ、整数データ、または通貨データの桁数。  その他の場合は NULL が返されます。|  
|datetime\_precision|Int16|パラメーターの型が datetime または smalldatetime である場合の秒数の小数部の有効桁数。  その他の場合は NULL が返されます。|  
|interval\_type|String|NULL。  将来 SQL Server で使用するために予約されています。|  
|interval\_precision|Int16|NULL。  将来 SQL Server で使用するために予約されています。|  
  
## \[テーブル\]  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|table\_catalog|String|テーブルのカタログ。|  
|table\_schema|String|テーブルを含むスキーマ。|  
|table\_name|String|テーブル名。|  
|table\_type|String|テーブルの型。  VIEW または BASE TABLE のいずれかです。|  
  
## 列  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|table\_catalog|String|テーブルのカタログ。|  
|table\_schema|String|テーブルを含むスキーマ。|  
|table\_name|String|テーブル名。|  
|column\_name|String|列名。|  
|ordinal\_position|Int16|列の識別番号。|  
|column\_default|String|列の既定値。|  
|is\_nullable|String|列に NULL 値が許容されるかどうかを指定します。  この列に NULL が許容される場合は、YES が返されます。  その他の場合は NO が返されます。|  
|data\_type|String|システムにより提供されるデータ型。|  
|character\_maximum\_length|Int32 – Sql8、Int16 – Sql7|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大文字列長。  その他の場合は NULL が返されます。|  
|character\_octet\_length|Int32 – SQL8、Int16 – Sql7|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大バイト長。  その他の場合は NULL が返されます。|  
|numeric\_precision|Unsigned Byte|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数。  その他の場合は NULL が返されます。|  
|numeric\_precision\_radix|Int16|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数の基数。  その他の場合は NULL が返されます。|  
|numeric\_scale|Int32|数値データの概数、正確な数値データ、整数データ、または通貨データの桁数。  その他の場合は NULL が返されます。|  
|datetime\_precision|Int16|日付時刻データ型および SQL\-92 interval データ型のサブタイプ コード。  その他のデータ型に対しては NULL が返されます。|  
|character\_set\_catalog|String|列が文字データ型またはテキスト データ型である場合は、文字セットがあるデータベースを示すマスターが返されます。  その他の場合は NULL が返されます。|  
|character\_set\_schema|String|常に NULL が返されます。|  
|character\_set\_name|String|この列が文字データ型またはテキスト データ型である場合、文字セットの一意の名前が返されます。  その他の場合は NULL が返されます。|  
|collation\_catalog|String|列が文字データ型またはテキスト データ型である場合は、照合順序が定義されているデータベースを示すマスターが返されます。  その他の場合、この列は NULL になります。|  
  
### Columns \(SQL Server 2008\)  
 .NET Framework version 3.5 SP1 および SQL Server 2008 以降では、新しい空間型、filestream、およびスパース列をサポートするために、以下の列が Columns スキーマ コレクションに追加されています。  これらの列は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|IS\_FILESTREAM|String|列に FILESTREAM 属性がある場合は YES。<br /><br /> 列には FILESTREAM 属性がない場合は NO。|  
|IS\_SPARSE|String|列がスパース列である場合は YES。<br /><br /> 列がスパース列でない場合は NO。|  
|IS\_COLUMN\_SET|String|列が列セットの列である場合は YES。<br /><br /> 列が列セットの列でない場合は NO。|  
  
### AllColumns \(SQL Server 2008\)  
 .NET Framework version 3.5 SP1 および SQL Server 2008 以降では、スパース列をサポートするために、AllColumns スキーマ コレクションが追加されています。  AllColumns は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。  
  
 AllColumns の制限と生成される DataTable スキーマは、Columns スキーマ コレクションと同じです。  相違は、Columns スキーマ コレクションに含まれていない列セットの列が AllColumns に含まれている点のみです。  次の表では、それらの列について説明します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|table\_catalog|String|テーブルのカタログ。|  
|table\_schema|String|テーブルを含むスキーマ。|  
|table\_name|String|テーブル名。|  
|column\_name|String|列名。|  
|ordinal\_position|Int16|列の識別番号。|  
|column\_default|String|列の既定値。|  
|is\_nullable|String|列に NULL 値が許容されるかどうかを指定します。  この列に NULL が許容される場合は、YES が返されます。  その他の場合は NO が返されます。|  
|data\_type|String|システムにより提供されるデータ型。|  
|character\_maximum\_length|Int32|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大文字列長。  その他の場合は NULL が返されます。|  
|character\_octet\_length|Int32|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大バイト長。  その他の場合は NULL が返されます。|  
|numeric\_precision|Unsigned Byte|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数。  その他の場合は NULL が返されます。|  
|numeric\_precision\_radix|Int16|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数の基数。  その他の場合は NULL が返されます。|  
|numeric\_scale|Int32|数値データの概数、正確な数値データ、整数データ、または通貨データの桁数。  その他の場合は NULL が返されます。|  
|datetime\_precision|Int16|日付時刻データ型および SQL\-92 interval データ型のサブタイプ コード。  その他のデータ型に対しては NULL が返されます。|  
|character\_set\_catalog|String|列が文字データ型またはテキスト データ型である場合は、文字セットがあるデータベースを示すマスターが返されます。  その他の場合は NULL が返されます。|  
|character\_set\_schema|String|常に NULL が返されます。|  
|character\_set\_name|String|この列が文字データ型またはテキスト データ型である場合、文字セットの一意の名前が返されます。  その他の場合は NULL が返されます。|  
|collation\_catalog|String|列が文字データ型またはテキスト データ型である場合は、照合順序が定義されているデータベースを示すマスターが返されます。  その他の場合、この列は NULL になります。|  
|IS\_FILESTREAM|String|列に FILESTREAM 属性がある場合は YES。<br /><br /> 列には FILESTREAM 属性がない場合は NO。|  
|IS\_SPARSE|String|列がスパース列である場合は YES。<br /><br /> 列がスパース列でない場合は NO。|  
|IS\_COLUMN\_SET|String|列が列セットの列である場合は YES。<br /><br /> 列が列セットの列でない場合は NO。|  
  
### ColumnSetColumns \(SQL Server 2008\)  
 .NET Framework version 3.5 SP1 および SQL Server 2008 以降では、スパース列をサポートするために、ColumnSetColumns スキーマ コレクションが追加されています。  ColumnSetColumns は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。  ColumnSetColumns スキーマ コレクションは、列セット内のすべての列のスキーマを返します。  次の表では、それらの列について説明します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|table\_catalog|String|テーブルのカタログ。|  
|table\_schema|String|テーブルを含むスキーマ。|  
|table\_name|String|テーブル名。|  
|column\_name|String|列名。|  
|ordinal\_position|Int16|列の識別番号。|  
|column\_default|String|列の既定値。|  
|is\_nullable|String|列に NULL 値が許容されるかどうかを指定します。  この列に NULL が許容される場合は、YES が返されます。  その他の場合は NO が返されます。|  
|data\_type|String|システムにより提供されるデータ型。|  
|character\_maximum\_length|Int32|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大文字列長。  その他の場合は NULL が返されます。|  
|character\_octet\_length|Int32|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大バイト長。  その他の場合は NULL が返されます。|  
|numeric\_precision|Unsigned Byte|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数。  その他の場合は NULL が返されます。|  
|numeric\_precision\_radix|Int16|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数の基数。  その他の場合は NULL が返されます。|  
|numeric\_scale|Int32|数値データの概数、正確な数値データ、整数データ、または通貨データの桁数。  その他の場合は NULL が返されます。|  
|datetime\_precision|Int16|日付時刻データ型および SQL\-92 interval データ型のサブタイプ コード。  その他のデータ型に対しては NULL が返されます。|  
|character\_set\_catalog|String|列が文字データ型またはテキスト データ型である場合は、文字セットがあるデータベースを示すマスターが返されます。  その他の場合は NULL が返されます。|  
|character\_set\_schema|String|常に NULL が返されます。|  
|character\_set\_name|String|この列が文字データ型またはテキスト データ型である場合、文字セットの一意の名前が返されます。  その他の場合は NULL が返されます。|  
|collation\_catalog|String|列が文字データ型またはテキスト データ型である場合は、照合順序が定義されているデータベースを示すマスターが返されます。  その他の場合、この列は NULL になります。|  
|IS\_FILESTREAM|String|列に FILESTREAM 属性がある場合は YES。<br /><br /> 列には FILESTREAM 属性がない場合は NO。|  
|IS\_SPARSE|String|列がスパース列である場合は YES。<br /><br /> 列がスパース列でない場合は NO。|  
|IS\_COLUMN\_SET|String|列が列セットの列である場合は YES。<br /><br /> 列が列セットの列でない場合は NO。|  
  
## Users  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|uid|Int16|このデータベースで一意のユーザー ID。  1 はデータベースの所有者です。|  
|name|String|このデータベースで一意のユーザー名またはグループ名。|  
|createdate|DateTime|アカウントが追加された日付。|  
|updatedate|DateTime|アカウントが最後に変更された日付。|  
  
## ビュー  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|table\_catalog|String|ビューのカタログ。|  
|table\_schema|String|ビューを含むスキーマ。|  
|table\_name|String|ビューの名前。|  
|check\_option|String|WITH CHECK OPTION の型。  元のビューが WITH CHECK OPTION を使用して作成されている場合は CASCADE になります。  その他の場合は NONE が返されます。|  
|is\_updatable|String|ビューが更新可能であるかどうかを指定します。  常に NO が返されます。|  
  
## ViewColumns  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|view\_catalog|String|ビューのカタログ。|  
|view\_schema|String|ビューを含むスキーマ。|  
|view\_name|String|ビューの名前。|  
|table\_catalog|String|このビューに関連付けられているテーブルのカタログ。|  
|table\_schema|String|このビューに関連付けられているテーブルを含むスキーマ。|  
|table\_name|String|ビューに関連付けられているテーブルの名前。  ベース テーブルになります。|  
|column\_name|String|列名。|  
  
## UserDefinedTypes  
  
|ColumnName|DataType|説明|  
|----------------|--------------|--------|  
|assembly\_name|String|アセンブリのファイル名。|  
|UDT\_name|String|アセンブリのクラス名。|  
|version\_major|Object|メジャー バージョン番号。|  
|version\_minor|Object|マイナー バージョン番号。|  
|version\_build|Object|ビルド番号。|  
|version\_revision|Object|リビジョン番号。|  
|Culture\_info|Object|この UDT に関連付けられているカルチャ情報。|  
|Public\_key|Object|このアセンブリで使用される公開キー。|  
|Is\_fixed\_length|Boolean|型の長さを max\_length と常に同じにするかどうかを指定します。|  
|max\_length|Int16|型の最大長 \(バイト単位\)。|  
|permission\_set\_desc|String|アセンブリのアクセス許可セット\/セキュリティ レベルのフレンドリ名。|  
|create\_date|DateTime|アセンブリが作成\/登録された日付。|  
  
## 参照  
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)