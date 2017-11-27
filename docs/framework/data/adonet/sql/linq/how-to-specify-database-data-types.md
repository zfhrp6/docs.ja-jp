---
title: "方法 : データベース データ型を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d46c63f5944895311e73524a0ba31a126d768522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="882c9-102">方法 : データベース データ型を指定する</span><span class="sxs-lookup"><span data-stu-id="882c9-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="882c9-103">使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>属性を T-SQL テーブル宣言内で列を定義する正確なテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="882c9-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="882c9-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティは、<xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してデータベースのインスタンスを作成することを予定している場合のみ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="882c9-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="882c9-105">コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="882c9-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="882c9-106">データ型を T-SQL テーブルに定義するテキストを指定するには</span><span class="sxs-lookup"><span data-stu-id="882c9-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="882c9-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="882c9-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="882c9-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> プロパティの値を T-SQL で使用される正確なテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="882c9-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882c9-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="882c9-109">See Also</span></span>  
 [<span data-ttu-id="882c9-110">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="882c9-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="882c9-111">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="882c9-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
