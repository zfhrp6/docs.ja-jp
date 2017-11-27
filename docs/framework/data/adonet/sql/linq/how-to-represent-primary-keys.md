---
title: "方法 : 主キーを表す"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3510d52f6f6de9ee2e99ebc1e9fc6fa581d58f3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="6f843-102">方法 : 主キーを表す</span><span class="sxs-lookup"><span data-stu-id="6f843-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="6f843-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>をデータベース列に主キーを表すフィールドまたはプロパティを指定する属性。</span><span class="sxs-lookup"><span data-stu-id="6f843-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="6f843-104">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f843-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6f843-105"> では、計算列は主キーとしてサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6f843-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="6f843-106">プロパティまたはフィールドを主キーとして指定するには</span><span class="sxs-lookup"><span data-stu-id="6f843-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="6f843-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="6f843-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="6f843-108">値として `true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f843-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f843-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f843-109">See Also</span></span>  
 [<span data-ttu-id="6f843-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="6f843-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="6f843-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="6f843-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
