---
title: "接続プール | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 接続プール
データ ソースへの接続は時間のかかる処理です。  接続を開くコストを最小化するために、ADO.NET は*接続プール*と呼ばれる最適化の手法を使用しています。接続プールを使用することで、接続を開いて閉じるという処理の繰り返しによって生じるコストを最小限に抑えることができます。  接続プールは、.NET Framework データ プロバイダーに応じて異なる処理が行われます。  
  
## このセクションの内容  
 [SQL Server の接続プール \(ADO.NET\)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 接続プールの概要および [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] における接続プールの動作を説明します。  
  
 [OLE DB、ODBC、および Oracle 接続プール](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 .NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC、および .NET Framework Data Provider for Oracle の接続プールについて説明します。  
  
## 参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)