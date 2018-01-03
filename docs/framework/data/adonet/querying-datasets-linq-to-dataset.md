---
title: "DataSet のクエリ (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3793417502d359a9d05899f6e1d4306aac7ca88b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="853f2-102">DataSet のクエリ (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="853f2-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="853f2-103"><xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="853f2-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="853f2-104">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使ったクエリの作成方法は、他の [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 対応データ ソースに対して [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] を使用する方法と似ています。</span><span class="sxs-lookup"><span data-stu-id="853f2-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="853f2-105">ただしを使用すると[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]経由でクエリを実行、<xref:System.Data.DataSet>オブジェクトの列挙クエリを実行する<xref:System.Data.DataRow>カスタム型の列挙体ではなく、オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="853f2-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="853f2-106">つまりのメンバーのいずれかを使用できます、<xref:System.Data.DataRow>クラス内で、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="853f2-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="853f2-107">これにより、高度で複雑なクエリの作成が可能となります。</span><span class="sxs-lookup"><span data-stu-id="853f2-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="853f2-108">その他の実装と同様[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]、作成することができます[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]2 つの異なる形式でのクエリ: クエリ式の構文とメソッド ベースのクエリ構文です。</span><span class="sxs-lookup"><span data-stu-id="853f2-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="853f2-109">これら 2 つの形式の詳細については、次を参照してください。 [LINQ の概要](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)です。</span><span class="sxs-lookup"><span data-stu-id="853f2-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="853f2-110">クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="853f2-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="853f2-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="853f2-111">In This Section</span></span>  
 [<span data-ttu-id="853f2-112">単一テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="853f2-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="853f2-113">単一テーブルのクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="853f2-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="853f2-114">複数テーブルにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="853f2-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="853f2-115">複数テーブルにまたがるクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="853f2-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="853f2-116">型指定された DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="853f2-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="853f2-117">型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="853f2-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853f2-118">参照</span><span class="sxs-lookup"><span data-stu-id="853f2-118">See Also</span></span>  
 [<span data-ttu-id="853f2-119">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="853f2-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="853f2-120">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="853f2-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
