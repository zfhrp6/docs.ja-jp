---
title: "方法 : Windows フォームにコントロールを固定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceaacc250d48e7199d7224f95aa91ed976c097e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="a0ecf-102">方法 : Windows フォームにコントロールを固定する</span><span class="sxs-lookup"><span data-stu-id="a0ecf-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="a0ecf-103">実行時にサイズを変更できるユーザーをフォームをデザインする場合、フォーム上のコントロールがサイズし、位置を正しくです。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="a0ecf-104">使用することができますが、フォームを動的にコントロールのサイズを変更するには、 <xref:System.Windows.Forms.Control.Anchor%2A> Windows フォーム コントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="a0ecf-105"><xref:System.Windows.Forms.Control.Anchor%2A>プロパティがコントロールの固定位置を定義します。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="a0ecf-106">フォームにコントロールを固定すると、フォームのサイズが、コントロールは、コントロールと、アンカー位置の間の距離を保持します。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="a0ecf-107">ある場合など、<xref:System.Windows.Forms.TextBox>フォームのサイズを変更、左、右、およびフォームの下端が固定されるコントロール、<xref:System.Windows.Forms.TextBox>フォームの横の右側と左側からの距離が維持されるため、水平方向にサイズ変更を制御します。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="a0ecf-108">さらに、コントロール配置自体垂直方向にその場所は、フォームの下部エッジからの距離では常にできるようにします。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="a0ecf-109">コントロールが固定されていないと、フォームのサイズが、フォームの端を基準としたコントロールの位置が変更されました。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="a0ecf-110"><xref:System.Windows.Forms.Control.Anchor%2A>プロパティの対話、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="a0ecf-111">詳細については、次を参照してください。 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0ecf-112">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a0ecf-113">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a0ecf-114">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="a0ecf-115">フォーム上のコントロールを固定するには</span><span class="sxs-lookup"><span data-stu-id="a0ecf-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="a0ecf-116">固定するコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0ecf-117">CTRL キーを押し、して選択し、各コントロールをクリックし、この手順の残りの部分で同時に複数のコントロールを固定できます。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="a0ecf-118">**プロパティ** ウィンドウの右側の矢印をクリックして、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="a0ecf-119">クロス エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="a0ecf-120">アンカーを設定するには、左上、右、またはクロスの下部のセクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="a0ecf-121">コントロール、ページのトップへと左に固定既定です。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="a0ecf-122">固定されているコントロールの辺をクリアするには、その arm クロスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="a0ecf-123">閉じるには、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ エディターをクリックして、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ名をもう一度です。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="a0ecf-124">実行時に、フォームが表示されたら、フォームの端からの距離を保持するコントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="a0ecf-125">アンカーのエッジからの距離。 常に同じ距離は、Windows フォーム デザイナーでコントロールが配置されているときに定義されています。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0ecf-126">などの特定のコントロール、<xref:System.Windows.Forms.ComboBox>の高さに制限されている、制御します。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="a0ecf-127">フォームまたはコンテナーの最下位にコントロールを固定強制的にコントロールを制限された高さを高くことはできません。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="a0ecf-128">継承されたコントロールがある必要があります`Protected`固定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="a0ecf-129">コントロールのアクセス レベルを変更するには、次のように設定します。 その`Modifiers`プロパティに、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="a0ecf-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ecf-130">参照</span><span class="sxs-lookup"><span data-stu-id="a0ecf-130">See Also</span></span>  
 [<span data-ttu-id="a0ecf-131">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="a0ecf-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a0ecf-132">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a0ecf-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a0ecf-133">AutoSize プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="a0ecf-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="a0ecf-134">方法: Windows フォーム上のコントロールをドッキングする</span><span class="sxs-lookup"><span data-stu-id="a0ecf-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="a0ecf-135">チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a0ecf-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="a0ecf-136">チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="a0ecf-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="a0ecf-137">チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト</span><span class="sxs-lookup"><span data-stu-id="a0ecf-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
