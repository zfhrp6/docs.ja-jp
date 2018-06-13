---
title: '方法 : Windows フォームの Button コントロールを承認ボタンとして指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: a69964b83e9948a844483725616a150234a38c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531941"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a><span data-ttu-id="63f9f-102">方法 : Windows フォームの Button コントロールを承認ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="63f9f-102">How to: Designate a Windows Forms Button as the Accept Button</span></span>
<span data-ttu-id="63f9f-103">すべての Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="63f9f-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="63f9f-104">ユーザーが ENTER キーを押したときに既定のボタンがクリックされたフォーム上の他のコントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="63f9f-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63f9f-105">このコントロールにフォーカスが別のボタン機能には、例外:、フォーカスのあるボタンをクリックする場合は、— 複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロールです。</span><span class="sxs-lookup"><span data-stu-id="63f9f-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="63f9f-106">承認ボタンを指定するには</span><span class="sxs-lookup"><span data-stu-id="63f9f-106">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="63f9f-107">フォームの設定<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="63f9f-107">Set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the appropriate <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="63f9f-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="63f9f-108">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="63f9f-109">Button コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="63f9f-109">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="63f9f-110">Windows フォームの Button コントロールを選択する方法</span><span class="sxs-lookup"><span data-stu-id="63f9f-110">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="63f9f-111">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="63f9f-111">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="63f9f-112">方法: Windows フォームの Button コントロールをキャンセル ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="63f9f-112">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [<span data-ttu-id="63f9f-113">Button コントロール</span><span class="sxs-lookup"><span data-stu-id="63f9f-113">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
