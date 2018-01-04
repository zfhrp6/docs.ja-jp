---
title: "方法 :デザイナーを使って ToolBar ボタンのアイコンを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e72b2516efab3bc5b5d8cc7cacb66f149f3a66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="52613-102">方法 :デザイナーを使って ToolBar ボタンのアイコンを定義する</span><span class="sxs-lookup"><span data-stu-id="52613-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="52613-103"><xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="52613-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="52613-104"><xref:System.Windows.Forms.ToolBar>ボタンは、ユーザーがそれらに含まれるを識別しやすくのアイコンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="52613-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="52613-105">これに画像を追加することによって実現、<xref:System.Windows.Forms.ImageList>コンポーネントと関連付けることで、<xref:System.Windows.Forms.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="52613-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="52613-106">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ToolBar>コントロールと<xref:System.Windows.Forms.ImageList>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="52613-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="52613-107">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="52613-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52613-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="52613-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="52613-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52613-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="52613-110">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52613-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="52613-111">デザイン時ツール バー ボタンのアイコンを設定するには</span><span class="sxs-lookup"><span data-stu-id="52613-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="52613-112">イメージを追加、<xref:System.Windows.Forms.ImageList>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="52613-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="52613-113">詳細については、次を参照してください。[する方法: デザイナーを使って ImageList イメージを追加または](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="52613-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="52613-114">選択、<xref:System.Windows.Forms.ToolBar>フォーム上のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="52613-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="52613-115">**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.ImageList%2A>プロパティを<xref:System.Windows.Forms.ImageList>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="52613-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="52613-116">クリックして、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.Buttons%2A>プロパティを選択し、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を開くには、ボタン**ToolBarButton コレクション エディター**です。</span><span class="sxs-lookup"><span data-stu-id="52613-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="52613-117">使用して、**追加**ボタンを追加するにはボタン、<xref:System.Windows.Forms.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="52613-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="52613-118">**プロパティ**の右側のペインに表示されるウィンドウ、 **ToolBarButton コレクション エディター**、設定、<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>各ツールバーのボタン、リスト内の値のいずれかのプロパティを追加した画像の描画、<xref:System.Windows.Forms.ImageList>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="52613-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52613-119">参照</span><span class="sxs-lookup"><span data-stu-id="52613-119">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="52613-120">方法: ツール バー ボタンのメニュー イベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="52613-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="52613-121">ToolBar コントロール</span><span class="sxs-lookup"><span data-stu-id="52613-121">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="52613-122">ImageList コンポーネント</span><span class="sxs-lookup"><span data-stu-id="52613-122">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
