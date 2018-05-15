---
title: 'チュートリアル : MaskedTextBox コントロールの使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: bcca6c5f5481d351a39a4e71532cc0f006075128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="8d811-102">チュートリアル : MaskedTextBox コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="8d811-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="8d811-103">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="8d811-103">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="8d811-104">初期化中、<xref:System.Windows.Forms.MaskedTextBox>コントロール</span><span class="sxs-lookup"><span data-stu-id="8d811-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
-   <span data-ttu-id="8d811-105">使用して、<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>文字がマスクに準拠していないときにユーザーに警告するイベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="8d811-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
-   <span data-ttu-id="8d811-106">型を割り当てる、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>プロパティを使用して、<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>をコミットしようとしている値の型の有効な場合、ユーザーのアラートを生成するイベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="8d811-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="8d811-107">プロジェクトを作成して、コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="8d811-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="8d811-108">MaskedTextBox コントロールをフォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="8d811-108">To add a MaskedTextBox control to your form</span></span>  
  
1.  <span data-ttu-id="8d811-109">配置するフォームを開いて、<xref:System.Windows.Forms.MaskedTextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8d811-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2.  <span data-ttu-id="8d811-110">ドラッグ、<xref:System.Windows.Forms.MaskedTextBox>から制御、**ツールボックス**をフォームにします。</span><span class="sxs-lookup"><span data-stu-id="8d811-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3.  <span data-ttu-id="8d811-111">コントロールを右クリックして選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="8d811-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="8d811-112">**プロパティ**ウィンドウで、**マスク**プロパティをクリックして、**しています.** プロパティ名の横にある (省略記号) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8d811-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4.  <span data-ttu-id="8d811-113">**定型入力**ダイアログ ボックスで、**短い日付**マスクし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="8d811-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5.  <span data-ttu-id="8d811-114">**プロパティ**ウィンドウのセット、<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="8d811-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="8d811-115">このプロパティはにより、ビープ音を鳴らすたびに、ユーザーが、マスク定義に違反する文字を入力しようとしています。 です。</span><span class="sxs-lookup"><span data-stu-id="8d811-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="8d811-116">概要については、マスクのプロパティをサポートする文字のの「解説」セクションを参照してください、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8d811-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="8d811-117">入力エラーをユーザーに警告します。</span><span class="sxs-lookup"><span data-stu-id="8d811-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="8d811-118">拒否されたマスクの入力のバルーン ヒントを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d811-118">Add a balloon tip for rejected mask input</span></span>  
  
1.  <span data-ttu-id="8d811-119">戻り、**ツールボックス**を追加し、<xref:System.Windows.Forms.ToolTip>をフォームにします。</span><span class="sxs-lookup"><span data-stu-id="8d811-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2.  <span data-ttu-id="8d811-120">イベント ハンドラーを作成、<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>イベントを発生させる、<xref:System.Windows.Forms.ToolTip>入力エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8d811-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="8d811-121">バルーン ヒントは引き続き、5 秒間のまたは、ユーザーがクリックするまで表示します。</span><span class="sxs-lookup"><span data-stu-id="8d811-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="8d811-122">無効な型をユーザーに警告します。</span><span class="sxs-lookup"><span data-stu-id="8d811-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="8d811-123">無効なデータ型のバルーン ヒントを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d811-123">Add a balloon tip for invalid data types</span></span>  
  
1.  <span data-ttu-id="8d811-124">フォームの<xref:System.Windows.Forms.Form.Load>、イベント ハンドラーを割り当てます、<xref:System.Type>オブジェクトを表す、<xref:System.DateTime>型を<xref:System.Windows.Forms.MaskedTextBox>コントロールの<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>プロパティ。</span><span class="sxs-lookup"><span data-stu-id="8d811-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="8d811-125"><xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> イベントのイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d811-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8d811-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d811-126">See Also</span></span>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [<span data-ttu-id="8d811-127">MaskedTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="8d811-127">MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
