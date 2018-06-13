---
title: DataSet の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 3c48b430b1a087a79db37398b2c68014b8077c55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755966"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="c446b-102">DataSet の作成</span><span class="sxs-lookup"><span data-stu-id="c446b-102">Creating a DataSet</span></span>
<span data-ttu-id="c446b-103"><xref:System.Data.DataSet> のインスタンスを作成するには、<xref:System.Data.DataSet> のコンストラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c446b-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="c446b-104">必要に応じて、引数 name を指定します。</span><span class="sxs-lookup"><span data-stu-id="c446b-104">Optionally specify a name argument.</span></span> <span data-ttu-id="c446b-105">名前を指定しない場合、<xref:System.Data.DataSet> の名前は "NewDataSet" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c446b-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="c446b-106">また、既存の <xref:System.Data.DataSet> に基づいて新しい <xref:System.Data.DataSet> を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c446b-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c446b-107">既存の <xref:System.Data.DataSet> の正確なコピーを新しい <xref:System.Data.DataSet> として作成できるのは、リレーショナル構造またはスキーマはコピーするけれども既存の <xref:System.Data.DataSet> からのデータは含まない <xref:System.Data.DataSet> のクローン、または <xref:System.Data.DataSet> メソッドを使用して既存の <xref:System.Data.DataSet> から変更された行だけを含む <xref:System.Data.DataSet.GetChanges%2A> のサブセットのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="c446b-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="c446b-108">詳細については、次を参照してください。 [DataSet の内容をコピー](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)です。</span><span class="sxs-lookup"><span data-stu-id="c446b-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="c446b-109"><xref:System.Data.DataSet> のインスタンスの作成方法を示すコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c446b-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="c446b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c446b-110">See Also</span></span>  
 [<span data-ttu-id="c446b-111">DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="c446b-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="c446b-112">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="c446b-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="c446b-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="c446b-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
