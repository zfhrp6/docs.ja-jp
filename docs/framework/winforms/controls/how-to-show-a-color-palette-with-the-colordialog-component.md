---
title: "方法 : ColorDialog コンポーネントを使用してカラー パレットを表示する"
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
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af773141039d049e010742f339ec4f9363d73cc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="7b92c-102">方法 : ColorDialog コンポーネントを使用してカラー パレットを表示する</span><span class="sxs-lookup"><span data-stu-id="7b92c-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="7b92c-103">[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)コンポーネント色のパレットを表示し、ユーザーが選択した色を含むプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="7b92c-103">The [ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="7b92c-104">ColorDialog コンポーネントを使用する色を選択するには</span><span class="sxs-lookup"><span data-stu-id="7b92c-104">To choose a color using the ColorDialog component</span></span>  
  
1.  <span data-ttu-id="7b92c-105">ダイアログ ボックスを使用して、表示、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7b92c-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2.  <span data-ttu-id="7b92c-106">使用して、<xref:System.Windows.Forms.DialogResult>プロパティ ダイアログ ボックスの終了方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="7b92c-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3.  <span data-ttu-id="7b92c-107">使用して、<xref:System.Windows.Forms.ColorDialog.Color%2A>のプロパティ、<xref:System.Windows.Forms.ColorDialog>選択した色を設定するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="7b92c-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="7b92c-108">次の例で、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが表示されます、<xref:System.Windows.Forms.ColorDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="7b92c-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="7b92c-109">ときに、色を選択し、ユーザーが**OK**、<xref:System.Windows.Forms.Button>コントロールの背景色が、選択した色に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7b92c-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="7b92c-110">この例では、フォームには、<xref:System.Windows.Forms.Button>コントロールと<xref:System.Windows.Forms.ColorDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="7b92c-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     <span data-ttu-id="7b92c-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="7b92c-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7b92c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b92c-112">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="7b92c-113">ColorDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7b92c-113">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
