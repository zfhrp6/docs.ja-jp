---
title: "方法 : カスタム パネル要素を作成する | Microsoft Docs"
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
  - "カスタムの Panel 要素"
  - "Panel コントロール"
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : カスタム パネル要素を作成する
## 使用例  
 この例では、<xref:System.Windows.Controls.Panel> 要素の既定のレイアウト動作をオーバーライドして、<xref:System.Windows.Controls.Panel> から派生したカスタム レイアウト要素を作成する方法を示します。  
  
 この例では、`PlotPanel` という単純なカスタム <xref:System.Windows.Controls.Panel> 要素を定義します。この要素は、ハードコーディングされた x 座標および y 座標に従って子要素を配置します。  この例では、`x` および `y` をどちらも `50` に設定します。そのため、すべての子要素は x 座標および y 座標上のこの位置に配置されます。  
  
 カスタムの <xref:System.Windows.Controls.Panel> 動作を実装するために、この例では <xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドと <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドを使用します。  各メソッドは、子要素の配置とレンダリングに必要な <xref:System.Windows.Size> データを返します。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Panel>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [カスタム コンテンツ折り返しパネルの作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159979)