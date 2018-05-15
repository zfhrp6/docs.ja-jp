---
title: '方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: aade1b6e988fc4b43f7ad9cfb58382302c875d37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="99ba5-102">方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="99ba5-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="99ba5-103">すべての Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="99ba5-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="99ba5-104">ユーザーが ENTER キーを押したときに既定のボタンがクリックされたフォーム上の他のコントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="99ba5-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="99ba5-105">このコントロールにフォーカスが別のボタン機能には、例外:、フォーカスのあるボタンをクリックする場合は、— 複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロールです。</span><span class="sxs-lookup"><span data-stu-id="99ba5-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99ba5-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="99ba5-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="99ba5-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99ba5-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="99ba5-108">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99ba5-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="99ba5-109">承認ボタンを指定するには</span><span class="sxs-lookup"><span data-stu-id="99ba5-109">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="99ba5-110">ボタンが置かれているフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="99ba5-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="99ba5-111">**プロパティ**ウィンドウで、設定、フォームの<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを<xref:System.Windows.Forms.Button>コントロールの名前。</span><span class="sxs-lookup"><span data-stu-id="99ba5-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ba5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="99ba5-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="99ba5-113">Button コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="99ba5-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="99ba5-114">Windows フォームの Button コントロールを選択する方法</span><span class="sxs-lookup"><span data-stu-id="99ba5-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="99ba5-115">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="99ba5-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="99ba5-116">方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="99ba5-116">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="99ba5-117">Button コントロール</span><span class="sxs-lookup"><span data-stu-id="99ba5-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
