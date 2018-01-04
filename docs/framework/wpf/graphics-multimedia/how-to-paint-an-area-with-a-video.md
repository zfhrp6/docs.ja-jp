---
title: "方法 : ビデオを使用して領域を塗りつぶす"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a72843547d934aeaeec062eec1241e402baf56bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="8437d-102">方法 : ビデオを使用して領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="8437d-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="8437d-103">この例では、メディアを使用して領域を塗りつぶす方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8437d-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="8437d-104">メディアを使用して領域を描画する方法の 1 つを使用して、<xref:System.Windows.Controls.MediaElement>と共に、<xref:System.Windows.Media.VisualBrush>です。</span><span class="sxs-lookup"><span data-stu-id="8437d-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="8437d-105">使用して、<xref:System.Windows.Controls.MediaElement>ロードし、メディアを再生し、設定を使用する、<xref:System.Windows.Media.VisualBrush.Visual%2A>のプロパティ、<xref:System.Windows.Media.VisualBrush>です。</span><span class="sxs-lookup"><span data-stu-id="8437d-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="8437d-106">使用してできます、<xref:System.Windows.Media.VisualBrush>読み込まれたメディアで領域を塗りつぶすにします。</span><span class="sxs-lookup"><span data-stu-id="8437d-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8437d-107">例</span><span class="sxs-lookup"><span data-stu-id="8437d-107">Example</span></span>  
 <span data-ttu-id="8437d-108">次の例では、<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.VisualBrush>を描画する、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>ビデオ コントロール。</span><span class="sxs-lookup"><span data-stu-id="8437d-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="8437d-109">この例では設定、<xref:System.Windows.Controls.MediaElement.IsMuted%2A>のプロパティ、<xref:System.Windows.Controls.MediaElement>に`true`サウンドが生成されないようにします。</span><span class="sxs-lookup"><span data-stu-id="8437d-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="8437d-110">例</span><span class="sxs-lookup"><span data-stu-id="8437d-110">Example</span></span>  
 <span data-ttu-id="8437d-111"><xref:System.Windows.Media.VisualBrush>から継承、<xref:System.Windows.Media.TileBrush>クラス、いくつかのタイル モードを提供します。</span><span class="sxs-lookup"><span data-stu-id="8437d-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="8437d-112">設定して、<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティ、<xref:System.Windows.Media.VisualBrush>に<xref:System.Windows.Media.TileMode.Tile>を設定したり、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティを描画している領域より小さい値には、並べて表示するパターンを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8437d-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="8437d-113">次の例は点を除いて、前の例と同じ、<xref:System.Windows.Media.VisualBrush>ビデオからパターンが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8437d-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="8437d-114">そのため、アプリケーションが media ファイルなどのコンテンツ ファイルを追加する方法については、次を参照してください。 [WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="8437d-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="8437d-115">メディア ファイルを追加すると、リソース ファイルではなく、コンテンツ ファイルとして追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8437d-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8437d-116">参照</span><span class="sxs-lookup"><span data-stu-id="8437d-116">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="8437d-117">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="8437d-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="8437d-118">TileBrush の概要</span><span class="sxs-lookup"><span data-stu-id="8437d-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [<span data-ttu-id="8437d-119">マルチメディアの概要</span><span class="sxs-lookup"><span data-stu-id="8437d-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
