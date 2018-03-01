---
title: "Windows フォームの Button コントロールを選択する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0b6fa31b89b8fbe50077933cf04aa3c17db86438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="87009-102">Windows フォームの Button コントロールを選択する方法</span><span class="sxs-lookup"><span data-stu-id="87009-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="87009-103">Windows フォームのボタンは、次のように選択できます。</span><span class="sxs-lookup"><span data-stu-id="87009-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
-   <span data-ttu-id="87009-104">マウスを使用して、ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="87009-104">Use a mouse to click the button.</span></span>  
  
-   <span data-ttu-id="87009-105">呼び出し、ボタンの<xref:System.Windows.Forms.Control.Click>コード内のイベントです。</span><span class="sxs-lookup"><span data-stu-id="87009-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
-   <span data-ttu-id="87009-106">TAB キーを押して、ボタンにフォーカスを移動し、ボタンを選択し、space キーまたは ENTER キーを押して、します。</span><span class="sxs-lookup"><span data-stu-id="87009-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
-   <span data-ttu-id="87009-107">ボタンの (ALT + 下線付き文字) のアクセス キーを押します。</span><span class="sxs-lookup"><span data-stu-id="87009-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="87009-108">アクセス キーの詳細については、次を参照してください。[する方法: Windows のフォーム コントロールへのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="87009-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
-   <span data-ttu-id="87009-109">ボタンがフォームの「承認」ボタンの場合は、ENTER キーを押してボタンを選択、他のコントロールにフォーカスがある場合でも、その他のコントロールが別のボタン、複数行テキスト ボックス、または enter キーをトラップするカスタム コントロールの場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="87009-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
-   <span data-ttu-id="87009-110">別のコントロールにフォーカスがある場合でも、esc キーを押して、ボタンがフォームの「キャンセル」ボタンの場合に、ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="87009-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
-   <span data-ttu-id="87009-111">呼び出す、<xref:System.Windows.Forms.Button.PerformClick%2A>メソッドをプログラムで、ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="87009-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87009-112">参照</span><span class="sxs-lookup"><span data-stu-id="87009-112">See Also</span></span>  
 [<span data-ttu-id="87009-113">Button コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="87009-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="87009-114">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="87009-114">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="87009-115">Button コントロール</span><span class="sxs-lookup"><span data-stu-id="87009-115">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
