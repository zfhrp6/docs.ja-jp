---
title: "方法 : アクティブな MDI 子フォームを特定する"
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
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c026df631c2ac033594ea86887bb8440a6aa240a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="3e6bf-102">方法 : アクティブな MDI 子フォームを特定する</span><span class="sxs-lookup"><span data-stu-id="3e6bf-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="3e6bf-103">場合によっては、現在アクティブな子フォームにフォーカスを持つコントロールが操作するコマンドを提供するされます。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="3e6bf-104">たとえば、子フォームのテキスト ボックスから選択したテキストをクリップボードにコピーするとします。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="3e6bf-105">クリップボードを使用して、選択したテキストをコピーするプロシージャを作成すると、<xref:System.Windows.Forms.Control.Click>コピー メニュー項目の編集 メニューの標準的なイベントです。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="3e6bf-106">MDI アプリケーションでは、同じ子フォームの多くのインスタンスを持つことができますため、プロシージャを使用するフォームを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="3e6bf-107">正しい形式を指定するには、使用、<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>プロパティで、フォーカスを持っているか、最後にアクティブになった子フォームを返します。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="3e6bf-108">フォーム上のいくつかのコントロールがある場合は、どのコントロールがアクティブなを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="3e6bf-109">同様に、 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> 、プロパティ、<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>プロパティは、アクティブな子フォームにフォーカスがあるコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="3e6bf-110">次の手順は、子フォームのメニューを MDI フォームまたはツール バー ボタンのメニューから呼び出すことができるコピー手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="3e6bf-111">アクティブな MDI 子ウィンドウ (テキストをクリップボードにコピーします) を決定するには</span><span class="sxs-lookup"><span data-stu-id="3e6bf-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1.  <span data-ttu-id="3e6bf-112">メソッド内には、アクティブな子フォームのアクティブ コントロールのテキストをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e6bf-113">この例では、MDI 親フォームがある (`Form1`) を含む 1 つまたは複数の MDI 子ウィンドウを持つ、<xref:System.Windows.Forms.RichTextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="3e6bf-114">詳細については、次を参照してください。 [MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e6bf-114">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3e6bf-115">参照</span><span class="sxs-lookup"><span data-stu-id="3e6bf-115">See Also</span></span>  
 [<span data-ttu-id="3e6bf-116">マルチ ドキュメント インターフェイス (MDI) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3e6bf-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="3e6bf-117">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="3e6bf-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="3e6bf-118">方法: MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="3e6bf-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="3e6bf-119">方法: アクティブな MDI 子フォームにデータを送信する</span><span class="sxs-lookup"><span data-stu-id="3e6bf-119">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="3e6bf-120">方法: MDI 子フォームを配置する</span><span class="sxs-lookup"><span data-stu-id="3e6bf-120">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
