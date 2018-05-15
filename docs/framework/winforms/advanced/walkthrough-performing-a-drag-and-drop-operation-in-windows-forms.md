---
title: 'チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 6c78a06e37de491e95d56d29c9d2f3e60b88e8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a><span data-ttu-id="e89d7-102">チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行</span><span class="sxs-lookup"><span data-stu-id="e89d7-102">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>
<span data-ttu-id="e89d7-103">Windows ベースのアプリケーション内でドラッグ アンド ドロップ操作を実行する必要がありますを処理する、一連のイベント、特に、 <xref:System.Windows.Forms.Control.DragEnter>、 <xref:System.Windows.Forms.Control.DragLeave>、および<xref:System.Windows.Forms.Control.DragDrop>イベント。</span><span class="sxs-lookup"><span data-stu-id="e89d7-103">To perform drag-and-drop operations within Windows-based applications you must handle a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span> <span data-ttu-id="e89d7-104">情報の操作、使用可能なイベントのこれらのイベントの引数、ドラッグ アンド ドロップ操作を簡単に実現できます。</span><span class="sxs-lookup"><span data-stu-id="e89d7-104">By working with the information available in the event arguments of these events, you can easily facilitate drag-and-drop operations.</span></span>  
  
## <a name="dragging-data"></a><span data-ttu-id="e89d7-105">データのドラッグ</span><span class="sxs-lookup"><span data-stu-id="e89d7-105">Dragging Data</span></span>  
 <span data-ttu-id="e89d7-106">すべてのドラッグ アンド ドロップ操作では、ドラッグから始まります。</span><span class="sxs-lookup"><span data-stu-id="e89d7-106">All drag-and-drop operations begin with dragging.</span></span> <span data-ttu-id="e89d7-107">ドラッグの開始時に収集するデータを有効にする機能は実装、<xref:System.Windows.Forms.Control.DoDragDrop%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e89d7-107">The functionality to enable data to be collected when dragging begins is implemented in the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method.</span></span>  
  
 <span data-ttu-id="e89d7-108">次の例で、<xref:System.Windows.Forms.Control.MouseDown>イベントが最も簡単なになっているために、ドラッグ操作を開始するため (ドラッグ アンド ドロップ操作のほとんどは、マウス ボタンが押されているで始まります)。</span><span class="sxs-lookup"><span data-stu-id="e89d7-108">In the following example, the <xref:System.Windows.Forms.Control.MouseDown> event is used to start the drag operation because it is the most intuitive (most drag-and-drop actions begin with the mouse button being depressed).</span></span> <span data-ttu-id="e89d7-109">ただし、ドラッグ アンド ドロップ手順を開始するすべてのイベントを使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e89d7-109">However, remember that any event could be used to initiate a drag-and-drop procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e89d7-110">特定のコントロールでは、ドラッグに固有のカスタム イベントがあります。</span><span class="sxs-lookup"><span data-stu-id="e89d7-110">Certain controls have custom drag-specific events.</span></span> <span data-ttu-id="e89d7-111"><xref:System.Windows.Forms.ListView>と<xref:System.Windows.Forms.TreeView>コントロール、たとえば、ある、<xref:System.Windows.Forms.TreeView.ItemDrag>イベント。</span><span class="sxs-lookup"><span data-stu-id="e89d7-111">The <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls, for example, have an <xref:System.Windows.Forms.TreeView.ItemDrag> event.</span></span>  
  
#### <a name="to-start-a-drag-operation"></a><span data-ttu-id="e89d7-112">ドラッグ操作を開始するには</span><span class="sxs-lookup"><span data-stu-id="e89d7-112">To start a drag operation</span></span>  
  
