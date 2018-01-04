---
title: "方法 : Windows フォーム ListView コントロールの項目をグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12b7126e03f6a6c8363c69a607f4961f13120ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="25c4f-102">方法 : Windows フォーム ListView コントロールの項目をグループ化する</span><span class="sxs-lookup"><span data-stu-id="25c4f-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="25c4f-103">グループ化機能で、<xref:System.Windows.Forms.ListView>コントロール グループに項目の関連する設定を表示できます。</span><span class="sxs-lookup"><span data-stu-id="25c4f-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="25c4f-104">これらのグループは、画面の水平方向のグループを含むヘッダーにグループのタイトルで区切られます。</span><span class="sxs-lookup"><span data-stu-id="25c4f-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="25c4f-105">使用することができます<xref:System.Windows.Forms.ListView>日付、またはその他の論理グループで、アルファベット順に項目をグループ化して簡単に大規模なリストを移動するグループです。</span><span class="sxs-lookup"><span data-stu-id="25c4f-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="25c4f-106">次の図は、いくつかのグループ化された項目を示します。</span><span class="sxs-lookup"><span data-stu-id="25c4f-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="25c4f-107">![ListView グループ](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="25c4f-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="25c4f-108">ListView の項目をグループ化</span><span class="sxs-lookup"><span data-stu-id="25c4f-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="25c4f-109">グループ化を有効にするのには、まず、デザイナーで、またはプログラムでは、1 つまたは複数のグループを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25c4f-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="25c4f-110">グループは、定義した後は、割り当てる<xref:System.Windows.Forms.ListView>項目をグループにします。</span><span class="sxs-lookup"><span data-stu-id="25c4f-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="25c4f-111">移動することも項目 1 つのグループから別にプログラムでします。</span><span class="sxs-lookup"><span data-stu-id="25c4f-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25c4f-112"><xref:System.Windows.Forms.ListView>のみ使用可能なグループ[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]、アプリケーションを呼び出すと、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="25c4f-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="25c4f-113">以前のオペレーティング システムでグループに関連するすべてのコードが影響を与えませんし、グループが表示されません。</span><span class="sxs-lookup"><span data-stu-id="25c4f-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="25c4f-114">詳細については、「<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25c4f-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="25c4f-115">グループを追加するには</span><span class="sxs-lookup"><span data-stu-id="25c4f-115">To add groups</span></span>  
  
1.  <span data-ttu-id="25c4f-116"><xref:System.Windows.Forms.ListView.Groups%2A> コレクションの <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="25c4f-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="25c4f-117">グループを削除するには</span><span class="sxs-lookup"><span data-stu-id="25c4f-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="25c4f-118">使用して、<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>または<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>のメソッド、<xref:System.Windows.Forms.ListView.Groups%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="25c4f-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="25c4f-119"><xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>メソッドは 1 つのグループを削除;<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>メソッドは、一覧からすべてのグループを削除します。</span><span class="sxs-lookup"><span data-stu-id="25c4f-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="25c4f-120">グループを削除しても、そのグループ内の項目は削除されません。</span><span class="sxs-lookup"><span data-stu-id="25c4f-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="25c4f-121">項目をグループに割り当てるか、グループ間で項目を移動するには</span><span class="sxs-lookup"><span data-stu-id="25c4f-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="25c4f-122">設定、<xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType>個々 のアイテムのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="25c4f-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="25c4f-123">参照</span><span class="sxs-lookup"><span data-stu-id="25c4f-123">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="25c4f-124">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="25c4f-124">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="25c4f-125">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="25c4f-125">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="25c4f-126">Windows XP の機能と Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="25c4f-126">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="25c4f-127">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="25c4f-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
