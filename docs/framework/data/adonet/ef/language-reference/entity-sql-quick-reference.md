---
title: "Entity SQL クイック リファレンス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Entity SQL クイック リファレンス
このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリのクイック リファレンスを提供します。  このトピックのクエリでは、AdventureWorks Sales Model が使用されています。  
  
## リテラル  
  
### String  
 Unicode と非 Unicode の文字列リテラルがあります。  Unicode 文字列には、  たとえば、`N'hello'` のようにします。  
  
 非 Unicode 文字列リテラルの例を次に示します。  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Output:  
  
|値|  
|-------|  
|hello|  
  
### DateTime  
 DateTime リテラルでは、日付部分と時刻部分の両方が必須です。  既定値はありません。  
  
 例:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Output:  
  
|値|  
|-------|  
|12\/25\/2006 1:01:00 AM|  
  
### 整数  
 整数リテラルには Int32 \(123\) 型、UInt32 \(123U\) 型、Int64 \(123L\) 型、および UInt64 \(123UL\) 型があります。  
  
 例:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Output:  
  
|値|  
|-------|  
|1|  
|2|  
|3|  
  
### その他  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされているその他のリテラルは、Guid、Binary、Float\/Double、Decimal、および `null` です。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の NULL リテラルは、概念モデルのその他すべての型と互換性があると見なされます。  
  
## 型コンストラクター  
  
### ROW  
 [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) は、構造的に型指定された匿名のレコード値を作成します。`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 例:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Output:  
  
|ProductID|名前|  
|---------------|--------|  
|1|Adjustable Race|  
|879|All\-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) は、次のようなコレクションを作成します。  
  
 `MULTISET(1,2,2,3)` `--same as`\-`{1,2,2,3}.`  
  
 例:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Output:  
  
|ProductID|名前|ProductNumber|…|  
|---------------|--------|-------------------|-------|  
|842|Touring\-Panniers, Large|PA\-T100|…|  
  
### Object  
 [名前付きの型コンストラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) は、`person("abc", 12)` のように、名前付きのユーザー定義オブジェクトを作成します。  
  
 例:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Output:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911\-403C\-98|1|776|...|  
|2|4911\-403C\-98|3|777|...|  
|...|...|...|...|...|  
  
## 参照  
  
### REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) は、エンティティ型のインスタンスへの参照を作成します。  たとえば、次のクエリは、Orders エンティティ セットの各 Order エンティティへの参照を返します。  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Output:  
  
|値|  
|-------|  
|1|  
|2|  
|3|  
|...|  
  
 次の例では、プロパティ抽出演算子 \(.\) を使用して、エンティティのプロパティにアクセスします。  プロパティ抽出演算子を使用すると、参照は自動的に逆参照されます。  
  
 例:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|値|  
|-------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) は参照値を逆参照し、その逆参照の結果を生成します。  たとえば、次のクエリは、`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2` のように、Orders エンティティ セットの各 Order について Order エンティティを生成します。  
  
 例:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|値|  
|-------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### CREATEREF と KEY  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) は、キーを渡す参照を作成します。  [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) は、型参照を持つ式のキー部分を抽出します。  
  
 例:  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## 関数  
  
### 正規  
 [正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)の名前空間は Edm で、`Edm.Length("string")` のように使用されます。  正規関数と同じ名前の関数を含んでいる別の名前空間がインポートされない限り、名前空間を指定する必要はありません。  2 つの名前空間に同じ関数が存在する場合は、完全な名前を指定する必要があります。  
  
 例:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Output:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### Microsoft プロバイダー固有  
 [Microsoft プロバイダー固有の関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)は、`SqlServer` 名前空間にあります。  
  
 例:  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Output:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## 名前空間  
 [USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) は、クエリ式で使用する名前空間を指定します。  
  
 例:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Output:  
  
|値|  
|-------|  
|aa|  
  
## ページング  
 ページングは、[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) および [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) サブ句を [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 句に宣言することによって表現できます。  
  
 例:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Output:  
  
|ID|名前|  
|--------|--------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## グループ化  
 [GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) は、クエリ \([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)\) 式によって返されるオブジェクトをグループ化するよう指定します。  
  
 例:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Output:  
  
|name|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## ナビゲーション  
 リレーションシップ ナビゲーション操作を使用すると、開始側のエンティティと終了側のエンティティ間のリレーションシップをナビゲートできます。  [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) は、\<namespace\>.\<relationship type name\> として修飾されるリレーションシップ型をとります。  終了側の基数が 1 の場合、Ref\<T\> が返されます。  終端の基数が n の場合、Collection\<Ref\<T\>\> が返されます。  
  
 例:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Output:  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## SELECT VALUE AND SELECT  
  
### SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、暗黙の行の構築をスキップする SELECT VALUE 句が用意されています。  SELECT VALUE 句には 1 つの項目のみを指定できます。  このような句を使用した場合、SELECT 句内の項目には row ラッパーは構築されず、`SELECT VALUE a` などの目的の構造を持つコレクションを作成できます。  
  
 例:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|名前|  
|--------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、任意の行を構築するための行コンストラクターも用意されています。  SELECT は、投影内の 1 つまたは複数の要素、および `SELECT a, b, c` などのフィールドを持つデータ レコードの結果を取得します。  
  
 例:  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|名前|ProductID|  
|--------|---------------|  
|Adjustable Race|1|  
|All\-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## CASE 式  
 [CASE 式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)は、一連のブール式を評価して結果を判定します。  
  
 例:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Output:  
  
|値|  
|-------|  
|TRUE|  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)