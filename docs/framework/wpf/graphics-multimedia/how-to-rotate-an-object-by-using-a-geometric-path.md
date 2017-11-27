---
title: "方法 : ジオメトリック パスを使用してオブジェクトを回転させる"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>方法 : ジオメトリック パスを使用してオブジェクトを回転させる
この例では回転 (pivot) で定義されているジオメトリ パスに沿ってオブジェクト、<xref:System.Windows.Media.PathGeometry>オブジェクト。  
  
## <a name="example"></a>例  
 次の例は、3 つ<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>オブジェクトのジオメトリのパスに沿った四角形を移動します。  
  
-   最初の<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、<xref:System.Windows.Media.RotateTransform>四角形に適用されています。 アニメーションは、角度の値を生成します。 これにより、四角形がパスの輪郭に沿って回転 (ピボット) します。  
  
-   その他の 2 つのオブジェクトをアニメーション化する、<xref:System.Windows.Media.TranslateTransform.X%2A>と<xref:System.Windows.Media.TranslateTransform.Y%2A>の値、<xref:System.Windows.Media.TranslateTransform>四角形に適用されています。 これにより、四角形が、パスに沿って水平方向と垂直方向に移動します。  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 幾何学模様のパスを使用してオブジェクトの回転を別の方法を使用して、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>オブジェクトし、設定、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>プロパティを`true`です。 例および詳細については、次を参照してください。[幾何学模様のパス (行列アニメーション) を使用してオブジェクトを回転させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)です。  
  
 サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
