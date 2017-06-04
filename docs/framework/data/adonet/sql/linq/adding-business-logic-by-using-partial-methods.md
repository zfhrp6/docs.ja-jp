---
title: "Adding Business Logic By Using Partial Methods | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Adding Business Logic By Using Partial Methods
生成された [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C\# のコードは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]部分メソッドを使用して  *プロジェクトでカスタマイズできます。* [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] から生成されるコードでは、シグネチャが部分メソッドの一部として定義されています。  このメソッドを実装する場合に、独自の部分メソッドを追加できます。  独自の実装を追加しない場合は、コンパイラで部分メソッドのシグネチャが破棄され、既定のメソッドが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で呼び出されます。  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して、妥当性検査やその他のカスタマイズをエンティティ クラスに追加できます。  
  
 たとえば、Northwind サンプル データベースの `Customer` クラスに対する既定の対応付けには次の部分メソッドが含まれます。  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 次のようなコードを独自の部分 `Customer` クラスに追加することで、独自のメソッドを実装できます。  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 この方法は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、`Insert`、および `Update` の既定のメソッドをオーバーライドし、オブジェクトのライフ サイクル イベントの発生時にプロパティを検証するために、`Delete` で一般的に使用されます。  
  
 詳細については、「[Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)」\([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) または「[partial \(メソッド\) \(C\# リファレンス\)](../Topic/partial%20\(Method\)%20\(C%23%20Reference\).md)」\(C\#\) を参照してください。  
  
## 例  
  
### 説明  
 次の例では、SQLMetal などのコード生成ツールによって定義される `ExampleClass` を最初に示し、次に 2 つのメソッドの 1 つだけを実装できることを示します。  
  
### コード  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## 例  
  
### 説明  
 次の例では、`Shipper` エンティティと `Order` エンティティのリレーションシップを使用します。  メソッドには部分メソッドの `InsertShipper` と `DeleteShipper` が含まれています。  これらのメソッドは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の対応付けによって提供される既定の部分メソッドをオーバーライドします。  
  
### コード  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## 参照  
 [Making and Submitting Data Changes](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)   
 [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)