---
title: "方法 : クラス メンバーとして列を表す"
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
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0e797886b5e2fedafccf08b71e8cbb2791ea72b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-class-members"></a>方法 : クラス メンバーとして列を表す
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute>フィールドまたはプロパティをデータベース列に関連付ける属性です。  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>フィールドまたはプロパティをデータベース列に対応付けるには  
  
-   プロパティまたはフィールドの宣言に <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を追加します。  
  
## <a name="example"></a>例  
 次の例では、`CustomerID` クラス内の `Customer` フィールドを `CustomerID` データベース テーブル内の `Customers` 列に対応付けます。  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 名前が推論できる場合は、<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> プロパティを指定する必要はありません。 名前を指定しない場合は、プロパティまたはフィールドと同じ名前であると見なされます。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
