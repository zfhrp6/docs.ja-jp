---
title: "方法 : Windows フォームにコントロールを追加する"
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
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9075c93181b68828a307924259a9170c046baa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="1712d-102">方法 : Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="1712d-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="1712d-103">ほとんどのフォームは、フォームのサーフェイスにコントロールを追加してユーザー インターフェイス (UI) を定義するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="1712d-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="1712d-104">A*コントロール*情報の表示や、ユーザー入力をそのまま使用するために使用するフォームのコンポーネントは、します。</span><span class="sxs-lookup"><span data-stu-id="1712d-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="1712d-105">コントロールの詳細については、次を参照してください。 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="1712d-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1712d-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1712d-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1712d-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1712d-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1712d-108">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1712d-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="1712d-109">フォーム上のコントロールを描画するには</span><span class="sxs-lookup"><span data-stu-id="1712d-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="1712d-110">フォームを開きます。</span><span class="sxs-lookup"><span data-stu-id="1712d-110">Open the form.</span></span> <span data-ttu-id="1712d-111">詳細については、次を参照してください。[する方法: デザイナーでの Windows フォームの表示](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)です。</span><span class="sxs-lookup"><span data-stu-id="1712d-111">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="1712d-112">**ツールボックス**フォームに追加するコントロールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1712d-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="1712d-113">フォームに存在するコントロールの左上隅をクリックしを配置するコントロールの右下隅の任意の場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1712d-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="1712d-114">コントロールは、指定した位置とサイズでフォームに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1712d-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1712d-115">各コントロールには、定義されている既定のサイズがあります。</span><span class="sxs-lookup"><span data-stu-id="1712d-115">Each control has a default size defined.</span></span> <span data-ttu-id="1712d-116">ドラッグして、コントロールの既定のサイズで、フォームにコントロールを追加することができます、**ツールボックス**をフォームにします。</span><span class="sxs-lookup"><span data-stu-id="1712d-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="1712d-117">コントロールをフォームにドラッグするには</span><span class="sxs-lookup"><span data-stu-id="1712d-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="1712d-118">フォームを開きます。</span><span class="sxs-lookup"><span data-stu-id="1712d-118">Open the form.</span></span> <span data-ttu-id="1712d-119">詳細については、次を参照してください。[する方法: デザイナーでの Windows フォームの表示](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)です。</span><span class="sxs-lookup"><span data-stu-id="1712d-119">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="1712d-120">**ツールボックス**フォームにドラッグしてコントロールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1712d-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="1712d-121">コントロールは、既定のサイズで指定した場所にあるフォームに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1712d-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1712d-122">内のコントロールをダブルクリックすることができます、**ツールボックス**を既定のサイズで、フォームの左上隅に追加します。</span><span class="sxs-lookup"><span data-stu-id="1712d-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="1712d-123">実行時に、フォームにコントロールを動的に追加することができますも。</span><span class="sxs-lookup"><span data-stu-id="1712d-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="1712d-124">次のコード例で、<xref:System.Windows.Forms.TextBox>コントロールは、フォームに追加するときに、<xref:System.Windows.Forms.Button>コントロールがクリックされました。</span><span class="sxs-lookup"><span data-stu-id="1712d-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1712d-125">次の手順が必要ですがあるフォーム、**ボタン**コントロール、`Button1`に既に配置されている、します。</span><span class="sxs-lookup"><span data-stu-id="1712d-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="1712d-126">プログラムによってコントロールをフォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="1712d-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="1712d-127">ボタンの処理をメソッドで`Click`フォームのクラスを制御変数への参照を追加するには、次のような挿入コード内のイベント設定コントロールの`Location`、し、コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="1712d-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1712d-128">コントロールの他のプロパティを初期化するコードを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="1712d-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1712d-129">悪意のあるを参照して、ローカル コンピューターがネットワーク経由のセキュリティ リスクを公開する可能性があります`UserControl`です。</span><span class="sxs-lookup"><span data-stu-id="1712d-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="1712d-130">誤ってそれをプロジェクトに追加した後に、有害なカスタム コントロールを作成する悪意のあるユーザーの場合は問題にならなければのみとなります。</span><span class="sxs-lookup"><span data-stu-id="1712d-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1712d-131">参照</span><span class="sxs-lookup"><span data-stu-id="1712d-131">See Also</span></span>  
 [<span data-ttu-id="1712d-132">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="1712d-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="1712d-133">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="1712d-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="1712d-134">方法: Windows フォーム上のコントロールのサイズを変更する</span><span class="sxs-lookup"><span data-stu-id="1712d-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="1712d-135">方法: Windows フォーム コントロールによって表示されるテキストを設定する</span><span class="sxs-lookup"><span data-stu-id="1712d-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="1712d-136">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="1712d-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
