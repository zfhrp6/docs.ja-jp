---
title: "方法 : 計算列を表す"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eef3d12d3b0baa849d8eee1a01a87e3c6eee1c7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="1f18d-102">方法 : 計算列を表す</span><span class="sxs-lookup"><span data-stu-id="1f18d-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="1f18d-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>計算の結果で構成される列を表す属性です。</span><span class="sxs-lookup"><span data-stu-id="1f18d-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="1f18d-104">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f18d-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1f18d-105"> では、計算列は主キーとしてサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1f18d-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="1f18d-106">計算列を表すには</span><span class="sxs-lookup"><span data-stu-id="1f18d-106">To represent a computed column</span></span>  
  
1.  <span data-ttu-id="1f18d-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="1f18d-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="1f18d-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> プロパティに数式を表す文字列を代入します。</span><span class="sxs-lookup"><span data-stu-id="1f18d-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f18d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f18d-109">See Also</span></span>  
 [<span data-ttu-id="1f18d-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="1f18d-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="1f18d-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="1f18d-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
