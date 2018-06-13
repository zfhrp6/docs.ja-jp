---
title: '方法: キャッシュされた要素をブラシとして使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: c43c4ecbefe99d6e38766705378d85d92ecc5729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561525"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="89ea7-102">方法: キャッシュされた要素をブラシとして使用する</span><span class="sxs-lookup"><span data-stu-id="89ea7-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="89ea7-103">使用して、<xref:System.Windows.Media.BitmapCacheBrush>を効率的にキャッシュされた要素を再利用するクラス。</span><span class="sxs-lookup"><span data-stu-id="89ea7-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="89ea7-104">要素をキャッシュするには、新しいインスタンスを作成、<xref:System.Windows.Media.BitmapCache>クラスし、要素に割り当てる<xref:System.Windows.UIElement.CacheMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="89ea7-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89ea7-105">例</span><span class="sxs-lookup"><span data-stu-id="89ea7-105">Example</span></span>  
 <span data-ttu-id="89ea7-106">次のコード例では、キャッシュされた要素を再利用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="89ea7-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="89ea7-107">キャッシュされた要素は、<xref:System.Windows.Controls.Image>大きな画像を表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="89ea7-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="89ea7-108"><xref:System.Windows.Controls.Image>コントロールを使用して、ビットマップとしてキャッシュは、<xref:System.Windows.Media.BitmapCache>クラス、およびキャッシュに割り当てることで再利用、<xref:System.Windows.Media.BitmapCacheBrush>です。</span><span class="sxs-lookup"><span data-stu-id="89ea7-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="89ea7-109">ブラシは、効率的な再利用を表示するのに 25 個のボタンの背景に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="89ea7-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="89ea7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="89ea7-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="89ea7-111">方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="89ea7-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
