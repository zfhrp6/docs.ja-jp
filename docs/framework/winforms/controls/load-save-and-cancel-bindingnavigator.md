---
title: '方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 8f331c67dd22a6a9e2382ecc11d23c67cd2a5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540492"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="2f8c4-102">方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="2f8c4-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="2f8c4-103"><xref:System.Windows.Forms.BindingNavigator>コントロールは、特別な用途<xref:System.Windows.Forms.ToolStrip>コントロールを移動して、データにバインドされている、フォーム上のコントロールを操作対象とします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="2f8c4-104">なっているため、<xref:System.Windows.Forms.ToolStrip>コントロール、<xref:System.Windows.Forms.BindingNavigator>コンポーネントは、ユーザーの追加または代替のコマンドを含める簡単に変更できます。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="2f8c4-105">次の手順で、<xref:System.Windows.Forms.TextBox>コントロールは、データにバインドされ、<xref:System.Windows.Forms.ToolStrip>をフォームに追加されたコントロールは、保存、負荷を含めるし、キャンセル ボタンに変更します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="2f8c4-106">負荷を追加するには、保存、およびキャンセル BindingNavigator コンポーネントへのボタン</span><span class="sxs-lookup"><span data-stu-id="2f8c4-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="2f8c4-107">フォームに <xref:System.Windows.Forms.TextBox> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="2f8c4-108">バインドする<xref:System.Windows.Forms.BindingSource>、これが、データ ソースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="2f8c4-109">この例で、<xref:System.Windows.Forms.BindingSource>はデータベースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="2f8c4-110">データセットとテーブルのアダプターが生成されると、ドラッグ、<xref:System.Windows.Forms.BindingNavigator>をフォームにコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="2f8c4-111">設定、<xref:System.Windows.Forms.BindingNavigator>コントロールの<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>プロパティを<xref:System.Windows.Forms.BindingSource>コントロールにバインドされている形式にします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="2f8c4-112"><xref:System.Windows.Forms.BindingNavigator> コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="2f8c4-113">スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) ため、 **BindingNavigator タスク**ダイアログが表示され選択**アイテムの編集**.</span><span class="sxs-lookup"><span data-stu-id="2f8c4-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="2f8c4-114">**Items コレクション エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="2f8c4-115">**Items コレクション エディター**次を完了します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="2f8c4-116">追加、 <xref:System.Windows.Forms.ToolStripSeparator> 3<xref:System.Windows.Forms.ToolStripButton>項目の種類の適切な選択を<xref:System.Windows.Forms.ToolStripItem> をクリックし、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="2f8c4-117">設定、<xref:System.Windows.Forms.ToolStripItem.Name%2A>ボタンのプロパティ**LoadButton**、**SaveButton**、および**CancelButton**、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to**LoadButton**,**SaveButton**, and**CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="2f8c4-118">設定、<xref:System.Windows.Forms.ToolStripItem.Text%2A>ボタンのプロパティ**ロード**`,` **保存**、および**キャンセル**です。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to**Load**`,` **Save**, and**Cancel**.</span></span>  
  
    4.  <span data-ttu-id="2f8c4-119">設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>するボタンの各プロパティ**テキスト**です。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to**Text**.</span></span> <span data-ttu-id="2f8c4-120">このプロパティを設定する代わりに、**イメージ**または**ImageAndText**に表示されるイメージを設定し、<xref:System.Windows.Forms.ToolStripItem.Image%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-120">Alternatively, you can set this property to**Image**or**ImageAndText**and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="2f8c4-121">をクリックして**OK**  ダイアログ ボックスを閉じます。ボタンに追加されて、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="2f8c4-122">フォームを右クリックして選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="2f8c4-123">コード エディターでは、テーブル アダプターにデータを読み込むコードの行を検索します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="2f8c4-124">このコードは、手順 2. でデータ バインディングを設定するときに生成されました。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="2f8c4-125">コードを次のようにする必要があります:`TableAdapterName.Fill(DataSetName.TableName)`です。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="2f8c4-126">ほとんどは、フォームのされる可能性が高い<xref:System.Windows.Forms.Form.Load>イベント。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="2f8c4-127">イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**ロード**<xref:System.Windows.Forms.ToolStripButton>以前に作成し、このデータの読み込みのコードを移動します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Load**<xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="2f8c4-128">コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-128">Your code should now look similar to the following:</span></span>  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. <span data-ttu-id="2f8c4-129">イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**保存**<xref:System.Windows.Forms.ToolStripButton>先ほど作成したし、テーブル コントロール内のデータを更新するコードの記述にバインドします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2f8c4-130">場合によっては、<xref:System.Windows.Forms.BindingNavigator>コンポーネントが既に与えられて、**保存**ボタン、コードではなく、によって生成された Windows フォーム デザイナー。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a**Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="2f8c4-131">上記のコードを配置するこの例では、<xref:System.Windows.Forms.ToolStripItem.Click>に完全に新しいボタンを作成するのではなく、そのボタンのイベント ハンドラー、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="2f8c4-132">ただし、ボタンは既定では無効ため、設定する必要があります、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>するボタンのプロパティ`true`に正しくボタン関数。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>  
  
12. <span data-ttu-id="2f8c4-133">イベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント、**キャンセル**<xref:System.Windows.Forms.ToolStripButton>以前に作成し、表示されるデータのレコードへの変更をキャンセルするコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Cancel**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2f8c4-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>メソッドのスコープは、データの行にします。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="2f8c4-135">次のレコードに移動する前に個々 のレコードの表示中に加えたあらゆる変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="2f8c4-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8c4-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f8c4-136">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="2f8c4-137">BindingNavigator コントロール</span><span class="sxs-lookup"><span data-stu-id="2f8c4-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="2f8c4-138">BindingSource コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="2f8c4-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
