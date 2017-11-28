---
title: "方法 : Windows フォーム TextBox コントロールでテキストを選択する"
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
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ad19f3daca43fb33e845b632ac7d92b00f544c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="62d03-102">方法 : Windows フォーム TextBox コントロールでテキストを選択する</span><span class="sxs-lookup"><span data-stu-id="62d03-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="62d03-103">Windows フォームでテキストをプログラムで選択できる<xref:System.Windows.Forms.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="62d03-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="62d03-104">たとえば、特定の文字列のテキストを検索する関数を作成する場合は、検索した文字列の位置のリーダーを視覚的にアラートを生成するテキストを選択できます。</span><span class="sxs-lookup"><span data-stu-id="62d03-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="62d03-105">プログラムによってテキストを選択するには</span><span class="sxs-lookup"><span data-stu-id="62d03-105">To select text programmatically</span></span>  
  
1.  <span data-ttu-id="62d03-106">設定、<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>プロパティを選択するテキストの先頭にします。</span><span class="sxs-lookup"><span data-stu-id="62d03-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="62d03-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>プロパティは、数値をテキスト文字列内に挿入ポイントを示す、0、左端の位置。</span><span class="sxs-lookup"><span data-stu-id="62d03-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="62d03-108">場合、<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>プロパティの値に文字数以上になると、テキスト ボックスに、カーソルが最後の文字の後に配置します。</span><span class="sxs-lookup"><span data-stu-id="62d03-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2.  <span data-ttu-id="62d03-109">設定、<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティを選択するテキストの長さをします。</span><span class="sxs-lookup"><span data-stu-id="62d03-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="62d03-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティは、カーソルの幅を設定する数値。</span><span class="sxs-lookup"><span data-stu-id="62d03-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="62d03-111">設定、 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 0 では、この数の文字を選択するとが現在のカーソル位置からの起動に大きい数値にします。</span><span class="sxs-lookup"><span data-stu-id="62d03-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3.  <span data-ttu-id="62d03-112">(省略可能)アクセスを選択したテキスト、<xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="62d03-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="62d03-113">選択以下のコードをテキストの内容ボックスときに、コントロールの<xref:System.Windows.Forms.Control.Enter>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="62d03-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="62d03-114">この例では、テキスト ボックスに値を持つかどうか、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティが`null`または空の文字列。</span><span class="sxs-lookup"><span data-stu-id="62d03-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="62d03-115">テキスト ボックスにフォーカスが移動すると、テキスト ボックスの現在のテキストが選択されます。</span><span class="sxs-lookup"><span data-stu-id="62d03-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="62d03-116">`TextBox1_Enter`イベント ハンドラーが; 詳細については、コントロールにバインドする必要がありますを参照してください[する方法: Windows フォームの時間の実行時のイベント ハンドラーの作成](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="62d03-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="62d03-117">この例をテストするには、テキスト ボックスにフォーカスがあるまで Tab キーを押します。</span><span class="sxs-lookup"><span data-stu-id="62d03-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="62d03-118">テキスト ボックスをクリックし場合、テキストは選択できません。</span><span class="sxs-lookup"><span data-stu-id="62d03-118">If you click in the text box, the text is unselected.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="62d03-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="62d03-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="62d03-120">TextBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="62d03-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="62d03-121">方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する</span><span class="sxs-lookup"><span data-stu-id="62d03-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="62d03-122">方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="62d03-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="62d03-123">方法: 読み取り専用テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="62d03-123">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="62d03-124">方法: 文字列に引用符を挿入する</span><span class="sxs-lookup"><span data-stu-id="62d03-124">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="62d03-125">方法: Windows フォーム TextBox コントロールで複数行を表示する</span><span class="sxs-lookup"><span data-stu-id="62d03-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="62d03-126">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="62d03-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
