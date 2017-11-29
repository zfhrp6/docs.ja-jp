---
title: "DataTable の移動"
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
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cecceb94caf4d1c0a9a05c48485f7e79a70bfce6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="navigating-datatables"></a><span data-ttu-id="f52f6-102">DataTable の移動</span><span class="sxs-lookup"><span data-stu-id="f52f6-102">Navigating DataTables</span></span>
<span data-ttu-id="f52f6-103"><xref:System.Data.DataTableReader> は、1 つ以上の <xref:System.Data.DataTable> オブジェクトの内容を、読み取り専用、前方参照専用の 1 つ以上の結果セットとして取得します。</span><span class="sxs-lookup"><span data-stu-id="f52f6-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f52f6-104"><xref:System.Data.DataTableReader> メソッドの呼び出しにより DataTableReader を作成した場合、<xref:System.Data.DataSet.CreateDataReader%2A> に複数の結果セットが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f52f6-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="f52f6-105">結果セットが複数ある場合、<xref:System.Data.DataTableReader.NextResult%2A> メソッドは、カーソルを次の結果セットに移動します。</span><span class="sxs-lookup"><span data-stu-id="f52f6-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="f52f6-106">これは前方参照専用です。</span><span class="sxs-lookup"><span data-stu-id="f52f6-106">This is a forward-only process.</span></span> <span data-ttu-id="f52f6-107">前の結果セットに戻ることはできません。</span><span class="sxs-lookup"><span data-stu-id="f52f6-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f52f6-108">例</span><span class="sxs-lookup"><span data-stu-id="f52f6-108">Example</span></span>  
 <span data-ttu-id="f52f6-109">次の例で、`TestConstructor`メソッドでは、2 つ作成されます<xref:System.Data.DataTable>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f52f6-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="f52f6-110">このコンス トラクターを実行するために、<xref:System.Data.DataTableReader>クラス、サンプルを作成、新しい**DataTableReader**を 2 つを含む配列に基づく**Datatable**、し、単純な操作を実行コンソール ウィンドウに最初のいくつかの列から内容を印刷します。</span><span class="sxs-lookup"><span data-stu-id="f52f6-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f52f6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f52f6-111">See Also</span></span>  
 [<span data-ttu-id="f52f6-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="f52f6-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [<span data-ttu-id="f52f6-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="f52f6-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
