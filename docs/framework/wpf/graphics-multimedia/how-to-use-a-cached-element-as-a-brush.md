---
title: "方法: キャッシュされた要素をブラシとして使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d0f0c60e9df6a1ec816b1f9cf5769c93b382ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="c9e61-102">方法: キャッシュされた要素をブラシとして使用する</span><span class="sxs-lookup"><span data-stu-id="c9e61-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="c9e61-103">使用して、<xref:System.Windows.Media.BitmapCacheBrush>を効率的にキャッシュされた要素を再利用するクラス。</span><span class="sxs-lookup"><span data-stu-id="c9e61-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="c9e61-104">要素をキャッシュするには、新しいインスタンスを作成、<xref:System.Windows.Media.BitmapCache>クラスし、要素に割り当てる<xref:System.Windows.UIElement.CacheMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c9e61-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9e61-105">例</span><span class="sxs-lookup"><span data-stu-id="c9e61-105">Example</span></span>  
 <span data-ttu-id="c9e61-106">次のコード例では、キャッシュされた要素を再利用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c9e61-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="c9e61-107">キャッシュされた要素は、<xref:System.Windows.Controls.Image>大きな画像を表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="c9e61-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="c9e61-108"><xref:System.Windows.Controls.Image>コントロールを使用して、ビットマップとしてキャッシュは、<xref:System.Windows.Media.BitmapCache>クラス、およびキャッシュに割り当てることで再利用、<xref:System.Windows.Media.BitmapCacheBrush>です。</span><span class="sxs-lookup"><span data-stu-id="c9e61-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="c9e61-109">ブラシは、効率的な再利用を表示するのに 25 個のボタンの背景に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c9e61-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="c9e61-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9e61-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="c9e61-111">方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="c9e61-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
