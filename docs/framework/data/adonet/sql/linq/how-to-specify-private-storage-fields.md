---
title: "方法 : プライベート ストレージ フィールドを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1095189eaefa8fe34dd554a982110754bb3bd135
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="91a62-102">方法 : プライベート ストレージ フィールドを指定する</span><span class="sxs-lookup"><span data-stu-id="91a62-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="91a62-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>プロパティを<xref:System.Data.Linq.Mapping.DataAttribute>属性を基になるストレージ フィールドの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="91a62-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="91a62-104">コード例については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91a62-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="91a62-105">基になるストレージ フィールドの名前を指定するには</span><span class="sxs-lookup"><span data-stu-id="91a62-105">To specify the name of an underlying storage field</span></span>  
  
1.  <span data-ttu-id="91a62-106"><xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="91a62-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="91a62-107">フィールドの名前を <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> プロパティの値として代入します。</span><span class="sxs-lookup"><span data-stu-id="91a62-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a62-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="91a62-108">See Also</span></span>  
 [<span data-ttu-id="91a62-109">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="91a62-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="91a62-110">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="91a62-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
