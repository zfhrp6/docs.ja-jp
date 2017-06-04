---
title: "How to: Submit Changes to the Database | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Submit Changes to the Database
オブジェクトに加えた変更は、その数にかかわらず、メモリ内のレプリカに対してのみ反映されています。  データベースの実際のデータは変更されていません。  <xref:System.Data.Linq.DataContext> の <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を明示的に呼び出すまでは、変更内容はサーバーに送信されません。  
  
 この呼び出しを行うと、<xref:System.Data.Linq.DataContext> は、変更内容を、同等の SQL コマンドに変換します。  独自のカスタム ロジックを使用してこれらの処理をオーバーライドすることもできますが、発行の順序は、*変更プロセッサ*と呼ばれる <xref:System.Data.Linq.DataContext> のサービスによって調整されています。  イベントの順序は次のとおりです。  
  
1.  <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、一連の既知のオブジェクトをチェックして、新しいインスタンスがアタッチされているかどうかを判断します。  その場合、それらの新しいインスタンスが、一連の追跡対象オブジェクトに追加されます。  
  
2.  保留中の変更があるすべてのオブジェクトが、互いの依存関係に基づいて、オブジェクトのシーケンスに配置されます。  他のオブジェクトに依存して変更内容が決まるオブジェクトは、その依存対象の後でシーケンスに配置されます。  
  
3.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、実際の変更を送信する直前に、一連の各コマンドをカプセル化するトランザクションを開始します。  
  
4.  オブジェクトに対する変更内容が 1 つずつ SQL コマンドに変換され、サーバーに送信されます。  
  
 この時点で、データベースによってエラーが検出された場合、送信処理は中断され、例外が発生します。  データベースに加えた変更はすべてロールバックされ、送信を行わなかった場合と同じ状態になります。  この時点でも、<xref:System.Data.Linq.DataContext> には、すべての変更内容の記録がそのまま残っています。  したがって、次のコード例のように、問題を修正したうえで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を再度呼び出すことができます。  
  
## 使用例  
 一連の送信処理のトランザクションが正常に完了した場合、<xref:System.Data.Linq.DataContext> は、変更追跡情報を無視して、オブジェクトに対する変更を受け入れます。  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## 参照  
 [How to: Detect and Resolve Conflicting Submissions](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)   
 [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Making and Submitting Data Changes](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)