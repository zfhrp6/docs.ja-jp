---
title: "方法 : ビジュアルにテキストを描画する | Microsoft Docs"
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
  - "描画, テキストをビジュアルに"
  - "テキスト, 描画 (ビジュアルに)"
  - "タイポグラフィ, 描画 (テキストをビジュアルに)"
  - "ビジュアル, 描画 (テキストを)"
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ビジュアルにテキストを描画する
<xref:System.Windows.Media.DrawingContext> オブジェクトを使用して <xref:System.Windows.Media.DrawingVisual> にテキストを描画する方法を次の例に示します。  描画コンテキストは、<xref:System.Windows.Media.DrawingVisual> オブジェクトの <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> メソッドを呼び出すことによって返されます。  描画コンテキストにグラフィックスとテキストを描画することができます。  
  
 描画コンテキストにテキストを描画するには、<xref:System.Windows.Media.DrawingContext> オブジェクトの <xref:System.Windows.Media.DrawingContext.DrawText%2A> メソッドを使用します。  描画コンテキストへのコンテンツの描画が完了したら、<xref:System.Windows.Media.DrawingContext.Close%2A> メソッドを呼び出して描画コンテキストを閉じ、コンテンツを保持します。  
  
## 使用例  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  前のコード例を含むコード サンプル全体については、[DrawingVisual を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)を参照してください。