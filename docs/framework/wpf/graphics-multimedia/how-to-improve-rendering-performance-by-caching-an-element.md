---
title: "方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd12b811ae4dd89c645ada1f4f70b06f73b9b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる
使用して、<xref:System.Windows.Media.BitmapCache>の複雑なレンダリング パフォーマンスを向上させるためにクラス<xref:System.Windows.UIElement>です。 要素をキャッシュするには、新しいインスタンスを作成、<xref:System.Windows.Media.BitmapCache>クラスし、要素に割り当てる<xref:System.Windows.UIElement.CacheMode%2A>プロパティです。 再利用することができます、<xref:System.Windows.Media.BitmapCache>が効率的な<xref:System.Windows.Media.BitmapCacheBrush>します。  
  
## <a name="example"></a>例  
 次のコード例では、複合型の要素を作成し、パフォーマンスを向上させるときは、要素をアニメーション、ビットマップとしてキャッシュする方法を示します。 要素は、頂点の数を持つ図形ジオメトリを保持するキャンバスです。 A<xref:System.Windows.Media.BitmapCache>に既定値は値が割り当てられている、<xref:System.Windows.UIElement.CacheMode%2A>キャンバスのし、アニメーションは、キャッシュされたビットマップのスムーズな拡張を示しています。  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [方法: キャッシュされた要素をブラシとして使用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
