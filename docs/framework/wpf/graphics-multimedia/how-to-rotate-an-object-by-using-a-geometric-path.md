---
title: "方法 : ジオメトリック パスを使用してオブジェクトを回転させる | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ジオメトリック パス、によってオブジェクトを回転させる"
  - "回転 (ジオメトリック パスでオブジェクトを)"
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ジオメトリック パスを使用してオブジェクトを回転させる
この例では (ピボット) を回転するオブジェクトによって定義されたジオメトリック パスに沿って、 <xref:System.Windows.Media.PathGeometry>オブジェクトです。  
  
## <a name="example"></a>例  
 次の例は、3 つ<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>ジオメトリック パスに沿った四角形を移動するオブジェクト。  
  
-   最初の<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、 <xref:System.Windows.Media.RotateTransform>四角形に適用されています。 アニメーションは、角度の値を生成します。 パスの輪郭に沿って (ピボット) を回転する四角形を使用して行えます。  
  
-   その他の&2; つのオブジェクトをアニメーション化する、 <xref:System.Windows.Media.TranslateTransform.X%2A>と<xref:System.Windows.Media.TranslateTransform.Y%2A>の値、 <xref:System.Windows.Media.TranslateTransform>四角形に適用されています。 四角形の幅と高さをパスに沿って移動を確認します。  
  
 [!code-xml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 ジオメトリック パスを使用してオブジェクトを回転する別の方法を使用して、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>オブジェクトし、設定、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>プロパティを`true`します。 詳細と例では、次を参照してください。[ジオメトリック パス (行列アニメーション) を使用してオブジェクトを回転させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)します。  
  
 完全なサンプルを参照してください。[パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)します。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)