---
title: "サンプル プロバイダーでの SQL 生成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a7f95f7432fdac00a34e7d878ef979656a7af4e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation-in-the-sample-provider"></a>サンプル プロバイダーでの SQL 生成
[Entity Framework サンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)をサポートする ADO.NET データ プロバイダーの新しいコンポーネントを示しています、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。  これは、SQL Server 2005 データベースで動作し、System.Data.SqlClient ADO.NET 2.0 データ プロバイダーのラッパーとして実装されます。  
  
 サンプル プロバイダーの SQL 生成モジュール (DmlSqlGenerator.cs ファイルを除き、SQL Generation フォルダーにあります) では、入力として DbQueryCommandTree を使用し、単一の SQL SELECT ステートメントを生成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 ここでは、次のトピックについて説明します。  
  
 [アーキテクチャとデザイン](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [チュートリアル: SQL 生成](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>参照  
 [SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
