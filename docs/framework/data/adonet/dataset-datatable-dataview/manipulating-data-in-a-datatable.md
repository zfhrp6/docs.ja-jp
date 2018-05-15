---
title: DataTable 内のデータの操作
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: f21ac216ed69db99001e324eb34cacf1254fcf6e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="bac3e-102">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="bac3e-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="bac3e-103"><xref:System.Data.DataTable> 内に <xref:System.Data.DataSet> を作成した後で、データベース内のテーブルを使用する場合と同じ操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="bac3e-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="bac3e-104">テーブル内のデータの追加、表示、編集、および削除を実行したり、エラーとイベントを監視したり、テーブル内のデータを照会したりできます。</span><span class="sxs-lookup"><span data-stu-id="bac3e-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="bac3e-105">内のデータを変更するときに、 **DataTable**変更が正確し、プログラムによって受け入れるか、変更を拒否するかどうかを決定かどうかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="bac3e-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bac3e-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bac3e-106">In This Section</span></span>  
 [<span data-ttu-id="bac3e-107">DataTable へのデータの追加</span><span class="sxs-lookup"><span data-stu-id="bac3e-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="bac3e-108">新しい行を作成してテーブルに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="bac3e-109">DataTable 内のデータの表示</span><span class="sxs-lookup"><span data-stu-id="bac3e-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="bac3e-110">元のバージョンのデータや現在のバージョンのデータを含め、行内のデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="bac3e-111">Load メソッド</span><span class="sxs-lookup"><span data-stu-id="bac3e-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="bac3e-112">使用方法について説明、**ロード**メソッドで設定する、 **DataTable**行を含むです。</span><span class="sxs-lookup"><span data-stu-id="bac3e-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="bac3e-113">DataTable の編集</span><span class="sxs-lookup"><span data-stu-id="bac3e-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="bac3e-114">提示された変更が検証され、受け入れられるまで行への実際の変更を保留しておく方法も含め、行内のデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="bac3e-115">行の状態とバージョン</span><span class="sxs-lookup"><span data-stu-id="bac3e-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="bac3e-116">行のさまざまな状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="bac3e-117">DataRow の削除</span><span class="sxs-lookup"><span data-stu-id="bac3e-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="bac3e-118">テーブルから行を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="bac3e-119">行エラー情報</span><span class="sxs-lookup"><span data-stu-id="bac3e-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="bac3e-120">アプリケーション内でのデータに関する問題を解決するために、行ごとのエラー情報を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="bac3e-121">AcceptChange と RejectChange</span><span class="sxs-lookup"><span data-stu-id="bac3e-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="bac3e-122">行への変更を受け入れたり拒否したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bac3e-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac3e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="bac3e-123">See Also</span></span>  
 [<span data-ttu-id="bac3e-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="bac3e-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="bac3e-125">DataTable イベントの処理</span><span class="sxs-lookup"><span data-stu-id="bac3e-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="bac3e-126">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="bac3e-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
