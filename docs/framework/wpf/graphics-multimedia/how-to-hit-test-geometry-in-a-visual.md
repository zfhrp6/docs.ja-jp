---
title: "方法 : ビジュアル内のジオメトリのヒット テストを実行する | Microsoft Docs"
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
  - "Geometry オブジェクト, ビジュアル オブジェクトを構成する"
  - "ヒット テスト, Geometry オブジェクトで構成されるビジュアル オブジェクト"
  - "ビジュアル オブジェクト, ヒット テスト"
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ビジュアル内のジオメトリのヒット テストを実行する
この例では、1 つ以上の <xref:System.Windows.Media.Geometry> オブジェクトで構成されるビジュアル オブジェクトに対して[ヒット テスト](GTMT)を実行する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> メソッドを使用して、ビジュアル オブジェクトから <xref:System.Windows.Media.DrawingGroup> を取得する方法を次の例に示します。  次に、<xref:System.Windows.Media.DrawingGroup> の各描画のレンダリングされたコンテンツに対してヒット テストを実行し、ヒットしたジオメトリを確認します。  
  
> [!NOTE]
>  通常、ポイントがビジュアルのレンダリングされたコンテンツと交差するかどうかを判定するには、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> メソッドを使用します。  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A> メソッドはオーバーロードされたメソッドであり、これを使用すると、指定した <xref:System.Windows.Point> または <xref:System.Windows.Media.Geometry> を使用してヒット テストを行うことができます。  ジオメトリに線が付いている場合は、塗りつぶしの境界の外側までストロークを延長できます。  この場合は、<xref:System.Windows.Media.Geometry.FillContains%2A> に加えて <xref:System.Windows.Media.Geometry.StrokeContains%2A> を呼び出すことができます。  
  
 ベジエ平坦化に使用する <xref:System.Windows.Media.ToleranceType> を提供することもできます。  
  
> [!NOTE]
>  このサンプルでは、ジオメトリに適用される可能性のある変換またはクリッピングは考慮していません。  また、スタイルが設定されたコントロールには直接関連付けられた描画がないので、このサンプルはスタイルが設定されたコントロールに対しては機能しません。  
  
## 参照  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [パラメーターとしてジオメトリを使用してヒット テストを実行する](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)