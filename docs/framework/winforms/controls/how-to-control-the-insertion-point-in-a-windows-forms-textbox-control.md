---
title: '方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: ced563eb063bbcc429cdf1447a0158459e5d5c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530739"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="fd588-102">方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する</span><span class="sxs-lookup"><span data-stu-id="fd588-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="fd588-103">Windows フォーム<xref:System.Windows.Forms.TextBox>コントロールが最初にフォーカスを受け取る、既存のテキストの左側には、テキスト ボックス内の既定のカーソル。</span><span class="sxs-lookup"><span data-stu-id="fd588-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="fd588-104">ユーザーは、キーボードまたはマウスのカーソルを移動できます。</span><span class="sxs-lookup"><span data-stu-id="fd588-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="fd588-105">テキスト ボックスを失い、フォーカスを得た場合、挿入ポイントされます任意の場所、ユーザー最後置かれます。</span><span class="sxs-lookup"><span data-stu-id="fd588-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="fd588-106">場合によっては、この動作は、ユーザーに混乱を招くことがあります。</span><span class="sxs-lookup"><span data-stu-id="fd588-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="fd588-107">ユーザーのワード プロセッシング アプリケーションで、既存のテキストの後に表示する新しい文字と思ったかもしれません。</span><span class="sxs-lookup"><span data-stu-id="fd588-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="fd588-108">データ エントリのアプリケーションでは、ユーザーは、既存のエントリを置き換える新しい文字と思ったかもしれません。</span><span class="sxs-lookup"><span data-stu-id="fd588-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="fd588-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>と<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>を目的に合わせて動作を変更するプロパティが有効にします。</span><span class="sxs-lookup"><span data-stu-id="fd588-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="fd588-110">TextBox コントロールのカーソル位置を制御するには</span><span class="sxs-lookup"><span data-stu-id="fd588-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="fd588-111"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="fd588-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="fd588-112">0 は、最初の文字の左側にすぐにカーソルを配置します。</span><span class="sxs-lookup"><span data-stu-id="fd588-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="fd588-113">(省略可能)設定、<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティを選択するテキストの長さをします。</span><span class="sxs-lookup"><span data-stu-id="fd588-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="fd588-114">次のコードは、常に 0 に挿入ポイントを返します。</span><span class="sxs-lookup"><span data-stu-id="fd588-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="fd588-115">`TextBox1_Enter`イベント ハンドラーが; 詳細については、コントロールにバインドする必要がありますを参照してください[Windows フォームでのイベント ハンドラーの作成](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd588-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="fd588-116">カーソルを既定で表示します。</span><span class="sxs-lookup"><span data-stu-id="fd588-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="fd588-117"><xref:System.Windows.Forms.TextBox>挿入ポイントが既定では、新しいフォーム場合にのみに表示される、<xref:System.Windows.Forms.TextBox>コントロールがタブ オーダーの先頭にします。</span><span class="sxs-lookup"><span data-stu-id="fd588-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="fd588-118">挿入ポイントが提供する場合にのみを表示するそれ以外の場合、<xref:System.Windows.Forms.TextBox>キーボードまたはマウスでフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="fd588-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="fd588-119">新しいフォームに既定では、テキスト ボックスの挿入ポイントを表示する</span><span class="sxs-lookup"><span data-stu-id="fd588-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="fd588-120">設定、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティを`0`です。</span><span class="sxs-lookup"><span data-stu-id="fd588-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd588-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd588-121">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="fd588-122">TextBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="fd588-122">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="fd588-123">方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="fd588-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fd588-124">方法: 読み取り専用テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="fd588-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="fd588-125">方法: 文字列に引用符を挿入する</span><span class="sxs-lookup"><span data-stu-id="fd588-125">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="fd588-126">方法: Windows フォーム TextBox コントロールでテキストを選択する</span><span class="sxs-lookup"><span data-stu-id="fd588-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fd588-127">方法: Windows フォーム TextBox コントロールで複数行を表示する</span><span class="sxs-lookup"><span data-stu-id="fd588-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="fd588-128">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="fd588-128">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
