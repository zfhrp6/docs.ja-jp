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
ms.workload: dotnet
ms.openlocfilehash: f463c15855e267a4c246625a8d06e627852f48a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>方法: キャッシュされた要素をブラシとして使用する
使用して、<xref:System.Windows.Media.BitmapCacheBrush>を効率的にキャッシュされた要素を再利用するクラス。 要素をキャッシュするには、新しいインスタンスを作成、<xref:System.Windows.Media.BitmapCache>クラスし、要素に割り当てる<xref:System.Windows.UIElement.CacheMode%2A>プロパティです。  
  
## <a name="example"></a>例  
 次のコード例では、キャッシュされた要素を再利用する方法を示します。 キャッシュされた要素は、<xref:System.Windows.Controls.Image>大きな画像を表示するコントロール。 <xref:System.Windows.Controls.Image>コントロールを使用して、ビットマップとしてキャッシュは、<xref:System.Windows.Media.BitmapCache>クラス、およびキャッシュに割り当てることで再利用、<xref:System.Windows.Media.BitmapCacheBrush>です。 ブラシは、効率的な再利用を表示するのに 25 個のボタンの背景に割り当てられます。  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
