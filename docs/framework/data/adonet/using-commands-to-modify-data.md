---
title: "コマンドを使用したデータ変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# コマンドを使用したデータ変更
.NET Framework データ プロバイダーを使用すると、ストアド プロシージャまたはデータ定義言語のステートメント \(たとえば、CREATE TABLE、ALTER COLUMN など\) を実行して、データベースやカタログに対するスキーマ操作を実行できます。  これらのコマンドはクエリとは異なり、行を返さないため、**Command** オブジェクトでは **ExecuteNonQuery** が提供されています。  
  
 **ExecuteNonQuery** メソッドを使用すると、スキーマを変更できるだけでなく、データを変更するが行を返さない INSERT、UPDATE、DELETE などの SQL ステートメントも処理できます。  
  
 **ExecuteNonQuery** メソッドでは行は返されませんが、**Command** オブジェクトの **Parameters** コレクションを通じて入力パラメーター、出力パラメーター、および戻り値を受け渡しできます。  
  
## このセクションの内容  
 [データ ソースのデータの更新](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 データベース内のデータを変更するコマンドまたはストアド プロシージャを実行する方法について説明します。  
  
 [カタログ操作の実行](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 データベース スキーマを変更するコマンドを実行する方法について説明します。  
  
## 参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [コマンドとパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)