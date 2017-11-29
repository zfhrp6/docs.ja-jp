---
title: "方法 : 列をデータベース生成列として表す"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b36e7035b885985e70203146957cdfca92148b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="96e62-102">方法 : 列をデータベース生成列として表す</span><span class="sxs-lookup"><span data-stu-id="96e62-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="96e62-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>データベースによって生成された列を表すフィールドまたはプロパティを指定する属性。</span><span class="sxs-lookup"><span data-stu-id="96e62-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="96e62-104">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96e62-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="96e62-105">データベース生成列を表すフィールドまたはプロパティを指定するには</span><span class="sxs-lookup"><span data-stu-id="96e62-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="96e62-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="96e62-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="96e62-107">プロパティ値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="96e62-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e62-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="96e62-108">See Also</span></span>  
 [<span data-ttu-id="96e62-109">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="96e62-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="96e62-110">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="96e62-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
