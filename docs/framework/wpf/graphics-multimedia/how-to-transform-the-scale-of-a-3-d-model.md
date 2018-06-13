---
title: '方法 : 3-D モデルのスケールを変換する'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 3cca1a210a7dbe410ebaacaaf89c08de8c31c40e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561099"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>方法 : 3-D モデルのスケールを変換する
この例では、3-D オブジェクトをスケーリングする方法を示します。 する 3d オブジェクトを拡張するを使用して、<xref:System.Windows.Media.Media3D.ScaleTransform3D>です。 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>、 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>、および<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>プロパティを指定する係数で要素のサイズを変更します。 たとえば、 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> 1.5 の値が元の幅の 150% にオブジェクトを拡大します。 A<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>値 0.5 は 50% でオブジェクトの高さを縮小します。 次のコードを使用して、<xref:System.Windows.Media.Media3D.ScaleTransform3D>に対して変換として、<xref:System.Windows.Media.Media3D.GeometryModel3D>です。  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [3-D 変換をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [3-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
