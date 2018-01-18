---
title: "プログラミング ガイド (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fc7c58f7062871fc3f6ac084bdeafcb12dad1f86
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="50c08-102">プログラミング ガイド (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="50c08-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="50c08-103">ここでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用したプログラミングに関する概要情報と例を提供します。</span><span class="sxs-lookup"><span data-stu-id="50c08-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50c08-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="50c08-104">In This Section</span></span>  
 [<span data-ttu-id="50c08-105">LINQ to DataSet でのクエリ</span><span class="sxs-lookup"><span data-stu-id="50c08-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="50c08-106">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリの作成方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="50c08-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="50c08-107">DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="50c08-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="50c08-108"><xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50c08-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="50c08-109">DataRow の比較</span><span class="sxs-lookup"><span data-stu-id="50c08-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="50c08-110"><xref:System.Data.DataRowComparer> オブジェクトを使用してデータ行を比較する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50c08-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="50c08-111">クエリによる DataTable の作成</span><span class="sxs-lookup"><span data-stu-id="50c08-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="50c08-112">作成に関する情報を提供、<xref:System.Data.DataTable>から、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリを使用して、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="50c08-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="50c08-113">方法: CopyToDataTable を実装する\<T > ジェネリック型 T が DataRow ではありません</span><span class="sxs-lookup"><span data-stu-id="50c08-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="50c08-114">`CopyToDataTable<T>` 型以外のジェネリック パラメーター T を持つカスタム <xref:System.Data.DataRow> メソッドの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50c08-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="50c08-115">ジェネリック メソッド Field および SetField</span><span class="sxs-lookup"><span data-stu-id="50c08-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="50c08-116">ジェネリック メソッド <xref:System.Data.DataRowExtensions.Field%2A> および <xref:System.Data.DataRowExtensions.SetField%2A> に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="50c08-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="50c08-117">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="50c08-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="50c08-118"><xref:System.Data.DataView> オブジェクトを使ったデータ バインドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="50c08-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="50c08-119">LINQ to DataSet クエリのデバッグ</span><span class="sxs-lookup"><span data-stu-id="50c08-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="50c08-120">デバッグとトラブルシューティングに関する情報を提供[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="50c08-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="50c08-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="50c08-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="50c08-122">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] におけるセキュリティの問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="50c08-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="50c08-123">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="50c08-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="50c08-124">[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 演算子を使ったクエリの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="50c08-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="50c08-125">参照</span><span class="sxs-lookup"><span data-stu-id="50c08-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="50c08-126">参照</span><span class="sxs-lookup"><span data-stu-id="50c08-126">See Also</span></span>  
 [<span data-ttu-id="50c08-127">LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="50c08-127">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [<span data-ttu-id="50c08-128">ビルド内にありません: LINQ の一般的なプログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="50c08-128">NOT IN BUILD: LINQ General Programming Guide</span></span>](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049)  
 [<span data-ttu-id="50c08-129">LINQ Framework</span><span class="sxs-lookup"><span data-stu-id="50c08-129">LINQ Framework</span></span>](http://msdn.microsoft.com/en-us/897ea0fc-40db-4694-bbe5-7dd339d5bf94)
