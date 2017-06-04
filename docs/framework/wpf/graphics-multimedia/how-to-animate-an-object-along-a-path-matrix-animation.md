---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (行列アニメーション) | Microsoft Docs"
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
  - "アニメーション オブジェクトをパスに沿って (行列アニメーション)"
  - "行列アニメーション"
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)
この例では、使用して、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>で定義されているパスに沿ってオブジェクトをアニメーション化するクラス、 <xref:System.Windows.Media.PathGeometry>します。  
  
## <a name="example"></a>例  
 次の例では、次の手順に従ってパスに沿ってオブジェクトをアニメーション化します。  
  
-   適用される、 <xref:System.Windows.Media.MatrixTransform>に移動するためにオブジェクトにします。  
  
-   使用してパスを定義、 <xref:System.Windows.Media.PathGeometry>します。  
  
-   作成、 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>オブジェクトをアニメーション化を使用して、<xref:System.Windows.Media.Matrix>のプロパティ、 <xref:System.Windows.Media.MatrixTransform>します。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>は、 <xref:System.Windows.Media.PathGeometry>し使用して生成<xref:System.Windows.Media.Matrix>値。  
  
 [!code-xml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 完全なサンプルを参照してください。[パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)します。 ジオメトリック パスの詳細については、次を参照してください。、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)します。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)   
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)