1.  <span data-ttu-id="e89d7-113"><xref:System.Windows.Forms.Control.MouseDown> 、ドラッグを開始する場所を使用するコントロールのイベントを`DoDragDrop`ドラッグされるデータを設定するメソッドとドラッグ許可の結果が設定されます。</span><span class="sxs-lookup"><span data-stu-id="e89d7-113">In the <xref:System.Windows.Forms.Control.MouseDown> event for the control where the drag will begin, use the `DoDragDrop` method to set the data to be dragged and the allowed effect dragging will have.</span></span> <span data-ttu-id="e89d7-114">詳細については、<xref:System.Windows.Forms.DragEventArgs.Data%2A> および <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e89d7-114">For more information, see <xref:System.Windows.Forms.DragEventArgs.Data%2A> and <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.</span></span>  
  
     <span data-ttu-id="e89d7-115">次の例では、ドラッグ操作を開始する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-115">The following example shows how to initiate a drag operation.</span></span> <span data-ttu-id="e89d7-116">コントロールのドラッグが開始されるは、<xref:System.Windows.Forms.Button>コントロール、ドラッグされるデータは、文字列を表す、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、<xref:System.Windows.Forms.Button>制御、および許可された効果をコピーまたは移動します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-116">The control where the drag begins is a <xref:System.Windows.Forms.Button> control, the data being dragged is the string representing the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control, and the allowed effects are either copying or moving.</span></span>  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e89d7-117">すべてのデータをパラメーターとして使用できます、`DoDragDrop`メソッド以外の場合は、上記の例では、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、 <xref:System.Windows.Forms.Button> (ではなく、値をハードコーディングまたはデータセットからデータを取得する) にコントロールが使用されたに関連するプロパティがあるため、ドラッグされている場所 (、<xref:System.Windows.Forms.Button>コントロール)。</span><span class="sxs-lookup"><span data-stu-id="e89d7-117">Any data can be used as a parameter in the `DoDragDrop` method; in the example above, the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.Button> control was used (rather than hard-coding a value or retrieving data from a dataset) because the property was related to the location being dragged from (the <xref:System.Windows.Forms.Button> control).</span></span> <span data-ttu-id="e89d7-118">ドラッグ アンド ドロップ操作を Windows ベースのアプリケーションに組み込む場合に、この点に留意してください。</span><span class="sxs-lookup"><span data-stu-id="e89d7-118">Keep this in mind as you incorporate drag-and-drop operations into your Windows-based applications.</span></span>  
  
 <span data-ttu-id="e89d7-119">ドラッグ操作が有効な状態を処理できます、 <xref:System.Windows.Forms.Control.QueryContinueDrag> 「アクセス許可を要求する」イベントのドラッグ操作を続行するシステムです。</span><span class="sxs-lookup"><span data-stu-id="e89d7-119">While a drag operation is in effect, you can handle the <xref:System.Windows.Forms.Control.QueryContinueDrag> event, which "asks permission" of the system to continue the drag operation.</span></span> <span data-ttu-id="e89d7-120">このメソッドを処理する場合も、適切なポイントを展開するなど、ドラッグ操作に影響があるメソッドを呼び出すには<xref:System.Windows.Forms.TreeNode>で、<xref:System.Windows.Forms.TreeView>上にカーソルを合わせるとを制御します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-120">When handling this method, it is also the appropriate point for you to call methods that will have an effect on the drag operation, such as expanding a <xref:System.Windows.Forms.TreeNode> in a <xref:System.Windows.Forms.TreeView> control when the cursor hovers over it.</span></span>  
  
## <a name="dropping-data"></a><span data-ttu-id="e89d7-121">データを削除します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-121">Dropping Data</span></span>  
 <span data-ttu-id="e89d7-122">データの場所から Windows フォームまたはコントロールのドラッグを開始した後は必然的にする任意の場所にドロップします。</span><span class="sxs-lookup"><span data-stu-id="e89d7-122">Once you have begun dragging data from a location on a Windows Form or control, you will naturally want to drop it somewhere.</span></span> <span data-ttu-id="e89d7-123">カーソルは、フォームまたはデータを削除するが正しく構成されているコントロールの領域を超えたときに変更されます。</span><span class="sxs-lookup"><span data-stu-id="e89d7-123">The cursor will change when it crosses an area of a form or control that is correctly configured for dropping data.</span></span> <span data-ttu-id="e89d7-124">設定して削除されたデータを受け入れるように Windows フォームまたはコントロール内の任意の領域ができる、<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティと処理、<xref:System.Windows.Forms.Control.DragEnter>と<xref:System.Windows.Forms.Control.DragDrop>イベント。</span><span class="sxs-lookup"><span data-stu-id="e89d7-124">Any area within a Windows Form or control can be made to accept dropped data by setting the <xref:System.Windows.Forms.Control.AllowDrop%2A> property and handling the <xref:System.Windows.Forms.Control.DragEnter> and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
#### <a name="to-perform-a-drop"></a><span data-ttu-id="e89d7-125">Drop を実行するには</span><span class="sxs-lookup"><span data-stu-id="e89d7-125">To perform a drop</span></span>  
  
