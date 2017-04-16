---
title: "How to: Resolve Conflicts by Overwriting Database Values | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Resolve Conflicts by Overwriting Database Values
変更を再送信する前に、データベース内の予期した値と実際の値の違いを調整するために、<xref:System.Data.Linq.RefreshMode> を使用してデータベース内の値を上書きできます。  詳細については、「[Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)」を参照してください。  
  
> [!NOTE]
>  どの場合も、データベースから最新のデータを取得することで、まずクライアントのレコードが更新されます。  この処理によって、次の更新処理が同じ同時実行チェックで失敗することを防止できます。  
  
## 使用例  
 このシナリオでは、ユーザー 1 が変更を送信しようとしたときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。これは、途中でユーザー 2 が Assistant 列と Department 列を変更していたためです。  次の表は、この状況を示しています。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|ユーザー 1 およびユーザー 2 が照会した最初のデータベース状態|Alfreds|Maria|Sales|  
|ユーザー 1 が送信しようとした変更内容|Alfred||Marketing|  
|ユーザー 2 が既に送信した変更内容||Mary|サービス|  
  
 ユーザー 1 は、この競合を解決するために、データベース値を現在のクライアント メンバー値で上書きすることに決めます。  
  
 ユーザー 1 が <xref:System.Data.Linq.RefreshMode> を使用して競合を解決すると、データベース内の結果は次の表のようになります。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|競合解決後の新しい状態|Alfred<br /><br /> \(ユーザー 1 の値\)|Maria<br /><br /> \(元の値\)|Marketing<br /><br /> \(ユーザー 1 の値\)|  
  
 次のコード例は、データベース値を現在のクライアント メンバー値で上書きする方法を示しています   \(個々のメンバーの競合に対する検査やカスタム ハンドリングは行われません\)。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## 参照  
 [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)