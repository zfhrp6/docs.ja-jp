---
title: 'チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537945"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="b16a5-102">チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行</span><span class="sxs-lookup"><span data-stu-id="b16a5-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="b16a5-103">Windows フォーム アプリケーションのフォームとコントロールを作成するときに、繰り返し実行する多くのタスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="b16a5-104">これらは、発生する、よく実行されるタスクの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="b16a5-105">追加または取り外し、タブ、<xref:System.Windows.Forms.TabControl>です。</span><span class="sxs-lookup"><span data-stu-id="b16a5-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="b16a5-106">コントロールの親へのドッキングします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="b16a5-107">向きの変更、<xref:System.Windows.Forms.SplitContainer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="b16a5-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="b16a5-108">開発を高速には、多くのコントロールは、デザイン時に 1 つのジェスチャで上記のような一般的なタスクを実行することは状況依存のメニューは、スマート タグを提供します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="b16a5-109">これらのタスクが呼び出されます*スマート タグ動詞*です。</span><span class="sxs-lookup"><span data-stu-id="b16a5-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="b16a5-110">スマート タグは、その有効期間、デザイナーでのコントロールのインスタンスに接続されたままし、常に利用します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="b16a5-111">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="b16a5-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="b16a5-112">Windows フォーム プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="b16a5-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="b16a5-113">スマート タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="b16a5-114">有効にして、スマート タグを無効化</span><span class="sxs-lookup"><span data-stu-id="b16a5-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="b16a5-115">終了すると、これらの重要なレイアウト機能が果たす役割について理解できます。</span><span class="sxs-lookup"><span data-stu-id="b16a5-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b16a5-116">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b16a5-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b16a5-117">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b16a5-118">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b16a5-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b16a5-119">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="b16a5-119">Creating the Project</span></span>  
 <span data-ttu-id="b16a5-120">最初にプロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="b16a5-121">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="b16a5-121">To create the project</span></span>  
  
1.  <span data-ttu-id="b16a5-122">"SmartTagsExample"と呼ばれる Windows ベースのアプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="b16a5-123">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b16a5-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="b16a5-124">フォームを選択、 **Windows フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="b16a5-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="b16a5-125">スマート タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-125">Using Smart Tags</span></span>  
 <span data-ttu-id="b16a5-126">スマート タグは提供するコントロールのデザイン時に常に使用します。</span><span class="sxs-lookup"><span data-stu-id="b16a5-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="b16a5-127">スマート タグを使用するには</span><span class="sxs-lookup"><span data-stu-id="b16a5-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="b16a5-128">ドラッグ、<xref:System.Windows.Forms.TabControl>から、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="b16a5-129">スマート タグ グリフを注意してください (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) のサイドに表示される、<xref:System.Windows.Forms.TabControl>です。</span><span class="sxs-lookup"><span data-stu-id="b16a5-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="b16a5-130">スマート タグ グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="b16a5-131">グリフの横に表示されるショートカット メニューで、選択、**タブの追加**項目。</span><span class="sxs-lookup"><span data-stu-id="b16a5-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="b16a5-132">新しいタブ ページが追加されたことを確認、<xref:System.Windows.Forms.TabControl>です。</span><span class="sxs-lookup"><span data-stu-id="b16a5-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="b16a5-133">ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="b16a5-134">スマート タグ グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="b16a5-135">グリフの横に表示されるショートカット メニューで、選択、**列の追加**項目。</span><span class="sxs-lookup"><span data-stu-id="b16a5-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="b16a5-136">新しい列が追加されたことを確認、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="b16a5-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="b16a5-137">ドラッグ、<xref:System.Windows.Forms.SplitContainer>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="b16a5-138">スマート タグ グリフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b16a5-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="b16a5-139">グリフの横に表示されるショートカット メニューで、選択、**水平分割線の向き**項目。</span><span class="sxs-lookup"><span data-stu-id="b16a5-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="b16a5-140">されることを確認、<xref:System.Windows.Forms.SplitContainer>コントロールの分割バーは水平方向です。</span><span class="sxs-lookup"><span data-stu-id="b16a5-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16a5-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="b16a5-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="b16a5-142">チュートリアル: Windows フォームのコンポーネントへのスマート タグの追加</span><span class="sxs-lookup"><span data-stu-id="b16a5-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
