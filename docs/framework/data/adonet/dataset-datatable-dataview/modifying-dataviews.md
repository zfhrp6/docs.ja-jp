---
title: "DataView の変更"
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
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 921707b07f1e8c8a9208df7de74512325f3027d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-dataviews"></a><span data-ttu-id="2fbb5-102">DataView の変更</span><span class="sxs-lookup"><span data-stu-id="2fbb5-102">Modifying DataViews</span></span>
<span data-ttu-id="2fbb5-103"><xref:System.Data.DataView> を使用して、データ行を基になるテーブルに追加、削除、または変更できます。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="2fbb5-104">使用する機能、 **DataView**基になるテーブル内のデータを変更するのには 3 つのブール型プロパティのいずれかの設定によって制御されます、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="2fbb5-105">この 3 つのプロパティとは、<xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> および <xref:System.Data.DataView.AllowDelete%2A> です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="2fbb5-106">設定されている**true**既定です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="2fbb5-107">場合**AllowNew**は**true**、使用することができます、<xref:System.Data.DataView.AddNew%2A>のメソッド、 **DataView**を新規作成する<xref:System.Data.DataRowView>です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="2fbb5-108">新しい行がないことが実際には、基になる追加<xref:System.Data.DataTable>まで、<xref:System.Data.DataRowView.EndEdit%2A>のメソッド、 **DataRowView**と呼びます。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="2fbb5-109">場合、<xref:System.Data.DataRowView.CancelEdit%2A>のメソッド、 **DataRowView**が呼び出されると、新しい行が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="2fbb5-110">1 つだけを編集できることにも注意してください**DataRowView**一度にです。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="2fbb5-111">呼び出す場合は、 **AddNew**または**BeginEdit**のメソッド、 **DataRowView**保留中の行が存在する間**EndEdit**で暗黙的に呼び出されると、保留中の行。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="2fbb5-112">ときに**EndEdit**が呼び出されると、変更は適用、基になる**DataTable**でき、後でコミットされたかを使用して拒否された、 **AcceptChanges**または**RejectChanges**のメソッド、 **DataTable**、**データセット**、または**DataRow**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="2fbb5-113">場合**AllowNew**は**false**、呼び出した場合、例外がスローされます、 **AddNew**のメソッド、 **DataRowView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="2fbb5-114">場合**AllowEdit**は**true**の内容を変更することができます、 **DataRow**を介して、 **DataRowView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="2fbb5-115">使用して基になる行への変更を確認する**DataRowView.EndEdit**を使用して変更を拒否または**DataRowView.CancelEdit**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="2fbb5-116">一度に編集できるのは 1 行だけです。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="2fbb5-117">呼び出す場合は、 **AddNew**または**BeginEdit**のメソッド、 **DataRowView**保留中の行が存在する間**EndEdit**で暗黙的に呼び出される保留中の行。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="2fbb5-118">ときに**EndEdit**が呼び出されるで提案された変更を配置している、**現在**行バージョンの基になる**DataRow**でき、後でコミットされたか、を使用して拒否されました。**AcceptChanges**または**RejectChanges**のメソッド、 **DataTable**、**データセット**、または**DataRow**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="2fbb5-119">場合**AllowEdit**は**false**、内の値を変更しようとする場合、例外がスローされます、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="2fbb5-120">既存**DataRowView**が編集中、基になるイベント**DataTable**提案された変更をまだ生成されます。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="2fbb5-121">呼び出す場合**EndEdit**または**CancelEdit**で、基になる**DataRow**、保留中の変更を適用またはかどうかに関係なくキャンセルは**EndEdit**または**CancelEdit**で呼び出されると、 **DataRowView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="2fbb5-122">場合**AllowDelete**は**true**から行を削除することができます、 **DataView**を使用して、**削除**のメソッド、 **DataView**または**DataRowView**オブジェクト、および行が削除されている場合、基になるから**DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="2fbb5-123">後でコミットまたはを使用して削除を拒否する**AcceptChanges**または**RejectChanges**それぞれします。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="2fbb5-124">場合**AllowDelete**は**false**、呼び出した場合、例外がスローされます、**削除**のメソッド、 **DataView**または**DataRowView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="2fbb5-125">次のコード例を使用して無効になります、 **DataView**に削除の行の行を新しい行を使用して基になるテーブルを追加、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="2fbb5-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fbb5-126">参照</span><span class="sxs-lookup"><span data-stu-id="2fbb5-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="2fbb5-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="2fbb5-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="2fbb5-128">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="2fbb5-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
