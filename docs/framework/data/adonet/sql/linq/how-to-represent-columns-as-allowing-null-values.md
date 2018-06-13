---
title: '方法 : null 値を許可する列として列を表す'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 6700ee5d4de53dd82da29d48ca7c42785d52afc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355978"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="47ca1-102">方法 : null 値を許可する列として列を表す</span><span class="sxs-lookup"><span data-stu-id="47ca1-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="47ca1-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>属性を関連するデータベース列が null 値を保持できることを指定します。</span><span class="sxs-lookup"><span data-stu-id="47ca1-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="47ca1-104">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47ca1-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="47ca1-105">null 値を許可する列を指定するには</span><span class="sxs-lookup"><span data-stu-id="47ca1-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="47ca1-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="47ca1-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="47ca1-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> プロパティ値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="47ca1-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ca1-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="47ca1-108">See Also</span></span>  
 [<span data-ttu-id="47ca1-109">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="47ca1-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="47ca1-110">方法 : コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="47ca1-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
