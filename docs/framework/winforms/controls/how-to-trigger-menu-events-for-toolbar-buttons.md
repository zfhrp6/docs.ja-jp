---
title: "方法: ツール バー ボタンのメニュー イベントをトリガーする"
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
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80d28bdb85a91ddd3129e7e0fab443f81ba9ecef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="bf40c-102">方法: ツール バー ボタンのメニュー イベントをトリガーする</span><span class="sxs-lookup"><span data-stu-id="bf40c-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
>  <span data-ttu-id="bf40c-103"><xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="bf40c-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="bf40c-104">場合、Windows フォームの機能、<xref:System.Windows.Forms.ToolBar>コントロール ツール バー ボタンにするかを知りたいユーザーがクリックしたボタンします。</span><span class="sxs-lookup"><span data-stu-id="bf40c-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="bf40c-105"><xref:System.Windows.Forms.ToolBar.ButtonClick>のイベント、<xref:System.Windows.Forms.ToolBar>を評価できるコントロール、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A>のプロパティ、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>クラスです。</span><span class="sxs-lookup"><span data-stu-id="bf40c-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="bf40c-106">次の例では、クリックされたボタンを示すメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf40c-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="bf40c-107">詳細については、「<xref:System.Windows.Forms.MessageBox>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf40c-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="bf40c-108">次の例では、<xref:System.Windows.Forms.ToolBar>を Windows フォーム コントロールが追加されました。</span><span class="sxs-lookup"><span data-stu-id="bf40c-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="bf40c-109">ツール バーの Click イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="bf40c-109">To handle the Click event on a toolbar</span></span>  
  
1.  <span data-ttu-id="bf40c-110">プロシージャでは、ツール バー ボタンを追加、<xref:System.Windows.Forms.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bf40c-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()   
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=   
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=   
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2.  <span data-ttu-id="bf40c-111">イベント ハンドラーを追加、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.ButtonClick>イベント。</span><span class="sxs-lookup"><span data-stu-id="bf40c-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="bf40c-112">ケース ステートメントの切り替えを使用して、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>ツールバーのボタンがクリックされたを決めるクラスをします。</span><span class="sxs-lookup"><span data-stu-id="bf40c-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="bf40c-113">この結果に基づいて、適切なメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf40c-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf40c-114">この例では、メッセージ ボックスは、プレースホルダーとして単独で使用されています。</span><span class="sxs-lookup"><span data-stu-id="bf40c-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="bf40c-115">ツール バーのボタンがクリックされたときに実行するコードは、自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="bf40c-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bf40c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf40c-116">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="bf40c-117">方法: ツール バー コントロールにボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="bf40c-117">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [<span data-ttu-id="bf40c-118">方法: ツール バー ボタンのアイコンを定義する</span><span class="sxs-lookup"><span data-stu-id="bf40c-118">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [<span data-ttu-id="bf40c-119">ToolBar コントロール</span><span class="sxs-lookup"><span data-stu-id="bf40c-119">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
