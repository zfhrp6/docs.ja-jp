---
title: "方法 : Canvas を作成および使用する | Microsoft Docs"
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
  - "Canvas コントロール, 作成"
  - "Canvas コントロール, 使用"
  - "コントロール, Canvas"
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Canvas を作成および使用する
<xref:System.Windows.Controls.Canvas> のインスタンスを作成して使用する方法を次の例に示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Canvas.SetTop%2A> メソッドと <xref:System.Windows.Controls.Canvas.SetLeft%2A> メソッドを使用して、2 つの <xref:System.Windows.Controls.TextBlock> 要素を明示的に配置しています。  また、この例では、`LightSteelBlue` の <xref:System.Windows.Controls.Control.Background%2A> 色を <xref:System.Windows.Controls.Canvas> に割り当てています。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して <xref:System.Windows.Controls.TextBlock> 要素を配置する場合は、<xref:System.Windows.Controls.Canvas.Top%2A> プロパティと <xref:System.Windows.Controls.Canvas.Left%2A> プロパティを使用します。  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.TextBlock>   
 <xref:System.Windows.Controls.Canvas.SetTop%2A>   
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>   
 <xref:System.Windows.Controls.Canvas.Top%2A>   
 <xref:System.Windows.Controls.Canvas.Left%2A>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)