---
title: "方法 : Windows フォーム上のタブ オーダーを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7acca633a5a2b98d7c4b6dd64355996e763d6df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a><span data-ttu-id="5fa1e-102">方法 : Windows フォーム上のタブ オーダーを設定する</span><span class="sxs-lookup"><span data-stu-id="5fa1e-102">How to: Set the Tab Order on Windows Forms</span></span>
<span data-ttu-id="5fa1e-103">タブ オーダーでは、ユーザーが TAB キーを押して 1 つのコントロールからでフォーカスを移動する順序です。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-103">The tab order is the order in which a user moves focus from one control to another by pressing the TAB key.</span></span> <span data-ttu-id="5fa1e-104">各フォームには、独自のタブ オーダーがあります。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-104">Each form has its own tab order.</span></span> <span data-ttu-id="5fa1e-105">既定では、タブ オーダーは、コントロールを作成した順序と同じです。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-105">By default, the tab order is the same as the order in which you created the controls.</span></span> <span data-ttu-id="5fa1e-106">タブ オーダーの番号は 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-106">Tab-order numbering begins with zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fa1e-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5fa1e-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5fa1e-109">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-tab-order-of-a-control"></a><span data-ttu-id="5fa1e-110">コントロールのタブ オーダーを設定するには</span><span class="sxs-lookup"><span data-stu-id="5fa1e-110">To set the tab order of a control</span></span>  
  
1.  <span data-ttu-id="5fa1e-111">**ビュー**  メニューのをクリックして**タブ オーダー**です。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-111">On the **View** menu, click **Tab Order**.</span></span>  
  
     <span data-ttu-id="5fa1e-112">これには、フォーム上のタブ オーダー選択モードがアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-112">This activates the tab-order selection mode on the form.</span></span> <span data-ttu-id="5fa1e-113">数値 (を表す、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティ) の各コントロールの左上隅に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-113">A number (representing the <xref:System.Windows.Forms.Control.TabIndex%2A> property) appears in the upper-left corner of each control.</span></span>  
  
