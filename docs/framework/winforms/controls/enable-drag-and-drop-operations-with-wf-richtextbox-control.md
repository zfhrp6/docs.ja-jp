---
title: "方法 : Windows フォームの RichTextBox コントロールにおけるドラッグ アンド ドロップ操作を有効にする"
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
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8497f0c13fece9c6a2b3ca2d1d2df0d427c605e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="06456-102">方法 : Windows フォームの RichTextBox コントロールにおけるドラッグ アンド ドロップ操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="06456-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="06456-103">Windows フォームでのドラッグ アンド ドロップ操作の <xref:System.Windows.Forms.RichTextBox> コントロールは、 <xref:System.Windows.Forms.RichTextBox.DragEnter> および <xref:System.Windows.Forms.RichTextBox.DragDrop> イベントを処理すると実行されます。</span><span class="sxs-lookup"><span data-stu-id="06456-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="06456-104">そのため、ドラッグ アンド ドロップの操作は <xref:System.Windows.Forms.RichTextBox> コントロールを使用すると非常にシンプルです。</span><span class="sxs-lookup"><span data-stu-id="06456-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="06456-105">RichTextBox コントロールでドラッグ操作を有効にするには</span><span class="sxs-lookup"><span data-stu-id="06456-105">To enable drag operations in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="06456-106"><xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> プロパティの <xref:System.Windows.Forms.RichTextBox> コントロールを `true`に設定します。</span><span class="sxs-lookup"><span data-stu-id="06456-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2.  <span data-ttu-id="06456-107"><xref:System.Windows.Forms.RichTextBox.DragEnter> イベントのイベント ハンドラーで適切なコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="06456-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="06456-108">`if` ステートメントを使用して、ドラッグされるデータが適切な型 (この場合はテキスト) であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="06456-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="06456-109"><xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> プロパティは、いずれかの <xref:System.Windows.Forms.DragDropEffects> 列挙値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="06456-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="06456-110">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="06456-110">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3.  <span data-ttu-id="06456-111"><xref:System.Windows.Forms.RichTextBox.DragDrop> イベントを処理するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="06456-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="06456-112"><xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> メソッドを使用してドラッグされるデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="06456-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="06456-113">次の例では、コードは、ドラッグされるデータに相当する <xref:System.Windows.Forms.RichTextBox.Text%2A> コントロールの <xref:System.Windows.Forms.RichTextBox> のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="06456-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="06456-114"><xref:System.Windows.Forms.RichTextBox> コントロール内にすでにテキストがある場合、ドラッグされたデータが挿入ポイントに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="06456-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragDrop  
       Dim i As Int16   
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +   
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());   
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="06456-115">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="06456-115">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew   
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="06456-116">アプリケーションでドラッグ アンド ドロップ機能をテストするには</span><span class="sxs-lookup"><span data-stu-id="06456-116">To test the drag-and-drop functionality in your application</span></span>  
  
1.  <span data-ttu-id="06456-117">アプリケーションを保存し、ビルドします。</span><span class="sxs-lookup"><span data-stu-id="06456-117">Save and build your application.</span></span> <span data-ttu-id="06456-118">実行中にワードパッドを起動します。</span><span class="sxs-lookup"><span data-stu-id="06456-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="06456-119">ワードパッドは、Windows によってインストールされるテキスト エディターであり、ドラッグ アンド ドロップ操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="06456-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="06456-120">ワードパッドを起動するには、 **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]**を選択し、 `WordPad` [ファイル名を指定して実行] **ダイアログ ボックスのテキスト ボックスに「** 」と入力し、 **[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="06456-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="06456-121">ワードパッドが起動したら、テキストの文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="06456-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="06456-122">マウスを使用してテキストを選択し、選択したテキストを Windows アプリケーションの <xref:System.Windows.Forms.RichTextBox> コントロールにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="06456-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="06456-123">マウスを <xref:System.Windows.Forms.RichTextBox> コントロールに移動すると (そして、その結果 <xref:System.Windows.Forms.RichTextBox.DragEnter> イベントが発生すると)、マウス ポインターの形が変化し、選択したテキストを <xref:System.Windows.Forms.RichTextBox> コントロールにドロップできます。</span><span class="sxs-lookup"><span data-stu-id="06456-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="06456-124">マウス ボタンを放すと、選択したテキストがドロップ (つまり <xref:System.Windows.Forms.RichTextBox.DragDrop> イベントが発生) し、 <xref:System.Windows.Forms.RichTextBox> コントロール内に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="06456-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06456-125">参照</span><span class="sxs-lookup"><span data-stu-id="06456-125">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="06456-126">方法: アプリケーション間でドラッグ アンド ドロップ操作を実行する</span><span class="sxs-lookup"><span data-stu-id="06456-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 [<span data-ttu-id="06456-127">RichTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="06456-127">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="06456-128">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="06456-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
