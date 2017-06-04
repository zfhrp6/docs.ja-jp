---
title: "方法 : パラメーターとしてジオメトリを使用してヒット テストを実行する | Microsoft Docs"
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
  - "Geometry オブジェクト, ヒット テスト (ビジュアル オブジェクトに対する)"
  - "ヒット テスト, Geometry オブジェクトによるビジュアル オブジェクトに対するヒット テスト"
  - "ビジュアル オブジェクト, ヒット テスト"
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : パラメーターとしてジオメトリを使用してヒット テストを実行する
この例では、<xref:System.Windows.Media.Geometry> をヒット テスト パラメーターとして使用して、ビジュアル オブジェクトに対して[ヒット テスト](GTMT)を実行する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> メソッドの <xref:System.Windows.Media.GeometryHitTestParameters> を使用してヒット テストを設定する方法を次の例に示します。  `OnMouseDown` メソッドに渡される <xref:System.Windows.Point> 値は、<xref:System.Windows.Media.Geometry> オブジェクトを作成してヒット テストの範囲を拡張する場合に使用されます。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult> の <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> プロパティは、<xref:System.Windows.Media.Geometry> をヒット テスト パラメーターとして使用したヒット テストの実行結果に関する情報を提供します。  ヒット テストのジオメトリ \(青い円\) と対象のビジュアル オブジェクト \(赤い正方形\) の描画されるコンテンツとの関係を次の図に示します。  
  
 ![ヒット テストで使用される IntersectionDetail のダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
ヒット テストのジオメトリと対象のビジュアル オブジェクトの交差部分  
  
 <xref:System.Windows.Media.Geometry> をヒット テスト パラメーターとして使用する場合に、ヒット テストのコールバックを実装する方法を次の例に示します。  <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> プロパティの値を取得するために、`result` パラメーターを <xref:System.Windows.Media.GeometryHitTestResult> にキャストしています。  このプロパティ値を使用して、<xref:System.Windows.Media.Geometry> ヒット テスト パラメーターの全体または一部がヒット テスト対象の描画されるコンテンツ内に含まれるかどうかを判別することができます。  ここに示すサンプル コードでは、完全に対象の境界内に含まれるビジュアルについてのみ、ヒット テストの結果をリストに追加しています。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  IntersectionDetail が <xref:System.Windows.Media.IntersectionDetail> の場合は、<xref:System.Windows.Media.HitTestResult> コールバックを呼び出さないようにしてください。  
  
## 参照  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)   
 [ビジュアル内のジオメトリのヒット テストを実行する](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)