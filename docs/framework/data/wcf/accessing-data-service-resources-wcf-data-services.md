---
title: "データ サービス リソースへのアクセス (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "概要, WCF Data Services"
  - "データ サービスのクエリ [WCF Data Services]"
  - "WCF Data Services, データへのアクセス"
  - "WCF Data Services, 概要"
  - "WCF Data Services, 照会"
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# データ サービス リソースへのアクセス (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、URI でアドレス指定できるリソースを使用し、データをフィードとして公開する [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] をサポートしています。  これらのリソースは、[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) のエンティティとリレーションシップの規則に従って表現されます。  このモデルでは、エンティティはアプリケーション ドメイン内のデータの操作単位 \(データ型\) を表します \(顧客、注文、項目、製品など\)。  エンティティ データは、Representational State Transfer \(REST\) のセマンティクス \(特に、標準的な HTTP 動詞である GET、PUT、POST、および DELETE\) を使用してアクセスおよび変更できます。  
  
## リソースへの対処  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、データ モデルによって公開されたデータを、URI を使用してアドレス指定します。  たとえば、次の URI は Customers エンティティ セットであるフィードを返します。このフィードには、Customer エンティティ型のすべてのインスタンスのエントリが含まれています。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 エンティティには、エンティティ キーという特別なプロパティがあります。  エンティティ キーは、エンティティ セット内の 1 つのエンティティを一意に識別するために使用されます。  そのため、エンティティ セット内のエンティティ型の特定のインスタンスのアドレスを指定できます。  たとえば、次の URI は、`ALFKI` のキー値のある Customer エンティティ型の特定のインスタンスのエントリを返します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 エンティティ インスタンスのプリミティブ プロパティおよび複合プロパティは、個別にアドレス指定することもできます。  たとえば、次の URI は特定の Customer の `ContactName` プロパティ値が含まれた XML 要素を返します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 前の URI に `$value` エンドポイントを含めた場合、応答メッセージにはプリミティブ プロパティの値のみが返されます。  次の例では、XML 要素のない "Maria Anders" という文字列のみが返されます。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 エンティティ間のリレーションシップは、アソシエーションによってデータ モデル内で定義されます。  これらのアソシエーションによって、エンティティ インスタンスのナビゲーション プロパティを使用して関連エンティティをアドレス指定することが可能になります。  ナビゲーション プロパティは、単一の関連エンティティ \(多対一のリレーションシップの場合\) または関連エンティティのセット \(一対多のリレーションシップの場合\) のいずれかを返します。  たとえば、次の URI は、特定の Customer に関連付けられたすべての Orders のセットであるフィードを返します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 リレーションシップは通常は双方向であり、ナビゲーション プロパティのペアで表されます。  前の例で示したリレーションシップとは逆に、次の URI は特定の Order エンティティが属する Customer エンティティへの参照を返します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、クエリ式の結果に基づいてリソースのアドレスを指定できます。  その結果、評価された式に基づいてリソースのセットをフィルターすることが可能になります。  たとえば、次の URI は、リソースをフィルターして特定の Customer に 1997 年 9 月 22 日以降に出荷された Orders だけを返します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 詳細については、「[OData: URI 規則](http://go.microsoft.com/fwlink/?LinkId=185564)」を参照してください。  
  
## System Query Options \(システム クエリ オプション\)  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では一連のシステム クエリ オプションが定義されており、フィルター処理、並べ替え、ページングなど、リソースに対する従来のクエリ操作の実行に使用できます。  たとえば、次の URI は、郵便番号 \(postal code\) の末尾が `100` ではないすべての `Order` エンティティのセットを、関連する `Order_Detail` エンティティと共に返します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 返されたフィードのエントリは、注文の ShipCity プロパティの値でも並べ替えられています。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、次の [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] システム クエリ オプションをサポートしています。  
  
