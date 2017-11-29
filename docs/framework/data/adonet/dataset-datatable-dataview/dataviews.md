---
title: DataView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2653a94992440b747371c5d8a7b9daa66b3e3ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dataviews"></a><span data-ttu-id="443d3-102">DataView</span><span class="sxs-lookup"><span data-stu-id="443d3-102">DataViews</span></span>
<span data-ttu-id="443d3-103"><xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータのさまざまなビューを作成できます。この機能は、データ連結アプリケーションで頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="443d3-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="443d3-104">使用して、 **DataView**さまざまな並べ替え順序、テーブル内のデータを公開することができます、および行の状態やフィルター式に基づいて、データをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="443d3-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="443d3-105">A **DataView** 、基になるデータの動的なビューを提供**DataTable**: 内容、順序、およびメンバーシップ発生すると、変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="443d3-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="443d3-106">この動作は異なります、**選択**のメソッド、 **DataTable**を返す、<xref:System.Data.DataRow>特定のフィルター処理や並べ替え順序に基づいて、テーブルから配列: thiscontent への変更を反映して、テーブルが、メンバーシップを基になると、順序付けは、静的なままです。</span><span class="sxs-lookup"><span data-stu-id="443d3-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: thiscontent reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="443d3-107">動的機能、 **DataView**データ連結アプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="443d3-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="443d3-108">A **DataView**では、別の並べ替えやフィルター処理条件を適用できますデータベース ビューの場合と同様に、データの単一セットの動的な表示します。</span><span class="sxs-lookup"><span data-stu-id="443d3-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="443d3-109">ただし、データベース ビューとは異なり、 **DataView**テーブルとして扱うことはできませんし、結合テーブルのビューを提供することはできません。</span><span class="sxs-lookup"><span data-stu-id="443d3-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="443d3-110">また、ソース テーブルの既存の列を除外したり、ソース テーブルにない列 (計算列など) を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="443d3-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="443d3-111">使用することができます、<xref:System.Data.DataView.DataViewManager%2A>内のすべてのテーブルの表示設定を管理する、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="443d3-112">**DataViewManager**テーブルごとに既定の表示設定を管理する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="443d3-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="443d3-113">2 つ以上のテーブルにコントロールをバインドするときに、**データセット**に連結する、 **DataViewManager**理想的なソリューションです。</span><span class="sxs-lookup"><span data-stu-id="443d3-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="443d3-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="443d3-114">In This Section</span></span>  
 [<span data-ttu-id="443d3-115">DataView の作成</span><span class="sxs-lookup"><span data-stu-id="443d3-115">Creating a DataView</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 <span data-ttu-id="443d3-116">作成する方法について説明します、 **DataView**の**DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="443d3-117">並べ替えとデータをフィルター処理</span><span class="sxs-lookup"><span data-stu-id="443d3-117">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 <span data-ttu-id="443d3-118">プロパティを設定する方法について説明、 **DataView**のサブセットを返すデータ行の特定のフィルター条件を満たす、または特定の並べ替え順序でデータを返します。</span><span class="sxs-lookup"><span data-stu-id="443d3-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="443d3-119">Datarow および Datarowview</span><span class="sxs-lookup"><span data-stu-id="443d3-119">DataRows and DataRowViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 <span data-ttu-id="443d3-120">によって公開されるデータにアクセスする方法について説明します、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="443d3-121">行を検索します。</span><span class="sxs-lookup"><span data-stu-id="443d3-121">Finding Rows</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 <span data-ttu-id="443d3-122">特定の行を検索する方法について説明、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="443d3-123">Childview とリレーション</span><span class="sxs-lookup"><span data-stu-id="443d3-123">ChildViews and Relations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 <span data-ttu-id="443d3-124">使用して、親子関係からのデータのビューを作成する方法について説明、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="443d3-125">Dataview の変更</span><span class="sxs-lookup"><span data-stu-id="443d3-125">Modifying DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 <span data-ttu-id="443d3-126">基になるデータを変更する方法について説明**DataTable**を介して、 **DataView**、有効化と更新プログラムを無効にするとします。</span><span class="sxs-lookup"><span data-stu-id="443d3-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="443d3-127">DataView イベントの処理</span><span class="sxs-lookup"><span data-stu-id="443d3-127">Handling DataView Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 <span data-ttu-id="443d3-128">使用する方法について説明します、 **ListChanged**イベント通知を受信するときの内容または順序、 **DataView**を更新しています。</span><span class="sxs-lookup"><span data-stu-id="443d3-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="443d3-129">DataViews の管理</span><span class="sxs-lookup"><span data-stu-id="443d3-129">Managing DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 <span data-ttu-id="443d3-130">使用する方法について説明します、 **DataViewManager**を管理する**DataView**内の各テーブルの設定、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="443d3-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="443d3-131">Related Sections</span></span>  
 [<span data-ttu-id="443d3-132">ASP.NET Web アプリケーション</span><span class="sxs-lookup"><span data-stu-id="443d3-132">ASP.NET Web Applications</span></span>](http://msdn.microsoft.com/en-us/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 <span data-ttu-id="443d3-133">ASP.NET アプリケーション、Web フォームおよび Web サービスを作成する場合の概要と詳細なステップごとの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="443d3-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 [<span data-ttu-id="443d3-134">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="443d3-134">Windows Applications</span></span>](http://msdn.microsoft.com/en-us/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 <span data-ttu-id="443d3-135">Windows フォームおよびコンソール アプリケーションの操作に関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="443d3-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="443d3-136">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="443d3-136">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="443d3-137">について説明します、**データセット**オブジェクトとアプリケーション データの管理を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="443d3-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="443d3-138">DataTables</span><span class="sxs-lookup"><span data-stu-id="443d3-138">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="443d3-139">について説明します、 **DataTable**オブジェクトとデータを管理するアプリケーションの一部としてまたは単独で使用する方法、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="443d3-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="443d3-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="443d3-140">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="443d3-141">ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="443d3-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443d3-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="443d3-142">See Also</span></span>  
 [<span data-ttu-id="443d3-143">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="443d3-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
