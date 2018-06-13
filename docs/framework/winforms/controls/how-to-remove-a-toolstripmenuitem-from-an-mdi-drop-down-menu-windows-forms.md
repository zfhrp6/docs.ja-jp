---
title: '方法: ToolStripMenuItem を MDI ドロップダウン メニューから削除する (Windows フォーム) '
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 0649e99c682464928aaae68451b2cb29d5675485
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540518"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="83cde-102">方法: ToolStripMenuItem を MDI ドロップダウン メニューから削除する (Windows フォーム) </span><span class="sxs-lookup"><span data-stu-id="83cde-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="83cde-103">アプリケーションの中には、マルチ ドキュメント インターフェイス (MDI) 子ウィンドウの種類が MDI 親ウィンドウと異なるものがあります。</span><span class="sxs-lookup"><span data-stu-id="83cde-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="83cde-104">たとえば、MDI 親がスプレッドシートで、MDI 子がグラフの場合があります。</span><span class="sxs-lookup"><span data-stu-id="83cde-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="83cde-105">そのような場合は、異なる種類の MDI 子ウィンドウがアクティブになったときに、MDI 子メニューの内容で MDI 親メニューの内容を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83cde-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="83cde-106">次の手順を使用して、 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、 <xref:System.Windows.Forms.MergeAction>、および<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>MDI 親メニューのドロップダウン部分からメニュー項目を削除するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="83cde-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="83cde-107">MDI 子ウィンドウを閉じると、MDI 親メニューに削除したメニュー項目が復元します。</span><span class="sxs-lookup"><span data-stu-id="83cde-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="83cde-108">MenuStrip を MDI ドロップダウン メニューから削除するには</span><span class="sxs-lookup"><span data-stu-id="83cde-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1.  <span data-ttu-id="83cde-109">フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="83cde-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="83cde-110"><xref:System.Windows.Forms.MenuStrip> を `Form1` に追加し、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="83cde-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3.  <span data-ttu-id="83cde-111">トップレベル メニュー項目を `Form1` の <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.Control.Text%2A> プロパティを「`&File`」に設定しますす。</span><span class="sxs-lookup"><span data-stu-id="83cde-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4.  <span data-ttu-id="83cde-112">次の 3 つのサブメニュー項目を追加、`&File`メニュー項目とセット、<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティ`&Open`、 `&Import from`、および`E&xit`です。</span><span class="sxs-lookup"><span data-stu-id="83cde-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5.  <span data-ttu-id="83cde-113">2 つのサブメニュー項目を追加、`&Import from`サブメニュー項目とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&Word`と`&Excel`です。</span><span class="sxs-lookup"><span data-stu-id="83cde-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6.  <span data-ttu-id="83cde-114">プロジェクトにフォームを追加し、フォームに <xref:System.Windows.Forms.MenuStrip> を追加し、`Form2` の <xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> のプロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="83cde-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7.  <span data-ttu-id="83cde-115">トップレベル メニュー項目を `Form2` の <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを「`&File`」に設定しますす。</span><span class="sxs-lookup"><span data-stu-id="83cde-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8.  <span data-ttu-id="83cde-116">追加、`&Import from`サブメニュー項目を`&File`のメニュー `Form2`、追加し、`&Word`サブメニュー項目を`&File`メニュー。</span><span class="sxs-lookup"><span data-stu-id="83cde-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="83cde-117">設定、<xref:System.Windows.Forms.MergeAction>と<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>のプロパティ、`Form2`メニュー項目を次の表に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="83cde-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="83cde-118">Form2 メニュー項目</span><span class="sxs-lookup"><span data-stu-id="83cde-118">Form2 menu item</span></span>|<span data-ttu-id="83cde-119">MergeAction 値</span><span class="sxs-lookup"><span data-stu-id="83cde-119">MergeAction value</span></span>|<span data-ttu-id="83cde-120">MergeIndex 値</span><span class="sxs-lookup"><span data-stu-id="83cde-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="83cde-121">ファイル</span><span class="sxs-lookup"><span data-stu-id="83cde-121">File</span></span>|<span data-ttu-id="83cde-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="83cde-122">MatchOnly</span></span>|<span data-ttu-id="83cde-123">-1</span><span class="sxs-lookup"><span data-stu-id="83cde-123">-1</span></span>|  
    |<span data-ttu-id="83cde-124">インポートします。</span><span class="sxs-lookup"><span data-stu-id="83cde-124">Import from</span></span>|<span data-ttu-id="83cde-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="83cde-125">MatchOnly</span></span>|<span data-ttu-id="83cde-126">-1</span><span class="sxs-lookup"><span data-stu-id="83cde-126">-1</span></span>|  
    |<span data-ttu-id="83cde-127">Word</span><span class="sxs-lookup"><span data-stu-id="83cde-127">Word</span></span>|<span data-ttu-id="83cde-128">削除</span><span class="sxs-lookup"><span data-stu-id="83cde-128">Remove</span></span>|<span data-ttu-id="83cde-129">-1</span><span class="sxs-lookup"><span data-stu-id="83cde-129">-1</span></span>|  
  
10. <span data-ttu-id="83cde-130">`Form1`、イベント ハンドラーを作成、<xref:System.Windows.Forms.Control.Click>のイベント、 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>です。</span><span class="sxs-lookup"><span data-stu-id="83cde-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="83cde-131">イベント ハンドラー内で作成しの新しいインスタンスを表示するコード例を次のようなコードを挿入`Form2`の MDI 子フォームとして`Form1`:</span><span class="sxs-lookup"><span data-stu-id="83cde-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="83cde-132">`&Open`<xref:System.Windows.Forms.ToolStripMenuItem> に次のコード例のようなコードを配置し、イベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="83cde-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83cde-133">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="83cde-133">Compiling the Code</span></span>  
 <span data-ttu-id="83cde-134">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="83cde-134">This example requires:</span></span>  
  
-   <span data-ttu-id="83cde-135">`Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。</span><span class="sxs-lookup"><span data-stu-id="83cde-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="83cde-136">`Form1` 上の `menuStrip1` という名前の <xref:System.Windows.Forms.MenuStrip> コントロールと、`Form2` 上の `menuStrip2` という名前の <xref:System.Windows.Forms.MenuStrip> コントロール。</span><span class="sxs-lookup"><span data-stu-id="83cde-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="83cde-137"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="83cde-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cde-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="83cde-138">See Also</span></span>  
 [<span data-ttu-id="83cde-139">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="83cde-139">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="83cde-140">方法: MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="83cde-140">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="83cde-141">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="83cde-141">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
