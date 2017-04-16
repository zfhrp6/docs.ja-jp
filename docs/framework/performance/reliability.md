---
title: "信頼性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード, 信頼性"
  - "マネージ コード, 信頼性"
  - "信頼性 [.NET Framework]"
  - "SQL Server [.NET Framework]"
  - "記述 (信頼性の高いコードを)"
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 信頼性
SQL Server などのサーバー環境で実行されるコードでは、非同期例外に対して保護することが重要です。  ここで説明する信頼性は、SQL Server に固有のものではなく、.NET Framework Version 2.0 環境で実行されるすべてのホスト用に信頼性のあるコードを記述するためのものです。  ただし、ここでは SQL Server を例として使用しています。これは、SQL Server が Version 2.0 の新しい信頼性機能を広範に利用する最初のサービスであるためです。  
  
 SQL Server で実行されるコードには、信頼性に関して他のサーバー環境よりも厳しいガイドラインを使用する必要があります。  これは、リソース使用の端に SQL Server が安定して動作させるためです。<xref:System.OutOfMemoryException> と <xref:System.Threading.ThreadAbortException> 例外が SQL Server 環境でよくあります。  一般に、このようなガイドラインでは、信頼性よりも、完全に信頼されているマネージ コードが <xref:System.AppDomain> レベルのリサイクル \(サーバーが一貫性と可用性を維持するための主要な方法\) に直面した場合に適切に失敗できるようにすることに重点が置かれています。  
  
## このセクションの内容  
 [SQL Server プログラミングとホスト保護属性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 アンマネージ コードの実行を制限するために、SQL Server が <xref:System.Security.Permissions.HostProtectionAttribute> 属性をどのように使用するかについて説明します。  
  
 [信頼性に関するベスト プラクティス](../../../docs/framework/performance/reliability-best-practices.md)  
 信頼性の要件を満たすコードを記述するためのガイドラインを示します。  
  
 [制約された実行領域](../../../docs/framework/performance/constrained-execution-regions.md)  
 制約された実行領域 \(CER: Constrained Execution Region\) の機能および動作について説明します。  
  
## 関連項目  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>