---
title: '方法 : システム ブラシで領域を塗りつぶす'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: f8a66ffc283016d65a17b33e98ce28fe4cd1c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561148"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="56984-102">方法 : システム ブラシで領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="56984-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="56984-103"><xref:System.Windows.SystemColors>クラスなどのシステム ブラシおよび色 へのアクセスの提供<xref:System.Windows.SystemColors.ControlBrush%2A>、 <xref:System.Windows.SystemColors.ControlBrushKey%2A>、および<xref:System.Windows.SystemColors.DesktopBrush%2A>です。</span><span class="sxs-lookup"><span data-stu-id="56984-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="56984-104">システム ブラシ、<xref:System.Windows.Media.SolidColorBrush>指定したシステム カラーを使用して領域を描画するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="56984-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="56984-105">システム ブラシは、常に純色の塗りつぶしを生成します。グラデーションを作成するために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="56984-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="56984-106">システム ブラシは、静的なリソースとしても、動的なリソースとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="56984-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="56984-107">アプリケーションの実行中にユーザーがシステム ブラシを変更したときにブラシを自動的に更新する場合は、動的なリソースを使用します。それ以外の場合は、静的なリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="56984-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="56984-108">SystemColors クラスには、厳密な名前付け規則に従うさまざまな静的プロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="56984-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="56984-109">*\<SystemColor>* Brush</span><span class="sxs-lookup"><span data-stu-id="56984-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="56984-110">静的参照を取得、<xref:System.Windows.Media.SolidColorBrush>の指定したシステム カラーです。</span><span class="sxs-lookup"><span data-stu-id="56984-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="56984-111">*\<SystemColor>* BrushKey</span><span class="sxs-lookup"><span data-stu-id="56984-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="56984-112">参照を動的に取得、<xref:System.Windows.Media.SolidColorBrush>の指定したシステム カラーです。</span><span class="sxs-lookup"><span data-stu-id="56984-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="56984-113">*\<SystemColor>* Color</span><span class="sxs-lookup"><span data-stu-id="56984-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="56984-114">静的参照を取得、<xref:System.Windows.Media.Color>指定したシステム カラーの構造。</span><span class="sxs-lookup"><span data-stu-id="56984-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="56984-115">*\<SystemColor>* ColorKey</span><span class="sxs-lookup"><span data-stu-id="56984-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="56984-116">参照を動的に取得、<xref:System.Windows.Media.Color>指定したシステム カラーの構造。</span><span class="sxs-lookup"><span data-stu-id="56984-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="56984-117">システム色は、<xref:System.Windows.Media.Color>ブラシを構成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="56984-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="56984-118">システム カラーを設定して、使用してグラデーションを作成するなど、<xref:System.Windows.Media.GradientStop.Color%2A>のプロパティ、<xref:System.Windows.Media.LinearGradientBrush>グラデーション終了位置を色のシステム オブジェクトの。</span><span class="sxs-lookup"><span data-stu-id="56984-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="56984-119">例については、次を参照してください。[のグラデーションを使用してシステム カラー](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)です。</span><span class="sxs-lookup"><span data-stu-id="56984-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56984-120">例</span><span class="sxs-lookup"><span data-stu-id="56984-120">Example</span></span>  
 <span data-ttu-id="56984-121">次の例では、動的なシステム ブラシの参照を使用して、ボタンの背景を設定します。</span><span class="sxs-lookup"><span data-stu-id="56984-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="56984-122">次の例では、静的なシステム ブラシの参照を使用して、ボタンの背景を設定します。</span><span class="sxs-lookup"><span data-stu-id="56984-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="56984-123">グラデーションのシステム カラーを使用する方法を示す例は、次を参照してください。[グラデーションのシステム カラーを使用して](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)です。</span><span class="sxs-lookup"><span data-stu-id="56984-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56984-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="56984-124">See Also</span></span>  
 [<span data-ttu-id="56984-125">グラデーションでシステム カラーを使用する</span><span class="sxs-lookup"><span data-stu-id="56984-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="56984-126">純色およびグラデーションによる塗りつぶしの概要</span><span class="sxs-lookup"><span data-stu-id="56984-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
