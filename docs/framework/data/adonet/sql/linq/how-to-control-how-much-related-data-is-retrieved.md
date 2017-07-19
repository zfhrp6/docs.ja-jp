---
title: "How to: Control How Much Related Data Is Retrieved | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Control How Much Related Data Is Retrieved
メイン ターゲットと一緒にどの関連データを取得するかを指定するには、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> メソッドを使用します。  たとえば、顧客の注文に関する情報が必要になることがわかっている場合は、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> を使用して、顧客情報と同時に注文情報を取得できます。  この方法によって、データベースへの 1 回のアクセスで 2 種類の情報セットを両方とも取得できます。  
  
> [!NOTE]
>  メイン ターゲットである顧客に関連して注文データも取得する場合など、クエリのメイン ターゲットに関連するデータを取得するには、クロス積を 1 つの大きな投影として取得する方法もあります。  ただし、多くの場合、この方法には欠点があります。  たとえば、この結果は単なる射影であり、エンティティではないため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で変更して永続化することはできません。また、不要なデータが大量に取得される可能性もあります。  
  
## 使用例  
 次の例では、クエリを実行すると、ロンドンに住んでいるすべての `Customers` のすべての `Orders` が取得されます。  その結果、それ以降 `Customer` オブジェクトの `Orders` プロパティにアクセスしても、新しいデータベース クエリは実行されません。  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## 参照  
 [Querying the Database](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)