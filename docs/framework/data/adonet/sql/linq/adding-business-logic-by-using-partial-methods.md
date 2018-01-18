---
title: "部分メソッドによるビジネス ロジックの追加"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9704ad7d4030ee85701f1f95f87c539c1fbd0122
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a>部分メソッドによるビジネス ロジックの追加
カスタマイズすることができます[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]c# のコードを生成して、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]を使用してプロジェクト*部分メソッド*です。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] から生成されるコードでは、シグネチャが部分メソッドの一部として定義されています。 このメソッドを実装する場合に、独自の部分メソッドを追加できます。 独自の実装を追加しない場合は、コンパイラで部分メソッドのシグネチャが破棄され、既定のメソッドが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で呼び出されます。  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して、妥当性検査やその他のカスタマイズをエンティティ クラスに追加できます。  
  
 たとえば、Northwind サンプル データベースの `Customer` クラスに対する既定の対応付けには次の部分メソッドが含まれます。  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 次のようなコードを独自の部分 `Customer` クラスに追加することで、独自のメソッドを実装できます。  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 このアプローチはで通常使用される[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の既定のメソッドをオーバーライドする`Insert`、 `Update`、 `Delete`、およびオブジェクトのライフ サイクル イベント中にプロパティを検証します。  
  
 詳細については、次を参照してください。[部分メソッド](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) または[partial (メソッド) (c# リファレンス)](~/docs/csharp/language-reference/keywords/partial-method.md) (C# の場合)。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、SQLMetal などのコード生成ツールによって定義される `ExampleClass` を最初に示し、次に 2 つのメソッドの 1 つだけを実装できることを示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、`Shipper` エンティティと `Order` エンティティのリレーションシップを使用します。 メソッドには部分メソッドの `InsertShipper` と `DeleteShipper` が含まれています。 これらのメソッドによって提供される既定の部分メソッドのオーバーライド[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]マッピングします。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>参照  
 [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [挿入、更新、および削除の各操作のカスタマイズ](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
