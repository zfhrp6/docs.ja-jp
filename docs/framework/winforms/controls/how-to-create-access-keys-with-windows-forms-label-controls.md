---
title: "方法 : Windows フォームの Label コントロールでアクセス キーを作成する"
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
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ad6cd99a6399adea2e69cbf844b9f134d2e592e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="de2e8-102">方法 : Windows フォームの Label コントロールでアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="de2e8-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="de2e8-103">Windows フォーム<xref:System.Windows.Forms.Label>を他のコントロールのアクセス キーを定義するコントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="de2e8-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="de2e8-104">ラベル コントロールにアクセス キーを定義するときに、ユーザーは ALT キーとそれに続くタブ オーダーでコントロールにフォーカスを移動するように指定した文字キーを押すことができます。</span><span class="sxs-lookup"><span data-stu-id="de2e8-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="de2e8-105">ラベルは、フォーカスを受け取ることはできません、ため、タブ オーダーの次のコントロールにフォーカスが自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="de2e8-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="de2e8-106">この手法を使用して、テキスト ボックス、コンボ ボックス、リスト ボックス、およびデータ グリッドにアクセス キーを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de2e8-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="de2e8-107">ラベルを持つコントロールにアクセス キーを割り当てる</span><span class="sxs-lookup"><span data-stu-id="de2e8-107">To assign an access key to a control with a label</span></span>  
  
1.  <span data-ttu-id="de2e8-108">最初に、ラベルを描画し、その他のコントロールを描画します。</span><span class="sxs-lookup"><span data-stu-id="de2e8-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="de2e8-109">または</span><span class="sxs-lookup"><span data-stu-id="de2e8-109">-or-</span></span>  
  
     <span data-ttu-id="de2e8-110">任意の順序で、コントロールを描画し、設定、<xref:System.Windows.Forms.Control.TabIndex%2A>他のコントロールより 1 小さい値をラベルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="de2e8-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2.  <span data-ttu-id="de2e8-111">ラベルの設定<xref:System.Windows.Forms.Label.UseMnemonic%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="de2e8-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="de2e8-112">アンパサンドを使用して、ラベルのでは、(&)<xref:System.Windows.Forms.Label.Text%2A>ラベルのアクセス キーを割り当てるプロパティをします。</span><span class="sxs-lookup"><span data-stu-id="de2e8-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="de2e8-113">詳細については、次を参照してください。[アクセス キーの Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="de2e8-113">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de2e8-114">アクセス キーの作成に使用するのではなく、ラベル コントロールにアンパサンドを表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="de2e8-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="de2e8-115">これは、アンパサンドがデータに含まれるレコード セット内のフィールドに、ラベル コントロールをバインドする場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="de2e8-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="de2e8-116">ラベル コントロールでは、アンパサンドを表示するには、設定、<xref:System.Windows.Forms.Label.UseMnemonic%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="de2e8-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="de2e8-117">アンパサンドを表示しても、アクセス キーを持っている場合は、設定、<xref:System.Windows.Forms.Label.UseMnemonic%2A>プロパティを`true`を示し、1 つのアンパサンドとアクセス キー (&)、アンパサンドは、2 つのアンパサンドで表示します。</span><span class="sxs-lookup"><span data-stu-id="de2e8-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="de2e8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="de2e8-118">See Also</span></span>  
 [<span data-ttu-id="de2e8-119">方法: Windows フォーム Label コントロールのサイズを内容に合わせて変更する</span><span class="sxs-lookup"><span data-stu-id="de2e8-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="de2e8-120">Label コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="de2e8-120">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="de2e8-121">Label コントロール</span><span class="sxs-lookup"><span data-stu-id="de2e8-121">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
