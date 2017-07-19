---
title: "方法 : Canvas の添付プロパティを使用して子要素を配置する | Microsoft Docs"
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
  - "添付プロパティ [WPF デザイナー]"
  - "Canvas コントロール, 添付プロパティ"
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Canvas の添付プロパティを使用して子要素を配置する
この例では、<xref:System.Windows.Controls.Canvas> の[添付プロパティ](GTMT)を使用して子要素を配置する方法を示します。  
  
## 使用例  
 次の例では、4 つの <xref:System.Windows.Controls.Button> 要素を親 <xref:System.Windows.Controls.Canvas> の子要素として追加します。  各子要素は、<xref:System.Windows.Controls.Canvas> の異なる添付プロパティである <xref:System.Windows.Controls.Canvas.Bottom%2A>、<xref:System.Windows.Controls.Canvas.Left%2A>、<xref:System.Windows.Controls.Canvas.Right%2A>、および <xref:System.Windows.Controls.Canvas.Top%2A> を表します。  各 <xref:System.Windows.Controls.Button> は、親の <xref:System.Windows.Controls.Canvas> を基準に、割り当てられているプロパティ値に従って配置されます。  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.Canvas.Bottom%2A>   
 <xref:System.Windows.Controls.Canvas.Left%2A>   
 <xref:System.Windows.Controls.Canvas.Right%2A>   
 <xref:System.Windows.Controls.Canvas.Top%2A>   
 <xref:System.Windows.Controls.Button>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)   
 [添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)