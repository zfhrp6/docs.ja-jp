---
title: "SQL-CLR Type Mapping | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# SQL-CLR Type Mapping
LINQ to SQL では、リレーショナル データベースのデータ モデルが、任意のプログラミング言語で表されるオブジェクト モデルに対応付けられています。  アプリケーションが実行されると、LINQ to SQL は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。  データベースから結果が返されると、LINQ to SQL はその結果をプログラミング言語で操作できるオブジェクトに変換し直します。  
  
 オブジェクト モデルとデータベースの間でデータを変換するには、*型マッピング*を定義する必要があります。  LINQ to SQL は型マッピングを使用して、共通言語ランタイム \(CLR\) のそれぞれの型を SQL Server の特定の型に対応付けます。  型マッピングおよびその他のマッピング情報 \(データベース構造やテーブルのリレーションシップなど\) は、オブジェクト モデル内で属性ベースの対応付けを使用して定義できます。  また、オブジェクト モデルの外部で外部マッピング ファイルを使用して指定することもできます。  詳細については、「[Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)」および「[External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。  
  
 このトピックでは、以下の点について説明します。  
  
-   [既定の型マッピング](#DefaultTypeMapping)  
  
-   [型マッピングと実行時動作の関係](#BehaviorMatrix)  
  
-   [CLR と SQL の実行時の動作の違い](#BehaviorDiffs)  
  
-   [Enum 型のマッピング](#EnumMapping)  
  
-   [数値のマッピング](#NumericMapping)  
  
-   [テキストおよび XML のマッピング](#TextMapping)  
  
-   [日付および時刻のマッピング](#DateMapping)  
  
-   [バイナリのマッピング](#BinaryMapping)  
  
-   [その他のマッピング](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## 既定の型マッピング  
 オブジェクト モデルまたは外部マッピング ファイルは、オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) または SQLMetal コマンド ライン ツールを使用して自動的に作成できます。  これらのツールの既定の型マッピングでは、SQL Server データベース内の列にマップするためにどの CLR 型を選択するかが定義されています。  これらのツールの使用方法の詳細については、「[Creating the Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)」を参照してください。  
  
 また、<xref:System.Data.Linq.DataContext.CreateDatabase%2A> メソッドを使用して、オブジェクト モデルまたは外部マッピング ファイルのマッピング情報に基づいて SQL Server データベースを作成することもできます。  <xref:System.Data.Linq.DataContext.CreateDatabase%2A> メソッドの既定の型マッピングでは、オブジェクト モデル内の CLR 型にマップするためにどの型の SQL Server 列を作成するかが定義されています。  詳細については、「[How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)」を参照してください。  
  
<a name="BehaviorMatrix"></a>   
## 型マッピングと実行時動作の関係  
 次の図は、データがデータベースから取得されるときやデータベースに保存されるときに、特定の型マッピングで行われる実行時の動作を示しています。  シリアル化を除き、LINQ to SQL では、このマトリックスに指定されていない CLR または SQL Server のデータ型のマッピングはサポートされません。  シリアル化のサポートの詳細については、「[バイナリ シリアル化](#BinarySerialization)」を参照してください。  
  
> [!NOTE]
>  一部の型マッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。  
  
### カスタム型マッピング  
 LINQ to SQL では、O\/R デザイナー、SQLMetal、および <xref:System.Data.Linq.DataContext.CreateDatabase%2A> メソッドで使用される既定の型マッピング以外も使用できます。  DBML ファイルで明示的に指定すると、カスタム型マッピングを作成できます。  次に、その DBML ファイルを使用してオブジェクト モデル コードとマッピング ファイルを作成できます。  詳細については、「[SQL\-CLR Custom Type Mappings](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md)」を参照してください。  
  
<a name="BehaviorDiffs"></a>   
## CLR と SQL の実行時の動作の違い  
 CLR と SQL Server では有効桁数や実行方法が異なるため、計算を実行する場所によって、得られる結果や動作が異なる場合があります。  LINQ to SQL クエリで実行される計算は、実際は Transact\-SQL に変換されてから SQL Server データベースで実行されます。  LINQ to SQL クエリの外部で実行される計算は、CLR のコンテキスト内で実行されます。  
  
 CLR および SQL Server 間での動作の違いの例を次に示します。  
  
-   SQL Server では、一部のデータ型が、CLR の対応する型のデータとは異なる順序で並べ替えられます。  たとえば、SQL Server の `UNIQUEIDENTIFIER` 型のデータは、CLR の <xref:System.Guid?displayProperty=fullName> 型のデータとは異なる順序で並べ替えられます。  
  
-   SQL Server では、一部の文字列比較操作の処理が CLR とは異なります。  SQL Server での文字列比較の動作は、サーバー上の照合順序の設定によって決まります。  詳細については、Microsoft SQL Server オンライン ブックの「[照合順序の使用](http://go.microsoft.com/fwlink/?LinkId=115330)」を参照してください。  
  
-   SQL Server では、マップされている一部の関数で、CLR とは異なる値が返されることがあります。  たとえば、末尾の空白文字のみが異なる 2 つの文字列を等価関数で比較した場合、SQL Server では等しいと見なされるのに対し、CLR では等しくないと見なされます。  
  
<a name="EnumMapping"></a>   
## Enum 型のマッピング  
 LINQ to SQL では、CLR の <xref:System.Enum?displayProperty=fullName> 型の SQL Server 型へのマッピングが 2 種類サポートされています。  
  
-   SQL 数値型 \(`TINYINT`、`SMALLINT`、`INT`、`BIGINT`\) へのマッピング  
  
     CLR <xref:System.Enum?displayProperty=fullName> 型を SQL 数値型にマップすると、基になる CLR <xref:System.Enum?displayProperty=fullName> の整数値は SQL Server データベース列の値にマップされます。  たとえば、<xref:System.Enum?displayProperty=fullName> という名前の `DaysOfWeek` に、基になる整数値が 3 である `Tue` という名前のメンバーが含まれる場合、そのメンバーはデータベース値 3 にマップされます。  
  
-   SQL テキスト型 \(`CHAR`、`NCHAR`、`VARCHAR`、`NVARCHAR`\) へのマッピング  
  
     CLR <xref:System.Enum?displayProperty=fullName> 型を SQL テキスト型にマップすると、CLR <xref:System.Enum?displayProperty=fullName> のメンバーの名前に SQL データベース値がマップされます。  たとえば、<xref:System.Enum?displayProperty=fullName> という名前の `DaysOfWeek` に、基になる整数値が 3 である `Tue` という名前のメンバーが含まれる場合、このメンバーはデータベース値 `Tue` にマップされます。  
  
> [!NOTE]
>  SQL のテキスト型を CLR の <xref:System.Enum?displayProperty=fullName> にマップする場合は、マップされる SQL 列に <xref:System.Enum> メンバーの名前のみを含めてください。  <xref:System.Enum> 型にマップされる SQL 列では、他の値はサポートされません。  
  
 O\/R デザイナーと SQLMetal コマンド ライン ツールでは、SQL の型から CLR の <xref:System.Enum> クラスへの自動的なマッピングはできません。  DBML ファイルを O\/R デザイナーと SQLMetal で使用できるようにカスタマイズして、このマッピングを明示的に設定する必要があります。  カスタム型マッピングの詳細については、「[SQL\-CLR Custom Type Mappings](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md)」を参照してください。  
  
 列挙を目的とする SQL の列は、他の数値やテキストの列と型が同じであるため、これらのツールはユーザーの意図を認識できず、次の「[数値のマッピング](#NumericMapping)」と「[テキストおよび XML のマッピング](#TextMapping)」のセクションで説明するように既定のマッピングを使用します。  DBML ファイルを使用したコード生成の詳細については、「[Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)」を参照してください。  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドでは、CLR の <xref:System.Enum?displayProperty=fullName> 型をマップするために数値型の SQL 列が作成されます。  
  
<a name="NumericMapping"></a>   
## 数値のマッピング  
 LINQ to SQL では、CLR と SQL Server のさまざまな数値型をマップできます。  次の表に、O\/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。  
  
|SQL Server 型|O\/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング|  
|------------------|-------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=fullName>|  
|`TINYINT`|<xref:System.Int16?displayProperty=fullName>|  
|`INT`|<xref:System.Int32?displayProperty=fullName>|  
|`BIGINT`|<xref:System.Int64?displayProperty=fullName>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=fullName>|  
|`MONEY`|<xref:System.Decimal?displayProperty=fullName>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=fullName>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=fullName>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=fullName>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=fullName>|  
  
 次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。  
  
|CLR 型|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> で使用される既定の SQL Server 型|  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=fullName>|`BIT`|  
|<xref:System.Byte?displayProperty=fullName>|`TINYINT`|  
|<xref:System.Int16?displayProperty=fullName>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=fullName>|`INT`|  
|<xref:System.Int64?displayProperty=fullName>|`BIGINT`|  
|<xref:System.SByte?displayProperty=fullName>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=fullName>|`INT`|  
|<xref:System.UInt32?displayProperty=fullName>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=fullName>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=fullName>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=fullName>|`REAL`|  
|<xref:System.Double?displayProperty=fullName>|`FLOAT`|  
  
 これ以外にもさまざまな数値のマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。  詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。  
  
### Decimal 型と Money 型  
 SQL Server の `DECIMAL` 型の既定の有効桁数 \(小数点の右側と左側で 18 桁\) は、対応する既定の型である CLR の <xref:System.Decima?displayProperty=fullName>l 型の有効桁数よりはるかに少なくなっています。  その結果、データベースにデータを保存するときに有効桁数が少なくなることがあります。  一方、SQL Server の `DECIMAL` 型に 29 桁を超える有効桁数が設定されている場合、その逆が発生する可能性があります。  SQL Server の `DECIMAL` 型に CLR の <xref:System.Decimal?displayProperty=fullName> より大きい有効桁数の値が設定されていると、データベースからデータを取得するときに有効桁数が少なくなることがあります。  
  
 SQL Server の `MONEY` 型と `SMALLMONEY` 型も、既定で CLR の <xref:System.Decimal?displayProperty=fullName> 型に対応付けられます。これらの型も有効桁数がはるかに少ないため、データベースにデータを保存するときにオーバーフローやデータ損失の例外が発生する可能性があります。  
  
<a name="TextMapping"></a>   
## テキストおよび XML のマッピング  
 さまざまなテキスト ベースの型および XML 型も、LINQ to SQL を使用してマップすることができます。  次の表に、O\/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。  
  
|SQL Server 型|O\/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング|  
|------------------|-------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=fullName>|  
|`NCHAR`|<xref:System.String?displayProperty=fullName>|  
|`VARCHAR`|<xref:System.String?displayProperty=fullName>|  
|`NVARCHAR`|<xref:System.String?displayProperty=fullName>|  
|`TEXT`|<xref:System.String?displayProperty=fullName>|  
|`NTEXT`|<xref:System.String?displayProperty=fullName>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=fullName>|  
  
 次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。  
  
|CLR 型|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> で使用される既定の SQL Server 型|  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=fullName>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=fullName>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=fullName>\[\]|`NVARCHAR(4000)`|  
|`Parse()` および `ToString()` を実装するカスタム型|`NVARCHAR(MAX)`|  
  
 これ以外にもさまざまなテキスト ベースおよび XML のマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。  詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。  
  
### XML 型  
 SQL Server の `XML` データ型は、Microsoft SQL Server 2005 以降で使用できます。  SQL Server の `XML` データ型は、<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument>、または <xref:System.String> にマップできます。  <xref:System.Xml.Linq.XElement> に読み込むことができない XML フラグメントが列に格納されている場合は、列を <xref:System.String> にマップして、実行時エラーを回避する必要があります。  <xref:System.String> にマップする必要がある XML フラグメントを次に示します。  
  
-   XML 要素のシーケンス  
  
-   属性  
  
-   パブリック識別子 \(PI\)  
  
-   コメント  
  
 <xref:System.Xml.Linq.XElement> および <xref:System.Xml.Linq.XDocument> は、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」で示したように SQL Server にマップすることができますが、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドには、これらの型に対する既定の SQL Server 型マッピングはありません。  
  
### カスタム型  
 クラスが `Parse()` および `ToString()` を実装している場合は、そのオブジェクトを SQL のテキスト型 \(`CHAR`、 `NCHAR`、`VARCHAR`、`NVARCHAR`、`TEXT`、`NTEXT`、`XML`\) にマップできます。  オブジェクトをデータベースに格納するには、`ToString()` から返された値をマップ先のデータベース列に送信します。  オブジェクトを再構築するには、データベースから返された文字列に対して `Parse()` を呼び出します。  
  
> [!NOTE]
>  LINQ to SQL では、<xref:System.Xml.Serialization.IXmlSerializable?displayProperty=fullName> の使用によるシリアル化はサポートされません。  
  
<a name="DateMapping"></a>   
## 日付および時刻のマッピング  
 LINQ to SQL では、SQL Server のさまざまな日付型および時刻型をマップできます。  次の表に、O\/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。  
  
|SQL Server 型|O\/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング|  
|------------------|-------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=fullName>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=fullName>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=fullName>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=fullName>|  
|`DATE`|<xref:System.DateTime?displayProperty=fullName>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=fullName>|  
  
 次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。  
  
|CLR 型|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> で使用される既定の SQL Server 型|  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=fullName>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=fullName>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=fullName>|`TIME`|  
  
 これ以外にもさまざまな日付および時刻のマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。  詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。  
  
> [!NOTE]
>  SQL Server の `DATETIME2` 型、`DATETIMEOFFSET` 型、`DATE` 型、および `TIME` 型は、Microsoft SQL Server 2008 以降で使用できます。  Microsoft .NET Framework version 3.5 SP1 以降の LINQ to SQL では、これらの新しい型へのマッピングがサポートされています。  
  
### System.Datetime  
 CLR の <xref:System.DateTime?displayProperty=fullName> 型の範囲と有効桁数の値は、`DATETIME` メソッドの既定の型マッピングである SQL Server の <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> 型の範囲と有効桁数より大きな値です。  `DATETIME` の範囲外の日付に関連する例外を回避するには、Microsoft SQL Server 2008 以降で利用できる `DATETIME2` を使用してください。  `DATETIME2` は、CLR の <xref:System.DateTime?displayProperty=fullName> の範囲と精度に対応させることができます。  
  
 SQL Server の日付には、CLR で十分にサポートされている機能である <xref:System.TimeZone> の概念がありません。  <xref:System.TimeZone> の値は、元の <xref:System.TimeZone> の情報にかかわらず、<xref:System.DateTimeKind> 変換なしでそのまま保存されます。  <xref:System.DateTime> 値がデータベースから取得される場合、その値は、<xref:System.DateTime> が <xref:System.DateTimeKind> の状態で、そのまま <xref:System.DateTimeKind> に読み込まれます。  サポートされる <xref:System.DateTime?displayProperty=fullName> メソッドの詳細については、「[System.DateTime Methods](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md)」を参照してください。  
  
### System.TimeSpan  
 Microsoft SQL Server 2008 および .NET Framework 3.5 SP1 では、CLR の <xref:System.TimeSpan?displayProperty=fullName> 型を SQL Server の `TIME` 型にマップできます。  ただし、CLR の <xref:System.TimeSpan?displayProperty=fullName> でサポートされる範囲と SQL Server `TIME` 型でサポートされる範囲には大きな差があります。  時間を表す 0 より小さい値または 23:59:59.9999999 より大きい値を SQL の `TIME` にマップすると、オーバーフロー例外が発生します。  詳細については、「[System.TimeSpan Methods](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md)」を参照してください。  
  
 Microsoft SQL Server 2000 および SQL Server 2005 では、データベース フィールドを <xref:System.TimeSpan> にマップすることはできません。  ただし、<xref:System.TimeSpan> 値を <xref:System.TimeSpan> 減算から返したり、リテラル変数またはバインド変数として式に取り込んだりできるため、<xref:System.DateTime> の操作はサポートされています。  
  
<a name="BinaryMapping"></a>   
## バイナリのマッピング  
 SQL Server のさまざまな型を CLR の <xref:System.Data.Linq.Binary?displayProperty=fullName> 型にマップすることができます。  次の表に、O\/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに、CLR の <xref:System.Data.Linq.Binary?displayProperty=fullName> 型が選択される SQL Server 型を示します。  
  
|SQL Server 型|O\/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング|  
|------------------|-------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`VARBINARY(MAX)`  属性を持つ `FILESTREAM`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=fullName>|  
  
 次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。  
  
|CLR 型|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> で使用される既定の SQL Server 型|  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=fullName>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=fullName>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>|`VARBINARY(MAX)`|  
  
 これ以外にもさまざまなバイナリのマッピングを選択できますが、一部のマッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。  詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。  
  
### SQL Server の FILESTREAM  
 `FILESTREAM` 列の `VARBINARY(MAX)` 属性は、Microsoft SQL Server 2008 以降で使用できます。.NET Framework version 3.5 SP1 以降の LINQ to SQL では、これらの属性にマップすることができます。  
  
 `VARBINARY(MAX)` 属性を持つ `FILESTREAM` 列を <xref:System.Data.Linq.Binary> オブジェクトにマップすることはできますが、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドを使用して `FILESTREAM` 属性を持つ列を自動的に作成することはできません。  `FILESTREAM` の詳細については、Microsoft SQL Server オンライン ブックの「[FILESTREAM の概要](http://go.microsoft.com/fwlink/?LinkId=115291)」を参照してください。  
  
<a name="BinarySerialization"></a>   
### バイナリ シリアル化  
 クラスが <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装している場合は、オブジェクトを SQL バイナリ フィールド \(`BINARY`、`VARBINARY`、`IMAGE`\) にシリアル化できます。  <xref:System.Runtime.Serialization.ISerializable> インターフェイスの実装方法に従って、オブジェクトのシリアル化と逆シリアル化が行われます。  詳細については、「[バイナリ シリアル化](http://go.microsoft.com/fwlink/?LinkId=115581)」を参照してください。  
  
<a name="MiscMapping"></a>   
## その他のマッピング  
 ここでは、上記以外のさまざまな型について、既定の型マッピングを示します。  次の表に、O\/R デザイナーおよび SQLMetal でデータベースに基づいてオブジェクト モデルまたは外部マッピング ファイルを作成するときに選択される CLR 型を示します。  
  
|SQL Server 型|O\/R デザイナーおよび SQLMetal で使用される既定の CLR 型マッピング|  
|------------------|-------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=fullName>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=fullName>|  
  
 次の表に、<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドで使用される既定の型マッピングを示します。既定の型マッピングでは、オブジェクト モデルまたは外部マッピング ファイルで定義された CLR 型にマップするために作成される SQL 列の型が定義されています。  
  
|CLR 型|<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> で使用される既定の SQL Server 型|  
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=fullName>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=fullName>|`SQL_VARIANT`|  
  
 LINQ to SQL では、ここに示したその他の型に対する上記以外の型マッピングはサポートされません。  詳細については、「[型マッピングと実行時動作の関係](#BehaviorMatrix)」を参照してください。  
  
## 参照  
 [Attribute\-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)   
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)   
 [SQL\-CLR Type Mismatches](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)