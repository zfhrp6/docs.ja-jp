---
title: "Button コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="73537-102">Button コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="73537-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="73537-103">Windows フォームの <xref:System.Windows.Forms.Button> コントロールを使用すると、ユーザーはそれをクリックしてアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="73537-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="73537-104">ボタンをクリックすると、ボタンを実際に押して離したかのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="73537-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="73537-105">ユーザーがクリックされるたびに、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="73537-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="73537-106">内のコードを配置する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを選択したアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="73537-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="73537-107">ボタンに表示されるテキストが含まれている、<xref:System.Windows.Forms.Control.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="73537-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="73537-108">テキストは、ボタンの幅を超えている場合は、次の行に折り返されます。</span><span class="sxs-lookup"><span data-stu-id="73537-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="73537-109">ただし、コントロールが全体の高さに対応できない場合、クリップされます。</span><span class="sxs-lookup"><span data-stu-id="73537-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="73537-110">詳細については、次を参照してください。[する方法: Windows フォーム コントロールによって表示されるテキストを設定](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="73537-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="73537-111"><xref:System.Windows.Forms.Control.Text%2A>プロパティは、これにより、ユーザーはアクセス キー、ALT キーを押すとコントロールを「クリックして」をアクセス キーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="73537-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="73537-112">詳細については、「[する方法: Windows のフォーム コントロールへのアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="73537-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="73537-113">によって、テキストの外観を制御、<xref:System.Windows.Forms.Control.Font%2A>プロパティおよび<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="73537-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="73537-114"><xref:System.Windows.Forms.Button>コントロールできますを使用してイメージを表示しても、<xref:System.Windows.Forms.ButtonBase.Image%2A>と<xref:System.Windows.Forms.ButtonBase.ImageList%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="73537-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="73537-115">詳細については、次を参照してください。[する方法: Windows フォーム コントロールによってイメージの表示設定](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="73537-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73537-116">参照</span><span class="sxs-lookup"><span data-stu-id="73537-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="73537-117">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="73537-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="73537-118">Windows フォームの Button コントロールを選択する方法</span><span class="sxs-lookup"><span data-stu-id="73537-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="73537-119">方法: デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="73537-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="73537-120">方法: デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="73537-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="73537-121">Button コントロール</span><span class="sxs-lookup"><span data-stu-id="73537-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
