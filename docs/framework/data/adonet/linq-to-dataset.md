---
title: LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de0f11149c2ec587372b9e25f39f35f8552503c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset"></a><span data-ttu-id="d8840-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d8840-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="d8840-103"> は、<xref:System.Data.DataSet> オブジェクトにキャッシュされたデータに対するクエリをより簡単に、より高速にします。</span><span class="sxs-lookup"><span data-stu-id="d8840-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="d8840-104">具体的には、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]を個別のクエリ言語を使用して、クエリの代わりにプログラミング言語そのものを記述する開発者を有効にしてクエリを簡素化します。</span><span class="sxs-lookup"><span data-stu-id="d8840-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="d8840-105">これは特に役立ちます[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]利用できるようのコンパイル時の構文チェック、静的な型指定、IntelliSense のサポートによって提供される、開発者、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]がクエリでします。</span><span class="sxs-lookup"><span data-stu-id="d8840-105">This is especially useful for [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] in their queries.</span></span>  
  
 <span data-ttu-id="d8840-106">また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用すると、1 つまたは複数のデータ ソースから取得して統合したデータを照会することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8840-106">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="d8840-107">これにより、ローカルに集計されたデータのクエリや Web アプリケーションでの中間層のキャッシュなど、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。</span><span class="sxs-lookup"><span data-stu-id="d8840-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="d8840-108">特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。</span><span class="sxs-lookup"><span data-stu-id="d8840-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="d8840-109">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]機能は、拡張メソッドによって、主に、公開、<xref:System.Data.DataRowExtensions>と<xref:System.Data.DataTableExtensions>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d8840-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="d8840-110">上に構築し、は、既存[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]アーキテクチャを置き換えるものでありません[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]アプリケーション コードでします。</span><span class="sxs-lookup"><span data-stu-id="d8840-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="d8840-111">既存の ADO.NET 2.0 コードは [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] アプリケーションにおいても機能します。</span><span class="sxs-lookup"><span data-stu-id="d8840-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="d8840-112">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] と [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] のリレーションシップとデータ ストアを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="d8840-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="d8840-113">![LINQ to DataSet は、ADO.NET プロバイダーに基づいて](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="d8840-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8840-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d8840-114">In This Section</span></span>  
 [<span data-ttu-id="d8840-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="d8840-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="d8840-116">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d8840-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="d8840-117">参照</span><span class="sxs-lookup"><span data-stu-id="d8840-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="d8840-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8840-118">See Also</span></span>  
 [<span data-ttu-id="d8840-119">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d8840-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="d8840-120">LINQ と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8840-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="d8840-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8840-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