1.  <span data-ttu-id="e89d7-126">設定、<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティを true にします。</span><span class="sxs-lookup"><span data-stu-id="e89d7-126">Set the <xref:System.Windows.Forms.Control.AllowDrop%2A> property to true.</span></span>  
  
2.  <span data-ttu-id="e89d7-127">`DragEnter`ドラッグされるデータが適切な型を確実に削除が行われる、コントロールのイベントを (この場合、 <xref:System.Windows.Forms.Control.Text%2A>)。</span><span class="sxs-lookup"><span data-stu-id="e89d7-127">In the `DragEnter` event for the control where the drop will occur, ensure that the data being dragged is of an acceptable type (in this case, <xref:System.Windows.Forms.Control.Text%2A>).</span></span> <span data-ttu-id="e89d7-128">コード内の値にドロップが発生したときに発生する効果を設定し、<xref:System.Windows.Forms.DragDropEffects>列挙します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-128">The code then sets the effect that will happen when the drop occurs to a value in the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span> <span data-ttu-id="e89d7-129">詳細については、「<xref:System.Windows.Forms.DragEventArgs.Effect%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e89d7-129">For more information, see <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e89d7-130">独自に定義することができます<xref:System.Windows.Forms.DataFormats>オブジェクトとして指定することによって、<xref:System.Object>のパラメーター、<xref:System.Windows.Forms.DataObject.SetData%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e89d7-130">You can define your own <xref:System.Windows.Forms.DataFormats> by specifying your own object as the <xref:System.Object> parameter of the <xref:System.Windows.Forms.DataObject.SetData%2A> method.</span></span> <span data-ttu-id="e89d7-131">必要があります、これには、実施する際に指定されたオブジェクトがシリアル化可能であります。</span><span class="sxs-lookup"><span data-stu-id="e89d7-131">Be sure, when doing this, that the object specified is serializable.</span></span> <span data-ttu-id="e89d7-132">詳細については、「<xref:System.Runtime.Serialization.ISerializable>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e89d7-132">For more information, see <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
3.  <span data-ttu-id="e89d7-133"><xref:System.Windows.Forms.Control.DragDrop>を使用して、削除が行われる、コントロールのイベントを<xref:System.Windows.Forms.DataObject.GetData%2A>ドラッグされるデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-133">In the <xref:System.Windows.Forms.Control.DragDrop> event for the control where the drop will occur, use the <xref:System.Windows.Forms.DataObject.GetData%2A> method to retrieve the data being dragged.</span></span> <span data-ttu-id="e89d7-134">詳細については、「<xref:System.Security.Cryptography.Xml.DataObject.Data%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e89d7-134">For more information, see <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.</span></span>  
  
     <span data-ttu-id="e89d7-135">次の例で、<xref:System.Windows.Forms.TextBox>コントロールは、(、削除が行われる) にドラッグされているコントロール。</span><span class="sxs-lookup"><span data-stu-id="e89d7-135">In the example below, a <xref:System.Windows.Forms.TextBox> control is the control being dragged to (where the drop will occur).</span></span> <span data-ttu-id="e89d7-136">コード セット、<xref:System.Windows.Forms.Control.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>ドラッグされるデータと等しいを制御します。</span><span class="sxs-lookup"><span data-stu-id="e89d7-136">The code sets the <xref:System.Windows.Forms.Control.Text%2A> property of the <xref:System.Windows.Forms.TextBox> control equal to the data being dragged.</span></span>  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e89d7-137">さらに、使用できますが、<xref:System.Windows.Forms.DragEventArgs.KeyState%2A>プロパティ、キーによって、ドラッグ アンド ドロップ操作中に押されているように、特定の効果の発生 (たとえば、これは、CTRL キーが押されたときに、ドラッグしたデータをコピーする標準的な)。</span><span class="sxs-lookup"><span data-stu-id="e89d7-137">Additionally, you can work with the <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> property, so that, depending on keys depressed during the drag-and-drop operation, certain effects occur (for example, it is standard to copy the dragged data when the CTRL key is pressed).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89d7-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="e89d7-138">See Also</span></span>  
 [<span data-ttu-id="e89d7-139">方法: クリップボードにデータを追加する</span><span class="sxs-lookup"><span data-stu-id="e89d7-139">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="e89d7-140">方法: クリップボードからデータを取得する</span><span class="sxs-lookup"><span data-stu-id="e89d7-140">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="e89d7-141">ドラッグ アンド ドロップ操作とクリップボードのサポート</span><span class="sxs-lookup"><span data-stu-id="e89d7-141">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
