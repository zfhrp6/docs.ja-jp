---
title: DocumentViewer のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: 217fa0ff7b8c34de817a269effbf64311bbea7f2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="e32d0-102">DocumentViewer のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="e32d0-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="e32d0-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e32d0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="e32d0-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="e32d0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e32d0-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e32d0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="e32d0-106">DocumentViewer のパーツ</span><span class="sxs-lookup"><span data-stu-id="e32d0-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="e32d0-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e32d0-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="e32d0-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="e32d0-108">Part</span></span>|<span data-ttu-id="e32d0-109">型</span><span class="sxs-lookup"><span data-stu-id="e32d0-109">Type</span></span>|<span data-ttu-id="e32d0-110">説明</span><span class="sxs-lookup"><span data-stu-id="e32d0-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e32d0-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="e32d0-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="e32d0-112">コンテンツと領域をスクロールします。</span><span class="sxs-lookup"><span data-stu-id="e32d0-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="e32d0-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="e32d0-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="e32d0-114">既定では下部にある検索ボックス。</span><span class="sxs-lookup"><span data-stu-id="e32d0-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="e32d0-115">DocumentViewer の状態</span><span class="sxs-lookup"><span data-stu-id="e32d0-115">DocumentViewer States</span></span>  
 <span data-ttu-id="e32d0-116">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e32d0-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="e32d0-117">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="e32d0-117">VisualState Name</span></span>|<span data-ttu-id="e32d0-118">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="e32d0-118">VisualStateGroup Name</span></span>|<span data-ttu-id="e32d0-119">説明</span><span class="sxs-lookup"><span data-stu-id="e32d0-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e32d0-120">有効</span><span class="sxs-lookup"><span data-stu-id="e32d0-120">Valid</span></span>|<span data-ttu-id="e32d0-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e32d0-121">ValidationStates</span></span>|<span data-ttu-id="e32d0-122">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="e32d0-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e32d0-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e32d0-123">InvalidFocused</span></span>|<span data-ttu-id="e32d0-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e32d0-124">ValidationStates</span></span>|<span data-ttu-id="e32d0-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="e32d0-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e32d0-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e32d0-126">InvalidUnfocused</span></span>|<span data-ttu-id="e32d0-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e32d0-127">ValidationStates</span></span>|<span data-ttu-id="e32d0-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="e32d0-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="e32d0-129">DocumentViewer ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="e32d0-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="e32d0-130">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e32d0-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="e32d0-131">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="e32d0-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e32d0-132">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e32d0-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32d0-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e32d0-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e32d0-134">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="e32d0-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e32d0-135">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e32d0-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e32d0-136">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="e32d0-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e32d0-137">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e32d0-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
