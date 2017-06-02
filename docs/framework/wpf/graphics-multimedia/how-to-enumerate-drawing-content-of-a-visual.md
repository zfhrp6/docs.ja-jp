---
title: "方法 : ビジュアルの描画コンテンツを列挙する | Microsoft Docs"
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
  - "列挙 (Visual のコンテンツを) [WPF]"
  - "取得 (Visual の DrawingGroup 値を) [WPF]"
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 方法 : ビジュアルの描画コンテンツを列挙する
<xref:System.Windows.Media.Drawing> オブジェクトは、<xref:System.Windows.Media.Visual> のコンテンツを列挙するためのオブジェクト モデルを提供します。  
  
## 使用例  
 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> メソッドを使用して、<xref:System.Windows.Media.Visual> の <xref:System.Windows.Media.DrawingGroup> 値を取得し列挙する例を次に示します。  
  
> [!NOTE]
>  ビジュアルのコンテンツの列挙の際には、ベクター グラフィックス命令リストとして基になるレンダリング データ表現を取得しているのではなく、<xref:System.Windows.Media.Drawing> オブジェクトを取得しています。  詳細については、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」を参照してください。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## 参照  
 <xref:System.Windows.Media.Drawing>   
 <xref:System.Windows.Media.DrawingGroup>   
 <xref:System.Windows.Media.VisualTreeHelper>   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)