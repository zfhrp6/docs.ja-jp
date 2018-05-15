---
title: PasswordBox のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: a5002aa9596eb45ad92ef67ebc599efac32e94b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="8309c-102">PasswordBox のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8309c-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="8309c-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8309c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="8309c-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="8309c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8309c-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8309c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="8309c-106">PasswordBox 部分</span><span class="sxs-lookup"><span data-stu-id="8309c-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="8309c-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8309c-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="8309c-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="8309c-108">Part</span></span>|<span data-ttu-id="8309c-109">型</span><span class="sxs-lookup"><span data-stu-id="8309c-109">Type</span></span>|<span data-ttu-id="8309c-110">説明</span><span class="sxs-lookup"><span data-stu-id="8309c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8309c-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="8309c-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="8309c-112">視覚的要素を含むことができます、<xref:System.Windows.FrameworkElement>です。</span><span class="sxs-lookup"><span data-stu-id="8309c-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="8309c-113">テキスト、<xref:System.Windows.Controls.PasswordBox>はこの要素に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8309c-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="8309c-114">PasswordBox 状態</span><span class="sxs-lookup"><span data-stu-id="8309c-114">PasswordBox States</span></span>  
 <span data-ttu-id="8309c-115">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8309c-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="8309c-116">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="8309c-116">VisualState Name</span></span>|<span data-ttu-id="8309c-117">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="8309c-117">VisualStateGroup Name</span></span>|<span data-ttu-id="8309c-118">説明</span><span class="sxs-lookup"><span data-stu-id="8309c-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8309c-119">標準</span><span class="sxs-lookup"><span data-stu-id="8309c-119">Normal</span></span>|<span data-ttu-id="8309c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8309c-120">CommonStates</span></span>|<span data-ttu-id="8309c-121">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="8309c-121">The default state.</span></span>|  
|<span data-ttu-id="8309c-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="8309c-122">MouseOver</span></span>|<span data-ttu-id="8309c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8309c-123">CommonStates</span></span>|<span data-ttu-id="8309c-124">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="8309c-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="8309c-125">無効</span><span class="sxs-lookup"><span data-stu-id="8309c-125">Disabled</span></span>|<span data-ttu-id="8309c-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8309c-126">CommonStates</span></span>|<span data-ttu-id="8309c-127">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="8309c-127">The control is disabled.</span></span>|  
|<span data-ttu-id="8309c-128">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="8309c-128">Focused</span></span>|<span data-ttu-id="8309c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8309c-129">FocusStates</span></span>|<span data-ttu-id="8309c-130">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="8309c-130">The control has focus.</span></span>|  
|<span data-ttu-id="8309c-131">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="8309c-131">Unfocused</span></span>|<span data-ttu-id="8309c-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8309c-132">FocusStates</span></span>|<span data-ttu-id="8309c-133">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="8309c-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="8309c-134">有効</span><span class="sxs-lookup"><span data-stu-id="8309c-134">Valid</span></span>|<span data-ttu-id="8309c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8309c-135">ValidationStates</span></span>|<span data-ttu-id="8309c-136">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="8309c-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8309c-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8309c-137">InvalidFocused</span></span>|<span data-ttu-id="8309c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8309c-138">ValidationStates</span></span>|<span data-ttu-id="8309c-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="8309c-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8309c-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8309c-140">InvalidUnfocused</span></span>|<span data-ttu-id="8309c-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8309c-141">ValidationStates</span></span>|<span data-ttu-id="8309c-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="8309c-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="8309c-143">PasswordBox ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="8309c-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="8309c-144">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.PasswordBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8309c-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="8309c-145">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="8309c-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8309c-146">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8309c-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8309c-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="8309c-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="8309c-148">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8309c-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="8309c-149">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8309c-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="8309c-150">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8309c-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="8309c-151">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8309c-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
