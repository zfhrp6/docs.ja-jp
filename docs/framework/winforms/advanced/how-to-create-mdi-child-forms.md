---
title: "方法 : MDI 子フォームを作成する"
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
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bbbe8dbbfa6b2aebd3834314f0f56b7c7643c21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="4a6bb-102">方法 : MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="4a6bb-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="4a6bb-103">MDI 子フォームの不可欠な要素は、[マルチ ドキュメント インターフェイス (MDI) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)ユーザー操作の中心となるため、します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="4a6bb-104">次の手順では、ほとんどのワード プロセッシング アプリケーションに似ている <xref:System.Windows.Forms.RichTextBox> コントロールを表示する MDI 子フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="4a6bb-105"><xref:System.Windows.Forms> コントロールを、<xref:System.Windows.Forms.DataGridView> コントロールやコントロールを組み合わせたその他のコントロールで置き換えることで、さまざまな可能性のある MDI 子ウィンドウ (およびその拡張としての MDI アプリケーション) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a6bb-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4a6bb-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4a6bb-108">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="4a6bb-109">MDI 子フォームを作成するには</span><span class="sxs-lookup"><span data-stu-id="4a6bb-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="4a6bb-110">新しい Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="4a6bb-111">**プロパティ ウィンドウ**、フォームの次のように設定します。 その<xref:System.Windows.Forms.Form.IsMdiContainer%2A>プロパティを`true`、およびその`WindowsState`プロパティを`Maximized`です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="4a6bb-112">これによって、フォームが子ウィンドウの MDI コンテナーとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="4a6bb-113">`Toolbox` から、<xref:System.Windows.Forms.MenuStrip> コントロールをフォームにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="4a6bb-114">設定の`Text`プロパティを**ファイル**です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="4a6bb-115">横にある省略記号 (...) をクリックして、**項目**プロパティ、およびクリック**追加**を 2 つの子ツール ストリップのメニュー項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="4a6bb-116">設定、`Text`プロパティにこれらの項目を**新規**と**ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="4a6bb-117">**ソリューション エクスプ ローラー**プロジェクトを右クリックしをポイントし、**追加**、し、**新しい項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="4a6bb-118">**新しい項目の追加**ダイアログ ボックスで、 **Windows フォーム**(で[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]または[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) または**Windows フォーム アプリケーション (.NET)** (で[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-118">In the **Add New Item** dialog box, select **Windows Form** (in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="4a6bb-119">**名前**ボックスに、フォームを名前**Form2**です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="4a6bb-120">クリックして、**開く**フォームをプロジェクトに追加するボタンです。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a6bb-121">この手順で作成した、MDI 子フォームは、標準の Windows フォームです。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="4a6bb-122">そのため、フォームの透明度を制御できる <xref:System.Windows.Forms.Form.Opacity%2A> プロパティを持っています。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="4a6bb-123">ただし、<xref:System.Windows.Forms.Form.Opacity%2A> プロパティは最上位レベルのウィンドウ用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="4a6bb-124">描画に関する問題が発生する可能性があるため、MDI 子フォームと共に使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="4a6bb-125">このフォームは、MDI 子フォーム用のテンプレートになります。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="4a6bb-126">**Windows フォーム デザイナー**が開き、表示する**Form2**です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="4a6bb-127">**ツールボックス**、ドラッグ、 **RichTextBox**をフォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="4a6bb-128">**プロパティ**ウィンドウで、設定、`Anchor`プロパティを**Top、Left**と`Dock`プロパティを**塗りつぶし**です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="4a6bb-129">これにより、フォームがサイズ変更された場合でも、<xref:System.Windows.Forms.RichTextBox> コントロールが MDI 子フォームの領域を完全に塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="4a6bb-130">ダブルクリックして、**新規**メニュー項目を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="4a6bb-131">ユーザーがクリックしたときに、新しい MDI 子フォームを作成するには、次のようなコードを挿入、**新規**メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a6bb-132">次の例では、イベント ハンドラーが `MenuItem2` の <xref:System.Windows.Forms.Control.Click> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="4a6bb-133">注意して、アプリケーション アーキテクチャの仕様によっては、**新規**メニュー項目ができない可能性があります`MenuItem2`です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     <span data-ttu-id="4a6bb-134">[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] で、次の `#include` ディレクティブを Form1.h の先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="4a6bb-135">上部にあるドロップダウン リストで、**プロパティ**ウィンドウに対応するメニュー ストリップを選択して、**ファイル** メニュー ストリップと、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティを Window<xref:System.Windows.Forms.ToolStripMenuItem>です。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="4a6bb-136">これにより、**ウィンドウ** メニューのアクティブな子ウィンドウの横にチェック マークが付いた開いている MDI 子ウィンドウのリストを保持します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="4a6bb-137">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-137">Press F5 to run the application.</span></span> <span data-ttu-id="4a6bb-138">選択して**新規**から、**ファイル**] メニューの [新しい MDI 子フォームでの保持を作成することができます、**ウィンドウ**メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a6bb-139">MDI 子フォームが (通常はメニュー項目のメニュー構造を持つ) <xref:System.Windows.Forms.MainMenu> コンポーネントを持っていて、(通常はメニュー項目のメニュー構造を持つ) <xref:System.Windows.Forms.MainMenu> コンポーネントを持つ MDI 親フォーム内で開いている場合、<xref:System.Windows.Forms.MenuItem.MergeType%2A> プロパティ (およびオプションで <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> プロパティ) を設定した場合に、メニュー項目が自動的にマージされます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="4a6bb-140">両方の <xref:System.Windows.Forms.MainMenu> コンポーネント、および子フォームのすべてのメニュー項目の <xref:System.Windows.Forms.MenuItem.MergeType%2A> プロパティを <xref:System.Windows.Forms.MenuMerge.MergeItems> に設定します。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="4a6bb-141">また、<xref:System.Windows.Forms.MenuItem.MergeOrder%2A> プロパティを設定し、両方のメニューのメニュー項目が指定した順序で表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="4a6bb-142">さらに、MDI 親フォームを閉じた時に、MDI 親の <xref:System.Windows.Forms.Form.Closing> イベントが発生する前に、各 MDI 子フォームが <xref:System.Windows.Forms.Form.Closing> イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="4a6bb-143">MDI 子の <xref:System.Windows.Forms.Form.Closing> イベントをキャンセルしても、MDI 親の <xref:System.Windows.Forms.Form.Closing> イベントの発生を防ぐことはできません。ただし、MDI 親の <xref:System.Windows.Forms.Form.Closing> イベントの <xref:System.ComponentModel.CancelEventArgs> 引数は `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="4a6bb-144"><xref:System.ComponentModel.CancelEventArgs> 引数を `false` に設定することで、MDI 親レポートとすべての MDI 子フォームを強制的に閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="4a6bb-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6bb-145">参照</span><span class="sxs-lookup"><span data-stu-id="4a6bb-145">See Also</span></span>  
 [<span data-ttu-id="4a6bb-146">マルチ ドキュメント インターフェイス (MDI) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4a6bb-146">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="4a6bb-147">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="4a6bb-147">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="4a6bb-148">方法: アクティブな MDI 子フォームを特定する</span><span class="sxs-lookup"><span data-stu-id="4a6bb-148">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="4a6bb-149">方法: アクティブな MDI 子フォームにデータを送信する</span><span class="sxs-lookup"><span data-stu-id="4a6bb-149">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="4a6bb-150">方法: MDI 子フォームを配置する</span><span class="sxs-lookup"><span data-stu-id="4a6bb-150">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
