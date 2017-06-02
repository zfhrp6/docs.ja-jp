---
title: "方法 : 反射を作成する | Microsoft Docs"
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
  - "ブラシ, 作成 (反射を)"
  - "作成 (反射を)"
  - "反射, 作成"
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 反射を作成する
この例では、<xref:System.Windows.Media.VisualBrush> を使用して反射を作成する方法を示します。  <xref:System.Windows.Media.VisualBrush> は既存のビジュアルを表示できるため、この機能を使用して、反射や拡大など関心を引くための視覚効果を作成できます。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.VisualBrush> を使用して、複数の要素が含まれる <xref:System.Windows.Controls.Border> の鏡像を作成します。  この例が生成する出力を次の図に示します。  
  
 ![反映された Visual オブジェクト](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.png "graphicsmm\_visualbrush\_reflection\_small")  
ビジュアル オブジェクトの鏡像  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 画面の一部分を拡大する方法および反射を作成する方法の例を含むサンプル全体については、[VisualBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160049)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.VisualBrush>   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)