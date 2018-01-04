---
title: "PasswordBox のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22b73704d21fa719a678799c1d95fc266c661e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="28178-102">PasswordBox のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="28178-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="28178-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="28178-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="28178-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="28178-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="28178-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28178-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="28178-106">PasswordBox 部分</span><span class="sxs-lookup"><span data-stu-id="28178-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="28178-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="28178-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="28178-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="28178-108">Part</span></span>|<span data-ttu-id="28178-109">型</span><span class="sxs-lookup"><span data-stu-id="28178-109">Type</span></span>|<span data-ttu-id="28178-110">説明</span><span class="sxs-lookup"><span data-stu-id="28178-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="28178-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="28178-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="28178-112">視覚的要素を含むことができます、<xref:System.Windows.FrameworkElement>です。</span><span class="sxs-lookup"><span data-stu-id="28178-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="28178-113">テキスト、<xref:System.Windows.Controls.PasswordBox>はこの要素に表示されます。</span><span class="sxs-lookup"><span data-stu-id="28178-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="28178-114">PasswordBox 状態</span><span class="sxs-lookup"><span data-stu-id="28178-114">PasswordBox States</span></span>  
 <span data-ttu-id="28178-115">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="28178-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="28178-116">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="28178-116">VisualState Name</span></span>|<span data-ttu-id="28178-117">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="28178-117">VisualStateGroup Name</span></span>|<span data-ttu-id="28178-118">説明</span><span class="sxs-lookup"><span data-stu-id="28178-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="28178-119">標準</span><span class="sxs-lookup"><span data-stu-id="28178-119">Normal</span></span>|<span data-ttu-id="28178-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="28178-120">CommonStates</span></span>|<span data-ttu-id="28178-121">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="28178-121">The default state.</span></span>|  
|<span data-ttu-id="28178-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="28178-122">MouseOver</span></span>|<span data-ttu-id="28178-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="28178-123">CommonStates</span></span>|<span data-ttu-id="28178-124">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="28178-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="28178-125">無効</span><span class="sxs-lookup"><span data-stu-id="28178-125">Disabled</span></span>|<span data-ttu-id="28178-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="28178-126">CommonStates</span></span>|<span data-ttu-id="28178-127">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="28178-127">The control is disabled.</span></span>|  
|<span data-ttu-id="28178-128">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="28178-128">Focused</span></span>|<span data-ttu-id="28178-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="28178-129">FocusStates</span></span>|<span data-ttu-id="28178-130">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="28178-130">The control has focus.</span></span>|  
|<span data-ttu-id="28178-131">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="28178-131">Unfocused</span></span>|<span data-ttu-id="28178-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="28178-132">FocusStates</span></span>|<span data-ttu-id="28178-133">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="28178-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="28178-134">有効</span><span class="sxs-lookup"><span data-stu-id="28178-134">Valid</span></span>|<span data-ttu-id="28178-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="28178-135">ValidationStates</span></span>|<span data-ttu-id="28178-136">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="28178-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="28178-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="28178-137">InvalidFocused</span></span>|<span data-ttu-id="28178-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="28178-138">ValidationStates</span></span>|<span data-ttu-id="28178-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="28178-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="28178-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="28178-140">InvalidUnfocused</span></span>|<span data-ttu-id="28178-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="28178-141">ValidationStates</span></span>|<span data-ttu-id="28178-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="28178-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="28178-143">PasswordBox ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="28178-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="28178-144">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="28178-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="28178-145">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="28178-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="28178-146">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28178-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28178-147">参照</span><span class="sxs-lookup"><span data-stu-id="28178-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="28178-148">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="28178-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="28178-149">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="28178-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="28178-150">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="28178-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="28178-151">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="28178-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
