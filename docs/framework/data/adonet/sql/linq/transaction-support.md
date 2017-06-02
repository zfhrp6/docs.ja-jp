---
title: "Transaction Support | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Transaction Support
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、3 種類のトランザクション モデルがサポートされています。  チェックが行われる順に、これらのモデルを以下に示します。  
  
## 明示的なローカル トランザクション  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が呼び出されたときに <xref:System.Data.Linq.DataContext.Transaction%2A> プロパティが \(`IDbTransaction`\) トランザクションに設定されている場合、同じトランザクションのコンテキストで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出しが実行されます。  
  
 トランザクションの実行が終了したら、ユーザーがトランザクションをコミットまたはロールバックする必要があります。  トランザクションに対応する接続は、<xref:System.Data.Linq.DataContext> を構築するのに使用した接続に一致する必要があります。  異なる接続が使用されると、例外がスローされます。  
  
## 明示的な分散トランザクション  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API \(<xref:System.Data.Linq.DataContext.SubmitChanges%2A> など\) は、アクティブな <xref:System.Transactions.Transaction> のスコープ内で呼び出すことができます。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、呼び出しがトランザクションのスコープにあることを検出し、新しいトランザクションを作成しません。  この場合は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって、接続の終了も回避されます。  このようなトランザクションのコンテキストで、クエリと <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の実行が可能です。  
  
## 暗黙のトランザクション  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、呼び出しが <xref:System.Transactions.Transaction> のスコープにあるかどうか、または `Transaction` プロパティ \(`IDbTransaction`\) がユーザーによって開始されたローカル トランザクションに設定されているかどうかをチェックします。  どちらのトランザクションも見つからない場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はローカル トランザクション \(`IDbTransaction`\) を開始し、それを使用して、生成された SQL コマンドを実行します。  すべての SQL コマンドが終了すると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はローカル トランザクションをコミットして戻ります。  
  
## 参照  
 [Background Information](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [How to: Bracket Data Submissions by Using Transactions](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)