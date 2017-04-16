---
title: "方法 : StreamGeometry を使用して図形を作成する | Microsoft Docs"
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
  - "クラス, StreamGeometry"
  - "グラフィックス [WPF], 形状"
  - "形状, 作成 (StreamGeometry クラスを使用して)"
  - "StreamGeometry クラス"
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : StreamGeometry を使用して図形を作成する
<xref:System.Windows.Media.StreamGeometry> は、幾何学図形を作成するための <xref:System.Windows.Media.PathGeometry> の代替となる軽量クラスです。  複雑なジオメトリを作成する必要があるが、データ バインディング、アニメーション、または変更をサポートするためのオーバーヘッドが望ましくない場合は、<xref:System.Windows.Media.StreamGeometry> を使用します。  たとえば、<xref:System.Windows.Media.StreamGeometry> クラスは効率的であるため、装飾の表現に適しています。  
  
## 使用例  
 次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で属性構文を使用して三角形の <xref:System.Windows.Media.StreamGeometry> を作成します。  
  
 [!code-xml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <xref:System.Windows.Media.StreamGeometry> 属性構文の詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。  
  
## 使用例  
 次の例では、コードで <xref:System.Windows.Media.StreamGeometry> を使用して三角形を定義します。  最初に <xref:System.Windows.Media.StreamGeometry> を作成した後、<xref:System.Windows.Media.StreamGeometryContext> を取得し、そのコンテキストを使用して三角形を記述します。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.StreamGeometry> と <xref:System.Windows.Media.StreamGeometryContext> を使用して指定パラメーターに基づいて幾何学図形を定義するメソッドを作成します。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Media.StreamGeometry>   
 <xref:System.Windows.Media.StreamGeometryContext>   
 [PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)   
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)