2.  <span data-ttu-id="5fa1e-114">タブの順序を確立するために順番にコントロールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-114">Click the controls sequentially to establish the tab order you want.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5fa1e-115">タブ オーダーのコントロールの位置は、0 以上、任意の値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-115">A control's place within the tab order can be set to any value greater than or equal to 0.</span></span> <span data-ttu-id="5fa1e-116">重複が発生すると、2 つのコントロールの z オーダーが評価され、上位のコントロールが最初にタブ付き。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-116">When duplicates occur, the z-order of the two controls is evaluated and the control on top is tabbed to first.</span></span> <span data-ttu-id="5fa1e-117">(Z オーダーは、フォームの z 軸 [奥行] に沿ってフォーム上のコントロールのビジュアルの重ね順です。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-117">(The z-order is the visual layering of controls on a form along the form's z-axis [depth].</span></span> <span data-ttu-id="5fa1e-118">Z オーダーを決定するコントロールは、その他のコントロールの前にします。)Z オーダーの詳細については、次を参照してください。 [Windows フォームでのオブジェクトの階層構造](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-118">The z-order determines which controls are in front of other controls.) For more information on z-order, see [Layering Objects on Windows Forms](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="5fa1e-119">完了したら、をクリックして**タブ オーダー**上、**ビュー**タブ オーダー モードを終了するには、もう一度メニュー。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-119">When you have finished, click **Tab Order** on the **View** menu again to leave tab order mode.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5fa1e-120">フォーカスを取得できません。 コントロールだけでなく、無効になっており、非表示のコントロールがない、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティであり、タブ オーダーに含まれません。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-120">Controls that cannot get the focus, as well as disabled and invisible controls, do not have a <xref:System.Windows.Forms.Control.TabIndex%2A> property and are not included in the tab order.</span></span> <span data-ttu-id="5fa1e-121">ユーザーは、TAB キーを押すと、これらのコントロールはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-121">As a user presses the TAB key, these controls are skipped.</span></span>  
  
 <span data-ttu-id="5fa1e-122">プロパティ ウィンドウを使用して、タブ オーダーを設定する代わりに、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-122">Alternatively, tab order can be set in the Properties window using the <xref:System.Windows.Forms.Control.TabIndex%2A> property.</span></span> <span data-ttu-id="5fa1e-123"><xref:System.Windows.Forms.Control.TabIndex%2A>  タブの順序で配置されているコントロールのプロパティを決定します。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-123">The <xref:System.Windows.Forms.Control.TabIndex%2A> property of a control determines where it is positioned in the tab order.</span></span> <span data-ttu-id="5fa1e-124">既定では、最初のコントロールの描画が、<xref:System.Windows.Forms.Control.TabIndex%2A>値 0、2 番目は、 <xref:System.Windows.Forms.Control.TabIndex%2A> 1 というようです。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-124">By default, the first control drawn has a <xref:System.Windows.Forms.Control.TabIndex%2A> value of 0, the second has a <xref:System.Windows.Forms.Control.TabIndex%2A> of 1, and so on.</span></span>  
  
 <span data-ttu-id="5fa1e-125">さらに、既定では、<xref:System.Windows.Forms.GroupBox>コントロールが持つ独自<xref:System.Windows.Forms.Control.TabIndex%2A>られている整数値。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-125">Additionally, by default, a <xref:System.Windows.Forms.GroupBox> control has its own <xref:System.Windows.Forms.Control.TabIndex%2A> value, which is a whole number.</span></span> <span data-ttu-id="5fa1e-126">A<xref:System.Windows.Forms.GroupBox>コントロール自体は、実行時にフォーカスを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-126">A <xref:System.Windows.Forms.GroupBox> control itself cannot have focus at run time.</span></span> <span data-ttu-id="5fa1e-127">したがって、各コントロール、<xref:System.Windows.Forms.GroupBox>独自の 10 進数を持つ<xref:System.Windows.Forms.Control.TabIndex%2A>.0 で始まる値。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-127">Thus, each control within a <xref:System.Windows.Forms.GroupBox> has its own decimal <xref:System.Windows.Forms.Control.TabIndex%2A> value, beginning with .0.</span></span> <span data-ttu-id="5fa1e-128">当然ながら、として、<xref:System.Windows.Forms.Control.TabIndex%2A>の<xref:System.Windows.Forms.GroupBox>コントロールがインクリメントされます、内のコントロールが増加します。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-128">Naturally, as the <xref:System.Windows.Forms.Control.TabIndex%2A> of a <xref:System.Windows.Forms.GroupBox> control is incremented, the controls within it will be incremented accordingly.</span></span> <span data-ttu-id="5fa1e-129">変更した場合、 <xref:System.Windows.Forms.Control.TabIndex%2A> 5、6 ~ 値、 <xref:System.Windows.Forms.Control.TabIndex%2A> 6.0 というように、グループの最初のコントロールの値が自動的に変更します。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-129">If you changed a <xref:System.Windows.Forms.Control.TabIndex%2A> value from 5 to 6, the <xref:System.Windows.Forms.Control.TabIndex%2A> value of the first control in its group automatically changes to 6.0, and so on.</span></span>  
  
 <span data-ttu-id="5fa1e-130">最後に、フォームのさまざまの任意のコントロールは、タブ オーダーでスキップできます。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-130">Finally, any control of the many on your form can be skipped in the tab order.</span></span> <span data-ttu-id="5fa1e-131">通常は、TAB キーを押して連続して実行時の選択、タブ オーダー内の各コントロールです。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-131">Usually, pressing TAB successively at run time selects each control in the tab order.</span></span> <span data-ttu-id="5fa1e-132">無効にして、<xref:System.Windows.Forms.Control.TabStop%2A>プロパティ、行うことができます、フォームのタブ オーダーで経由で渡されるコントロール。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-132">By turning off the <xref:System.Windows.Forms.Control.TabStop%2A> property, you can make a control be passed over in the tab order of the form.</span></span>  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a><span data-ttu-id="5fa1e-133">タブ オーダーのコントロールを削除するには</span><span class="sxs-lookup"><span data-stu-id="5fa1e-133">To remove a control from the tab order</span></span>  
  
1.  <span data-ttu-id="5fa1e-134">コントロールの設定<xref:System.Windows.Forms.Control.TabStop%2A>プロパティを`false`プロパティ ウィンドウでします。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-134">Set the control's <xref:System.Windows.Forms.Control.TabStop%2A> property to `false` in the Properties window.</span></span>  
  
     <span data-ttu-id="5fa1e-135">いる A コントロール<xref:System.Windows.Forms.Control.TabStop%2A>プロパティに設定された`false`TAB キーでコントロールを循環するときに、コントロールがスキップされた場合でも、タブ オーダー内での位置を維持できます。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-135">A control whose <xref:System.Windows.Forms.Control.TabStop%2A> property has been set to `false` still maintains its position in the tab order, even though the control is skipped when you cycle through the controls with the TAB key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5fa1e-136">ラジオ ボタン グループでは、実行時に停止する 1 つのタブがします。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-136">A radio button group has a single tab stop at run time.</span></span> <span data-ttu-id="5fa1e-137">選択したボタン (ボタンは、その<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティに設定`true`) がその<xref:System.Windows.Forms.Control.TabStop%2A>プロパティが自動的に設定`true`れ、他のボタン、<xref:System.Windows.Forms.Control.TabStop%2A>プロパティに設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-137">The selected button (that is, the button with its <xref:System.Windows.Forms.RadioButton.Checked%2A> property set to `true`) has its <xref:System.Windows.Forms.Control.TabStop%2A> property automatically set to `true`, while the other buttons have their <xref:System.Windows.Forms.Control.TabStop%2A> property set to `false`.</span></span> <span data-ttu-id="5fa1e-138">グループ化の詳細については<xref:System.Windows.Forms.RadioButton>コントロールを参照してください[セットとして機能する Windows フォーム RadioButton コントロールをグループ化](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fa1e-138">For more information about grouping <xref:System.Windows.Forms.RadioButton> controls, see [Grouping Windows Forms RadioButton Controls to Function as a Set](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa1e-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fa1e-139">See Also</span></span>  
 [<span data-ttu-id="5fa1e-140">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="5fa1e-140">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="5fa1e-141">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="5fa1e-141">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="5fa1e-142">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="5fa1e-142">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="5fa1e-143">Windows フォーム コントロールの機能別一覧</span><span class="sxs-lookup"><span data-stu-id="5fa1e-143">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
