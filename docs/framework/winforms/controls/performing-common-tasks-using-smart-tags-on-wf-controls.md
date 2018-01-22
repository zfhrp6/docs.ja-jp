---
title: "チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2fb4e8bf710e55be0a817a4154dfbce114db191
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="2d59f-102">チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行</span><span class="sxs-lookup"><span data-stu-id="2d59f-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="2d59f-103">Windows フォーム アプリケーションのフォームとコントロールを作成するときに、繰り返し実行する多くのタスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="2d59f-104">これらは、発生する、よく実行されるタスクの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="2d59f-105">追加または取り外し、タブ、<xref:System.Windows.Forms.TabControl>です。</span><span class="sxs-lookup"><span data-stu-id="2d59f-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="2d59f-106">コントロールの親へのドッキングします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="2d59f-107">向きの変更、<xref:System.Windows.Forms.SplitContainer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2d59f-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="2d59f-108">開発を高速には、多くのコントロールは、デザイン時に 1 つのジェスチャで上記のような一般的なタスクを実行することは状況依存のメニューは、スマート タグを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="2d59f-109">これらのタスクが呼び出されます*スマート タグ動詞*です。</span><span class="sxs-lookup"><span data-stu-id="2d59f-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="2d59f-110">スマート タグは、その有効期間、デザイナーでのコントロールのインスタンスに接続されたままし、常に利用します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="2d59f-111">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="2d59f-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="2d59f-112">Windows フォーム プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2d59f-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="2d59f-113">スマート タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="2d59f-114">有効にして、スマート タグを無効化</span><span class="sxs-lookup"><span data-stu-id="2d59f-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="2d59f-115">終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。</span><span class="sxs-lookup"><span data-stu-id="2d59f-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d59f-116">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d59f-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2d59f-117">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2d59f-118">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d59f-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2d59f-119">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2d59f-119">Creating the Project</span></span>  
 <span data-ttu-id="2d59f-120">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="2d59f-121">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="2d59f-121">To create the project</span></span>  
  
1.  <span data-ttu-id="2d59f-122">"SmartTagsExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="2d59f-123">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d59f-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="2d59f-124">フォームを選択、 **Windows フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="2d59f-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="2d59f-125">スマート タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-125">Using Smart Tags</span></span>  
 <span data-ttu-id="2d59f-126">スマート タグは提供するコントロールのデザイン時に常に使用します。</span><span class="sxs-lookup"><span data-stu-id="2d59f-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="2d59f-127">スマート タグを使用するには</span><span class="sxs-lookup"><span data-stu-id="2d59f-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="2d59f-128">ドラッグ、<xref:System.Windows.Forms.TabControl>から、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="2d59f-129">スマート タグ グリフを注意してください (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) のサイドに表示される、<xref:System.Windows.Forms.TabControl>です。</span><span class="sxs-lookup"><span data-stu-id="2d59f-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="2d59f-130">スマート タグ グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="2d59f-131">グリフの横に表示されるショートカット メニューで、選択、**タブの追加**項目。</span><span class="sxs-lookup"><span data-stu-id="2d59f-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="2d59f-132">新しいタブ ページが追加されたことを確認、<xref:System.Windows.Forms.TabControl>です。</span><span class="sxs-lookup"><span data-stu-id="2d59f-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="2d59f-133">ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="2d59f-134">スマート タグ グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="2d59f-135">グリフの横に表示されるショートカット メニューで、選択、**列の追加**項目。</span><span class="sxs-lookup"><span data-stu-id="2d59f-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="2d59f-136">新しい列が追加されたことを確認、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2d59f-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="2d59f-137">ドラッグ、<xref:System.Windows.Forms.SplitContainer>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="2d59f-138">スマート タグ グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d59f-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="2d59f-139">グリフの横に表示されるショートカット メニューで、選択、**水平分割線の向き**項目。</span><span class="sxs-lookup"><span data-stu-id="2d59f-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="2d59f-140">されることを確認、<xref:System.Windows.Forms.SplitContainer>コントロールの分割バーは水平方向です。</span><span class="sxs-lookup"><span data-stu-id="2d59f-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d59f-141">参照</span><span class="sxs-lookup"><span data-stu-id="2d59f-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="2d59f-142">チュートリアル: Windows フォームのコンポーネントへのスマート タグの追加</span><span class="sxs-lookup"><span data-stu-id="2d59f-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
