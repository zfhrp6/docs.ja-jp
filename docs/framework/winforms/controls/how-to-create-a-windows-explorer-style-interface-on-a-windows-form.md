---
title: "方法 : Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c30dd18e7303cf9fe913760da3f9dad7bca3c95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="5017d-102">方法 : Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="5017d-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="5017d-103">Windows エクスプ ローラーは、準備ができて、使いやすさのためのアプリケーションの一般的なユーザー インターフェイス選択です。</span><span class="sxs-lookup"><span data-stu-id="5017d-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="5017d-104">Windows エクスプ ローラーは、基本的に、<xref:System.Windows.Forms.TreeView>コントロールと<xref:System.Windows.Forms.ListView>別のパネル上のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="5017d-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="5017d-105">パネルは、スプリッターによってサイズ変更可能で行われます。</span><span class="sxs-lookup"><span data-stu-id="5017d-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="5017d-106">このコントロールの配置は、表示する情報と参照に対して非常に効果的です。</span><span class="sxs-lookup"><span data-stu-id="5017d-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="5017d-107">次の手順では、Windows エクスプ ローラーのようなフォームでコントロールを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5017d-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="5017d-108">Windows エクスプ ローラーのアプリケーションのファイル参照機能を追加する方法には表示されません。</span><span class="sxs-lookup"><span data-stu-id="5017d-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5017d-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5017d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5017d-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5017d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5017d-111">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5017d-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="5017d-112">Windows エクスプ ローラー スタイルの Windows フォームを作成するには</span><span class="sxs-lookup"><span data-stu-id="5017d-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="5017d-113">新しい Windows アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5017d-113">Create a new Windows Application project.</span></span> <span data-ttu-id="5017d-114">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5017d-114">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="5017d-115">**ツールボックス**:</span><span class="sxs-lookup"><span data-stu-id="5017d-115">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="5017d-116">ドラッグ、<xref:System.Windows.Forms.SplitContainer>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="5017d-116">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="5017d-117">ドラッグ、<xref:System.Windows.Forms.TreeView>にコントロールを**SplitterPanel1** (のパネル、<xref:System.Windows.Forms.SplitContainer>マークされているコントロール**Panel1**)。</span><span class="sxs-lookup"><span data-stu-id="5017d-117">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="5017d-118">ドラッグ、<xref:System.Windows.Forms.ListView>にコントロールを**SplitterPanel2** (のパネル、<xref:System.Windows.Forms.SplitContainer>マークされているコントロール**Panel2**)。</span><span class="sxs-lookup"><span data-stu-id="5017d-118">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="5017d-119">CTRL キーを押しながらクリックするとさらに、3 つすべてのコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="5017d-119">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="5017d-120">選択した場合、<xref:System.Windows.Forms.SplitContainer>制御、パネルではなく、分割バーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5017d-120">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5017d-121">使用しないで、**すべて選択**コマンドを**編集**メニュー。</span><span class="sxs-lookup"><span data-stu-id="5017d-121">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="5017d-122">これを行う場合、次の手順で必要なプロパティには表示されません、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="5017d-122">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="5017d-123">**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。</span><span class="sxs-lookup"><span data-stu-id="5017d-123">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="5017d-124">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5017d-124">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="5017d-125">フォームには、Windows エクスプ ローラーのような 2 部構成のユーザー インターフェイスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5017d-125">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5017d-126">分割線をドラッグすると、パネル サイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="5017d-126">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5017d-127">参照</span><span class="sxs-lookup"><span data-stu-id="5017d-127">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="5017d-128">方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="5017d-128">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="5017d-129">方法: 分割ウィンドウでのサイズ変更および位置指定動作を定義する</span><span class="sxs-lookup"><span data-stu-id="5017d-129">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="5017d-130">方法: ウィンドウを水平方向に分割する</span><span class="sxs-lookup"><span data-stu-id="5017d-130">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="5017d-131">SplitContainer コントロール</span><span class="sxs-lookup"><span data-stu-id="5017d-131">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
