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
# <a name="how-to-use-a-cached-element-as-a-brush"></a>方法: キャッシュされた要素をブラシとして使用する
使用して、<xref:System.Windows.Media.BitmapCacheBrush>を効率的にキャッシュされた要素を再利用するクラス。 要素をキャッシュするには、新しいインスタンスを作成、<xref:System.Windows.Media.BitmapCache>クラスし、要素に割り当てる<xref:System.Windows.UIElement.CacheMode%2A>プロパティです。  
  
## <a name="example"></a>例  
 次のコード例では、キャッシュされた要素を再利用する方法を示します。 キャッシュされた要素は、<xref:System.Windows.Controls.Image>大きな画像を表示するコントロール。 <xref:System.Windows.Controls.Image>コントロールを使用して、ビットマップとしてキャッシュは、<xref:System.Windows.Media.BitmapCache>クラス、およびキャッシュに割り当てることで再利用、<xref:System.Windows.Media.BitmapCacheBrush>です。 ブラシは、効率的な再利用を表示するのに 25 個のボタンの背景に割り当てられます。  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
