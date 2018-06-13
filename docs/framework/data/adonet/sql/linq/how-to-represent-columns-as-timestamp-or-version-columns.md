---
title: '方法 : 列をタイムスタンプ列またはバージョン列として表現する'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 2fc8aaf260dc3657e33e539939fdf58ad8224c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361240"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="d35e6-102">方法 : 列をタイムスタンプ列またはバージョン列として表現する</span><span class="sxs-lookup"><span data-stu-id="d35e6-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="d35e6-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>のプロパティ、<xref:System.Data.Linq.Mapping.ColumnAttribute>データベース タイムスタンプまたはバージョン番号を保持するデータベース列を表すフィールドまたはプロパティを指定する属性。</span><span class="sxs-lookup"><span data-stu-id="d35e6-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="d35e6-104">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d35e6-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="d35e6-105">タイムスタンプ列またはバージョン列を表すフィールドまたはプロパティを指定するには</span><span class="sxs-lookup"><span data-stu-id="d35e6-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="d35e6-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="d35e6-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="d35e6-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> プロパティ値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d35e6-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35e6-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="d35e6-108">See Also</span></span>  
 [<span data-ttu-id="d35e6-109">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="d35e6-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="d35e6-110">方法 : 同時実行の競合を検査するメンバーを指定する</span><span class="sxs-lookup"><span data-stu-id="d35e6-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="d35e6-111">方法 : コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="d35e6-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
