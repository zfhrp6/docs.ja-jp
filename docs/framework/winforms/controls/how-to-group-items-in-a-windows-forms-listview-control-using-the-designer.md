---
title: "方法 : デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c9dc3a12227d3c9bfd64c97be61e69b50d2bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="26bb1-102">方法 : デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する</span><span class="sxs-lookup"><span data-stu-id="26bb1-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="26bb1-103">グループ化機能、<xref:System.Windows.Forms.ListView>コントロールでは、グループ内のアイテムの関連のセットを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="26bb1-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="26bb1-104">これらのグループは、画面の水平方向のグループを含むヘッダーにグループのタイトルで区切られます。</span><span class="sxs-lookup"><span data-stu-id="26bb1-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="26bb1-105">使用することができます<xref:System.Windows.Forms.ListView>日付、またはその他の論理グループで、アルファベット順に項目をグループ化して簡単に大規模なリストを移動するグループです。</span><span class="sxs-lookup"><span data-stu-id="26bb1-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="26bb1-106">次の図は、いくつかのグループ化された項目を示します。</span><span class="sxs-lookup"><span data-stu-id="26bb1-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="26bb1-107">![ListView グループ](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="26bb1-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
  
 <span data-ttu-id="26bb1-108">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="26bb1-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="26bb1-109">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="26bb1-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
 <span data-ttu-id="26bb1-110">グループ化を有効にする必要があります最初に作成する 1 つまたは複数<xref:System.Windows.Forms.ListViewGroup>デザイナーで、またはプログラムでのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="26bb1-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="26bb1-111">グループを定義した後に項目を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="26bb1-111">Once a group has been defined, you can assign items to it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26bb1-112"><xref:System.Windows.Forms.ListView>のみ使用可能なグループ[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]、アプリケーションを呼び出すと、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="26bb1-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="26bb1-113">以前のオペレーティング システムでグループに関連するすべてのコードが影響を与えませんし、グループが表示されません。</span><span class="sxs-lookup"><span data-stu-id="26bb1-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="26bb1-114">詳細については、「<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26bb1-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="26bb1-115">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="26bb1-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="26bb1-116">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="26bb1-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="26bb1-117">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26bb1-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="26bb1-118">追加またはデザイナーでグループを削除するには</span><span class="sxs-lookup"><span data-stu-id="26bb1-118">To add or remove groups in the designer</span></span>  
  
1.  <span data-ttu-id="26bb1-119">**プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Groups%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="26bb1-119">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>  
  
     <span data-ttu-id="26bb1-120">**ListViewGroup コレクション エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="26bb1-120">The **ListViewGroup Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="26bb1-121">グループを追加するをクリックして、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="26bb1-121">To add a group, click the **Add** button.</span></span> <span data-ttu-id="26bb1-122">など、新しいグループのプロパティを設定することができますし、<xref:System.Windows.Forms.ListViewGroup.Header%2A>と<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="26bb1-122">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="26bb1-123">グループを削除するを選択し、クリックして、**削除**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="26bb1-123">To remove a group, select it and click the **Remove** button.</span></span>  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="26bb1-124">項目をデザイナーでのグループに割り当てる</span><span class="sxs-lookup"><span data-stu-id="26bb1-124">To assign items to groups in the designer</span></span>  
  
1.  <span data-ttu-id="26bb1-125">**プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Items%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="26bb1-125">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="26bb1-126">**ListViewItem コレクション エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="26bb1-126">The **ListViewItem Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="26bb1-127">新しいアイテムを追加する をクリックして、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="26bb1-127">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="26bb1-128">など、新しい項目のプロパティを設定することができますし、<xref:System.Windows.Forms.ListViewItem.Text%2A>と<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="26bb1-128">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
3.  <span data-ttu-id="26bb1-129">選択、<xref:System.Windows.Forms.ListViewItem.Group%2A>プロパティし、ドロップダウン リストからグループを選択します。</span><span class="sxs-lookup"><span data-stu-id="26bb1-129">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bb1-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="26bb1-130">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="26bb1-131">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="26bb1-131">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="26bb1-132">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="26bb1-132">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="26bb1-133">Windows XP の機能と Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="26bb1-133">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="26bb1-134">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="26bb1-134">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
