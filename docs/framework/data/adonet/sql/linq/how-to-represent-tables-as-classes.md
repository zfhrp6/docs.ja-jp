---
title: "方法 : クラスとしてテーブルを表す"
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
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d524daab97be56bc0b6b428b41dc1f3db2350f95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="600fe-102">方法 : クラスとしてテーブルを表す</span><span class="sxs-lookup"><span data-stu-id="600fe-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="600fe-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute>属性をデータベース テーブルに関連付けられたエンティティ クラスとしてクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="600fe-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="600fe-104">データベース テーブルにクラスを対応付けるには</span><span class="sxs-lookup"><span data-stu-id="600fe-104">To map a class to a database table</span></span>  
  
-   <span data-ttu-id="600fe-105">クラス宣言に <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="600fe-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="600fe-106">例</span><span class="sxs-lookup"><span data-stu-id="600fe-106">Example</span></span>  
 <span data-ttu-id="600fe-107">次のコードでは、`Customer` データベース テーブルに関連付けられたエンティティ クラスとして、`Customers` クラスを確立します。</span><span class="sxs-lookup"><span data-stu-id="600fe-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="600fe-108">名前が推論できる場合は、<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> プロパティを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="600fe-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="600fe-109">名前を指定しない場合は、プロパティまたはフィールドと同じ名前であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="600fe-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600fe-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="600fe-110">See Also</span></span>  
 [<span data-ttu-id="600fe-111">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="600fe-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="600fe-112">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="600fe-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
