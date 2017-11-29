---
title: "方法 : 3-D 変換をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0477943b715a23a1d6992f7e9da885ffa01061c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-3-d-translations"></a>方法 : 3-D 変換をアニメーション化する
このトピックで設定の変換の変換をアニメーション化する方法を示します、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]モデル。  
  
 次のコードのアプリケーション、<xref:System.Windows.Media.Media3D.TranslateTransform3D>オブジェクトを<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>のプロパティ、<xref:System.Windows.Media.Media3D.GeometryModel3D>です。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>このプロパティ<xref:System.Windows.Media.Media3D.TranslateTransform3D>次のコードを使用してオブジェクトをアニメーション化します。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [3-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
