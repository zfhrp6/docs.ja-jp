---
title: "LINQ to ADO.NET (ポータル ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: df23be4b87860afcde03328d0fe47e305860f5f7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="03939-102">LINQ to ADO.NET (ポータル ページ)</span><span class="sxs-lookup"><span data-stu-id="03939-102">LINQ to ADO.NET (Portal Page)</span></span>
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]<span data-ttu-id="03939-103">内の列挙可能なオブジェクトに対するクエリを実行することができます[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]を使用して、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]プログラミング モデルです。</span><span class="sxs-lookup"><span data-stu-id="03939-103"> enables you to query over any enumerable object in [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] by using the [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] programming model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03939-104">[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]ドキュメントは、.NET Framework SDK の ADO.NET セクションにあります: [LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)します。</span><span class="sxs-lookup"><span data-stu-id="03939-104">The [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).</span></span>  
  
 <span data-ttu-id="03939-105">ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] には、[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、および [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] の&3; つのテクノロジがあります。</span><span class="sxs-lookup"><span data-stu-id="03939-105">There are three separate ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] technologies: [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], and [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)].</span></span> [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]<span data-ttu-id="03939-106">豊富な最適化されたクエリを実行するには、 <xref:System.Data.DataSet>、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]を直接照会することができます[!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)]データベース スキーマ、および[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]クエリを実行することができます、 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]</xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="03939-106"> provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] enables you to directly query [!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] database schemas, and [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] allows you to query an [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)].</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="03939-107">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="03939-107">LINQ to DataSet</span></span>  
 <span data-ttu-id="03939-108"><xref:System.Data.DataSet>で最も広く使用されているコンポーネントの&1; つ[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]とは、非接続型プログラミングの重要な要素をモデル化[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]は上に構築します</xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="03939-108">The <xref:System.Data.DataSet> is one of the most widely used components in [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)], and is a key element of the disconnected programming model that [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] is built on.</span></span> <span data-ttu-id="03939-109">ただし、この重要であるにもかかわらず、<xref:System.Data.DataSet>クエリ機能が制限されています</xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="03939-109">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]<span data-ttu-id="03939-110">豊富なクエリ機能を構築することができます<xref:System.Data.DataSet>他の多くのデータ ソースに使用される同じクエリ機能を使用しています</xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="03939-110"> enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="03939-111">詳細については、次を参照してください。 [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)します。</span><span class="sxs-lookup"><span data-stu-id="03939-111">For more information, see [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="03939-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="03939-112">LINQ to SQL</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]<span data-ttu-id="03939-113">リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="03939-113"> provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="03939-114">[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、リレーショナル データベースのデータ モデルは、開発者のプログラミング言語で表されるオブジェクト モデルにマッピングします。</span><span class="sxs-lookup"><span data-stu-id="03939-114">In [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="03939-115">アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]オブジェクト モデルでの統合言語クエリを SQL に変換し、実行するためのデータベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="03939-115">When you execute the application, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="03939-116">データベースには、結果が返されるときに[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]操作できるオブジェクトにはそれを変換します。</span><span class="sxs-lookup"><span data-stu-id="03939-116">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]<span data-ttu-id="03939-117">オブジェクト モデルでは、ストアド プロシージャと、データベース内のユーザー定義関数、および継承のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="03939-117"> includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="03939-118">詳細については、次を参照してください。 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)します。</span><span class="sxs-lookup"><span data-stu-id="03939-118">For more information, see [LINQ to SQL](https://msdn.microsoft.com/library/bb386976).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="03939-119">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="03939-119">LINQ to Entities</span></span>  
 <span data-ttu-id="03939-120">[!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="03939-120">Through the [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)], relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="03939-121">これにより、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="03939-121">This makes the object layer an ideal target for [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="03939-122">この機能は、[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="03939-122">This capability is known as [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)].</span></span> <span data-ttu-id="03939-123">参照してください[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)の詳細。</span><span class="sxs-lookup"><span data-stu-id="03939-123">See [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03939-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="03939-124">See Also</span></span>  
 <span data-ttu-id="03939-125">[LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec) </span><span class="sxs-lookup"><span data-stu-id="03939-125">[LINQ and ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec) </span></span>  
<span data-ttu-id="03939-126"> [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="03939-126"> [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)</span></span>
