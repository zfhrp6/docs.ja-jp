---
title: DataTableReader
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b5160f5a2c68cab798dde154275c062e2bf31739
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="datatablereaders"></a><span data-ttu-id="336d6-102">DataTableReader</span><span class="sxs-lookup"><span data-stu-id="336d6-102">DataTableReaders</span></span>
<span data-ttu-id="336d6-103"><xref:System.Data.DataTableReader> は、<xref:System.Data.DataTable> または <xref:System.Data.DataSet> の内容を、読み取り専用かつ前方参照専用の 1 つ以上の結果セットとして表します。</span><span class="sxs-lookup"><span data-stu-id="336d6-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="336d6-104">作成するときに、 **DataTableReader**から、 **DataTable**、結果の**DataTableReader**オブジェクトには、1 つを含む結果セットと同じデータが含まれています、 **DataTable**作成元であることが、削除済みとしてマークされている行は除く。</span><span class="sxs-lookup"><span data-stu-id="336d6-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="336d6-105">元と同じ順序で列が表示される**DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="336d6-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="336d6-106">A **DataTableReader**呼び出すことによって作成された場合、複数の結果セットを含めることは<xref:System.Data.DataSet.CreateDataReader%2A>します。</span><span class="sxs-lookup"><span data-stu-id="336d6-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="336d6-107">結果と同じ順序では、 **Datatable**で、**データセット**オブジェクトの<xref:System.Data.DataSet.Tables%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="336d6-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="336d6-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="336d6-108">In This Section</span></span>  
 [<span data-ttu-id="336d6-109">DataReader の作成</span><span class="sxs-lookup"><span data-stu-id="336d6-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="336d6-110">作成する方法について説明します、 **DataTableReader**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="336d6-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="336d6-111">DataTable の移動</span><span class="sxs-lookup"><span data-stu-id="336d6-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="336d6-112">使用方法について説明、**読み取り**の内容を移動する方法、 **DataTableReader**です。</span><span class="sxs-lookup"><span data-stu-id="336d6-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336d6-113">参照</span><span class="sxs-lookup"><span data-stu-id="336d6-113">See Also</span></span>  
 [<span data-ttu-id="336d6-114">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="336d6-114">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="336d6-115">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="336d6-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
