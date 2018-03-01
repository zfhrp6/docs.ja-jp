---
title: "TextBox コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="89f4a-102">TextBox コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="89f4a-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="89f4a-103">Windows フォームのテキスト ボックスは、ユーザーからの入力を取得またはテキストの表示に使用されます。</span><span class="sxs-lookup"><span data-stu-id="89f4a-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="89f4a-104"><xref:System.Windows.Forms.TextBox>コントロールもにできる読み取り専用ですが、一般に編集可能なテキストは、使用できます。</span><span class="sxs-lookup"><span data-stu-id="89f4a-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="89f4a-105">テキスト ボックスでは、複数の行を表示、コントロールのサイズにテキストを折り返す、および基本的な書式を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="89f4a-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="89f4a-106"><xref:System.Windows.Forms.TextBox>コントロールが表示またはコントロールに入力されたテキストに対して単一の書式スタイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="89f4a-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="89f4a-107">表示するには複数の書式設定されたテキストの種類を使用して、<xref:System.Windows.Forms.RichTextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="89f4a-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="89f4a-108">詳細については、次を参照してください。 [RichTextBox コントロールの概要](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="89f4a-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="89f4a-109">TextBox コントロールの操作</span><span class="sxs-lookup"><span data-stu-id="89f4a-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="89f4a-110">コントロールによって表示されるテキストに含まれている、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="89f4a-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="89f4a-111">既定では、最大 2048 文字のテキスト ボックスに入力できます。</span><span class="sxs-lookup"><span data-stu-id="89f4a-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="89f4a-112">設定した場合、<xref:System.Windows.Forms.TextBox.Multiline%2A>プロパティを`true`、最大 32 KB のテキストを入力することができます。</span><span class="sxs-lookup"><span data-stu-id="89f4a-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="89f4a-113"><xref:System.Windows.Forms.TextBox.Text%2A>デザイン時のプロパティ ウィンドウで、実行時コード、またはユーザーの入力によって実行時にプロパティを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="89f4a-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="89f4a-114">テキスト ボックスの現在の内容は、読み取りを実行時に取得できる、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="89f4a-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="89f4a-115">次のコード例は、実行時に、コントロール内のテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="89f4a-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="89f4a-116">`InitializeMyControl`プロシージャが自動的に実行されません。 呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="89f4a-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="89f4a-117">参照</span><span class="sxs-lookup"><span data-stu-id="89f4a-117">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="89f4a-118">方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する</span><span class="sxs-lookup"><span data-stu-id="89f4a-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="89f4a-119">方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="89f4a-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="89f4a-120">方法: 読み取り専用テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="89f4a-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="89f4a-121">方法: 文字列に引用符を挿入する</span><span class="sxs-lookup"><span data-stu-id="89f4a-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="89f4a-122">方法: Windows フォーム TextBox コントロールでテキストを選択する</span><span class="sxs-lookup"><span data-stu-id="89f4a-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="89f4a-123">方法: Windows フォーム TextBox コントロールで複数行を表示する</span><span class="sxs-lookup"><span data-stu-id="89f4a-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="89f4a-124">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="89f4a-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
