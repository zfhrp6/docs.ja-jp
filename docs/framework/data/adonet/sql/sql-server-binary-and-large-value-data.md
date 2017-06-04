---
title: "SQL Server のバイナリ データと大きな値のデータ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# SQL Server のバイナリ データと大きな値のデータ
SQL Server では `max` 指定子が提供されています。これにより、`varchar`、`nvarchar`、および `varbinary` データ型の記憶容量が拡張されています。  `varchar(max)`、`nvarchar(max)`、および `varbinary(max)` は、総称して大きな値のデータ型と呼びます。  大きな値のデータ型を使用すると、最大で 2^31\-1 バイトのデータを格納できます。  
  
 SQL Server 2008 では FILESTREAM 属性が導入されました。これはデータ型ではありませんが、列に定義できる属性であり、これを使用すると大きな値のデータをデータベースではなくファイル システムに格納できます。  
  
## このセクションの内容  
 [ADO.NET での大きい値 \(max\) データの変更](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 大きな値のデータ型を扱う方法について説明します。  
  
 [FILESTREAM データ](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 SQL Server 2008 で FILESTREAM 属性を使用して保存された大きな値のデータを扱う方法について説明します。  
  
## 参照  
 [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [ADO.NET における SQL Server データ操作](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)   
 [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)