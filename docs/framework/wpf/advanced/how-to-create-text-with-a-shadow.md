---
title: "方法 : 影付きテキストを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b031b0dce8e1fd06399ded0b6d612a23323ae837
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="b54a3-102">方法 : 影付きテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="b54a3-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="b54a3-103">このセクションの例で、表示されるテキストに影を付ける方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b54a3-104">例</span><span class="sxs-lookup"><span data-stu-id="b54a3-104">Example</span></span>  
 <span data-ttu-id="b54a3-105"><xref:System.Windows.Media.Effects.DropShadowEffect>オブジェクトでは、さまざまなドロップ シャドウ効果を作成することができます[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b54a3-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="b54a3-106">テキストにドロップ シャドウ効果を適用した例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="b54a3-107">この場合、影はソフト シャドウです。つまり、影の色がぼやけています。</span><span class="sxs-lookup"><span data-stu-id="b54a3-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="b54a3-108">![テキストの影のぼかし &#61;です。0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="b54a3-108">![Text shadow with Softness &#61; 0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="b54a3-109">ソフト シャドウが付いたテキストの例</span><span class="sxs-lookup"><span data-stu-id="b54a3-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="b54a3-110">設定して影の幅を制御することができます、<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b54a3-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="b54a3-111">値`4.0`シャドウ幅 4 ピクセルを示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="b54a3-112">ぼかしを制御する、または変更することで影のぼかし、<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b54a3-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="b54a3-113">値`0.0`ないことを示しますぼかしが強くなります。</span><span class="sxs-lookup"><span data-stu-id="b54a3-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="b54a3-114">ソフト シャドウを付ける方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="b54a3-115">これらのシャドウ効果を通過しない、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テキスト レンダリング パイプライン。</span><span class="sxs-lookup"><span data-stu-id="b54a3-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="b54a3-116">結果として、これらの効果の利用時、ClearType が無効になります。</span><span class="sxs-lookup"><span data-stu-id="b54a3-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="b54a3-117">テキストにハード シャドウ効果を適用した例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="b54a3-118">この場合、影はぼかされません。</span><span class="sxs-lookup"><span data-stu-id="b54a3-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="b54a3-119">![テキストの影のぼかし &#61;です。0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="b54a3-119">![Text shadow with Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="b54a3-120">ハード シャドウが付いたテキストの例</span><span class="sxs-lookup"><span data-stu-id="b54a3-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="b54a3-121">設定してハード シャドウを作成することができます、<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>プロパティを`0.0`、ぼかし効果が使用されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="b54a3-122">影の方向を制御するには変更することによって、<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b54a3-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="b54a3-123">ある程度の間にこのプロパティの方向性のある値を設定`0`と`360`です。</span><span class="sxs-lookup"><span data-stu-id="b54a3-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="b54a3-124">次の図は、方向性のある値の<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>プロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="b54a3-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="b54a3-125">![シャドウの DropShadow 度の設定](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="b54a3-125">![DropShadow degree setting of shadow](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="b54a3-126">DropShadow 方向の図</span><span class="sxs-lookup"><span data-stu-id="b54a3-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="b54a3-127">ハード シャドウを付ける方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="b54a3-128">ぼかし効果を使用する</span><span class="sxs-lookup"><span data-stu-id="b54a3-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="b54a3-129">A<xref:System.Windows.Media.Effects.BlurBitmapEffect>テキスト オブジェクトの内側に配置可能なシャドウのような効果を作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b54a3-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="b54a3-130">テキストに適用されたぼかしビットマップ効果は、全方向に均等にテキストをぼかします。</span><span class="sxs-lookup"><span data-stu-id="b54a3-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="b54a3-131">テキストにぼかし効果が適用されている例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="b54a3-132">![BlurBitmapEffect を使用するテキスト シャドウ](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="b54a3-132">![Text shadow using a BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="b54a3-133">ぼかし効果が適用されたテキストの例</span><span class="sxs-lookup"><span data-stu-id="b54a3-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="b54a3-134">ぼかし効果を付ける方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="b54a3-135">TranslateTransform を使用する</span><span class="sxs-lookup"><span data-stu-id="b54a3-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="b54a3-136">A<xref:System.Windows.Media.TranslateTransform>テキスト オブジェクトの内側に配置可能なシャドウのような効果を作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b54a3-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="b54a3-137">次のコード例では、<xref:System.Windows.Media.TranslateTransform>テキストのオフセット。</span><span class="sxs-lookup"><span data-stu-id="b54a3-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="b54a3-138">この例では、メインのテキストの下にわずかに中心をずらしたコピーが付き、影のような効果を作っています。</span><span class="sxs-lookup"><span data-stu-id="b54a3-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="b54a3-139">![TranslateTransform を使用するテキスト シャドウ](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="b54a3-139">![Text shadow using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="b54a3-140">TranslateTransform を使用して影のような効果を付けたテキストの例</span><span class="sxs-lookup"><span data-stu-id="b54a3-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="b54a3-141">TranslateTransform を利用して影のような効果を付ける方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b54a3-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
