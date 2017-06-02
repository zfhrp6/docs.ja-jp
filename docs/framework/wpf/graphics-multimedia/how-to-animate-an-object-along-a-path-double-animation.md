---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アニメーション オブジェクトをパスに沿って (ダブル アニメーション)"
  - "ダブル アニメーション"
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)
この例では、使用して、 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>クラスで定義されているパスに沿ってオブジェクトを移動する、 <xref:System.Windows.Media.PathGeometry>します。  
  
## <a name="example"></a>例  
 次の例を使用して&2; つ<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>ジオメトリック パスに沿った四角形を移動するオブジェクト。  
  
-   最初の<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、 <xref:System.Windows.Media.TranslateTransform.X%2A>の<xref:System.Windows.Media.TranslateTransform>四角形に適用します。 パスに沿って水平方向に移動する四角形を使用して行えます。  
  
-   2 番目<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、 <xref:System.Windows.Media.TranslateTransform.Y%2A>の<xref:System.Windows.Media.TranslateTransform>四角形に適用します。 ほうが四角形パスに沿った垂直方向に移動をします。  
  
 [!code-xml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 完全なサンプルを参照してください。[パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)します。  
  
 ジオメトリック パスを使用してオブジェクトを移動する別の方法を使用して、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>オブジェクトです。 例については、次を参照してください。[オブジェクト上のパス (行列アニメーション) をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)