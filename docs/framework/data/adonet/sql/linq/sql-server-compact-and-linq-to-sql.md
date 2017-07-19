---
title: "SQL Server Compact and LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# SQL Server Compact and LINQ to SQL
SQL Server Compact は、Visual Studio と共にインストールされる既定のデータベースです。詳細については、「[PAVE OVER Using SQL Server Compact \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/13320dd1-94e5-4077-bf76-8df253695ccc)」を参照してください。  
  
 このトピックでは、使用法、構成、機能セット、および [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] サポートのスコープに関する主要な相違を示します。  
  
## LINQ to SQL との関係における SQL Server Compact の特徴  
 既定では、SQL Server Compact はすべての [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] エディションでインストールされるため、開発コンピューター上の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で使用できます。  しかし、SQL Server Compact と [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用するアプリケーションの配置は、[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] アプリケーションの場合とは異なります。  SQL Server Compact は .NET Framework の一部ではないため、アプリケーションにパッケージ化するか、Microsoft サイトから個別にダウンロードする必要があります。  
  
 これには、次のような特徴があります。  
  
-   SQL Server Compact は DLL としてパッケージ化されており、データベース ファイル \(.sdf 拡張子\) に対して直接使用できます。  
  
-   SQL Server Compact は、クライアント アプリケーションと同じプロセスで実行されます。  そのため、SQL Server Compact と通信する方が [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] と通信するより効率的に優れています。  一方、SQL Server Compact では、コストを伴うマネージ コードとアンマネージ コード間の相互運用性が必要です。  
  
-   SQL Server Compact DLL のサイズはわずかです。  このため、アプリケーション全体のサイズが抑制されます。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムおよび SQLMetal コマンド ライン ツールが SQL Server Compact をサポートしています。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] では、SQL Server Compact はサポートしていません。  
  
## 機能セット  
 SQL Server Compact の機能セットは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションに影響を及ぼす次の点で、[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] の機能セットより単純です。  
  
-   SQL Server Compact は、ストアド プロシージャまたはビューをサポートしません。  
  
-   SQL Server Compact は、一部のデータ型と SQL 関数のみをサポートします。  
  
-   SQL Server Compact は、一部の SQL コンストラクトのみをサポートします。  
  
-   SQL Server Compact は、最小限のオプティマイザーを備えています。  クエリによってはタイムアウトする場合もあります。  
  
-   SQL Server Compact は、部分信頼をサポートしません。  
  
## 参照  
 [Reference](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)