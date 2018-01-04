---
title: "方法 : デザイナーを使って Windows フォーム ListView コントロールの \"並べて表示\" ビューを有効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36b20f4ee5bed6f81c42225f35083d51fb2a6308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="625a7-102">方法 : デザイナーを使って Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする</span><span class="sxs-lookup"><span data-stu-id="625a7-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="625a7-103">並べて表示ビュー機能、<xref:System.Windows.Forms.ListView>コントロールでは、グラフィカルとテキスト情報バランスよく表示を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="625a7-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="625a7-104">並べて表示ビューの項目で表示されるテキスト情報は、詳細ビュー用に定義されている列情報と同じ情報です。</span><span class="sxs-lookup"><span data-stu-id="625a7-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="625a7-105">並べて表示ビューは、グループ化またはカーソルのいずれかと組み合わせてマークの機能、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="625a7-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="625a7-106">タイル ビューでは、次の図のように、32 x 32 のアイコンと数行のテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="625a7-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>  
  
 <span data-ttu-id="625a7-107">![ListView コントロール内のタイル ビュー](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="625a7-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
  
 <span data-ttu-id="625a7-108">並べて表示ビューのプロパティとメソッドを使用すると、どの列フィールドが設定されている各項目に表示して総称して、サイズとタイル ビュー ウィンドウ内のすべての項目の外観を制御するには、フィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="625a7-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="625a7-109">わかりやすくするために、タイル内のテキストの最初の行は常に、項目の名前です。変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="625a7-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>  
  
 <span data-ttu-id="625a7-110">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="625a7-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="625a7-111">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="625a7-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="625a7-112">並べて表示ビューを [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] で使用できるのは、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> メソッドを呼び出した場合だけです。</span><span class="sxs-lookup"><span data-stu-id="625a7-112">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="625a7-113">旧バージョンのオペレーティング システムでは、並べて表示ビューに関するコードがすべて無効になり、<xref:System.Windows.Forms.ListView> コントロールは大きなアイコンのビューで表示されます。</span><span class="sxs-lookup"><span data-stu-id="625a7-113">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="625a7-114">詳細については、「<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="625a7-114">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="625a7-115">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="625a7-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="625a7-116">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="625a7-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="625a7-117">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="625a7-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="625a7-118">デザイナーで並べて表示ビューを設定するには</span><span class="sxs-lookup"><span data-stu-id="625a7-118">To set tile view in the designer</span></span>  
  
1.  <span data-ttu-id="625a7-119">選択、<xref:System.Windows.Forms.ListView>フォーム上のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="625a7-119">Select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>  
  
2.  <span data-ttu-id="625a7-120">**プロパティ**ウィンドウで、<xref:System.Windows.Forms.ListView.View%2A>プロパティを選択し、**タイル**です。</span><span class="sxs-lookup"><span data-stu-id="625a7-120">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625a7-121">参照</span><span class="sxs-lookup"><span data-stu-id="625a7-121">See Also</span></span>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="625a7-122">Windows XP の機能と Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="625a7-122">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="625a7-123">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="625a7-123">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