|クエリ オプション|説明|  
|---------------|--------|  
|`$orderby`|返されるフィードのエンティティについて、既定の並べ替え順序を定義します。  次のクエリで返される Customers フィードは、国 \(County\) と都市 \(City\) で並べ替えられています。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> 詳細については、「[OData: OrderBy システム クエリ オプション \($orderby\)](http://go.microsoft.com/fwlink/?LinkId=186968)」を参照してください。|  
|`$top`|返されるフィードに含まれるエンティティの数を指定します。  次の例では、最初の 10 件の顧客をスキップし、その次の 10 件を返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> 詳細については、「[OData: Top システム クエリ オプション \($top\)](http://go.microsoft.com/fwlink/?LinkId=186969)」を参照してください。|  
|`$skip`|フィードにエンティティを返し始めるまでにスキップするエンティティの数を指定します。  次の例では、最初の 10 件の顧客をスキップし、その次の 10 件を返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> 詳細については、「[OData: Skip システム クエリ オプション \($skip\)](http://go.microsoft.com/fwlink/?LinkId=186971)」を参照してください。|  
|`$filter`|フィードに返されるエンティティを特定の条件に基づいてフィルターする式を定義します。  このクエリ オプションは、フィルター式の評価に使用される一連の論理比較演算子、算術演算子、および定義済みクエリ関数をサポートします。  次の例は、郵便番号の末尾が 100 でないすべての注文を返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> 詳細については、「[OData: Filter システム クエリ オプション \($filter\)](http://go.microsoft.com/fwlink/?LinkId=186972)」を参照してください。|  
|`$expand`|クエリで返される関連エンティティを指定します。  関連エンティティは、クエリで返されるエンティティにフィードまたはエントリとしてインラインで含まれています。  次の例では、顧客 'ALFKI' の注文を各注文の品目の詳細と共に返します。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> 詳細については、「[OData: Expand システム クエリ オプション \($expand\)](http://go.microsoft.com/fwlink/?LinkId=186973)」を参照してください。|  
|`$select`|フィードとして返されるエンティティのプロパティを指定します。  既定では、エンティティのすべてのプロパティがフィードとして返されます。  次のクエリでは、`Customer` エンティティの 3 つのプロパティが返されます。<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> 詳細については、「[OData: Select システム クエリ オプション \($select\)](http://go.microsoft.com/fwlink/?LinkID=186076)」を参照してください。|  
|`$inlinecount`|フィードで返されるエンティティの数のカウントがフィードに含まれるように要求します。  詳細については、「[OData: Inlinecount システム クエリ オプション \($inlinecount\)](http://go.microsoft.com/fwlink/?LinkId=186975)」を参照してください。|  
  
## リレーションシップのアドレス指定  
 エンティティ セットとエンティティ インスタンスのアドレス指定に加えて、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、2 つのエンティティ間のリレーションシップを表すアソシエーションのアドレスを指定することもできます。  この機能は、2 つのエンティティ インスタンス \(Northwind サンプル データベースの注文に関連付けられた配送会社など\) の間のリレーションシップを作成または変更するために必要です。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は、エンティティ間のアソシエーションをアドレス指定する `$link` 演算子をサポートします。  たとえば、次の URI を HTTP PUT 要求メッセージで指定した場合、指定した注文の配送会社を新しい配送会社に変更します。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 詳細については、「[OData: エントリ間のリンクのアドレス指定](http://go.microsoft.com/fwlink/?LinkId=187351)」を参照してください。  
  
## 返されたフィードの使用  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] リソースの URI を使用すると、サービスによって公開されるエンティティ データのアドレスを指定できます。  Web ブラウザーの \[アドレス\] フィールドに URI を入力すると、要求されたリソースの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィード表現が返されます。  詳細については、「[WCF Data Services クイックスタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)」を参照してください。  Web ブラウザーはデータ サービス リソースが予期されたデータを返すかどうかをテストするために便利ですが、データの作成、更新、および削除も行うことができる運用データ サービスには、一般的にアプリケーション コードや Web ページのスクリプト言語を使用してアクセスします。  詳細については、「[クライアント アプリケーションでのデータ サービスの使用](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)」を参照してください。  
  
## 参照  
 [Open Data Protocol Web サイト](http://go.microsoft.com/fwlink/?LinkID=182204)