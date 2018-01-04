---
title: "方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7b6f8ff44763c19de1eac6d4be98bca75ff9f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="88e82-102">方法 : デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="88e82-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="88e82-103">すべての Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="88e82-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="88e82-104">ユーザーが ENTER キーを押したときに既定のボタンがクリックされたフォーム上の他のコントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="88e82-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="88e82-105">このコントロールにフォーカスが別のボタン機能には、例外:、フォーカスのあるボタンをクリックする場合は、— 複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロールです。</span><span class="sxs-lookup"><span data-stu-id="88e82-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e82-106">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="88e82-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="88e82-107">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="88e82-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="88e82-108">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e82-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-accept-button"></a><span data-ttu-id="88e82-109">承認ボタンを指定するには</span><span class="sxs-lookup"><span data-stu-id="88e82-109">To designate the accept button</span></span>  
  
1.  <span data-ttu-id="88e82-110">ボタンが置かれているフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="88e82-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="88e82-111">**プロパティ**ウィンドウで、設定、フォームの<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを<xref:System.Windows.Forms.Button>コントロールの名前。</span><span class="sxs-lookup"><span data-stu-id="88e82-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e82-112">参照</span><span class="sxs-lookup"><span data-stu-id="88e82-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [<span data-ttu-id="88e82-113">Button コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="88e82-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="88e82-114">Windows フォームの Button コントロールを選択する方法</span><span class="sxs-lookup"><span data-stu-id="88e82-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="88e82-115">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="88e82-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="88e82-116">方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="88e82-116">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="88e82-117">Button コントロール</span><span class="sxs-lookup"><span data-stu-id="88e82-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
