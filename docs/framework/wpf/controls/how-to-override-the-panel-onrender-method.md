---
title: "方法 : パネルの OnRender メソッドをオーバーライドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "overriding OnRender method"
  - "Panel control, overriding OnRender method"
  - "OnRender method"
  - "controls, Panel, overriding OnRender method"
helpviewer_keywords: 
  - "OnRender メソッド, オーバーライド"
  - "オーバーライド (Panel コントロールの OnRender メソッドを)"
  - "Panel コントロール, オーバーライド (OnRender メソッドを)"
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : パネルの OnRender メソッドをオーバーライドする
この例では、<xref:System.Windows.Controls.Panel> の <xref:System.Windows.Controls.Panel.OnRender%2A> メソッドをオーバーライドして、レイアウト要素にカスタムのグラフィカル効果を追加する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Panel.OnRender%2A> メソッドを使用して、描画されたパネル要素にグラフィカル効果を追加します。  たとえば、このメソッドを使用してカスタムの境界線または背景の効果を追加できます。  <xref:System.Windows.Media.DrawingContext> オブジェクトが引数として渡され、図形、テキスト、イメージ、またはビデオを描画するためのメソッドを提供します。  このため、このメソッドはパネル オブジェクトをカスタマイズするのに役立ちます。  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Panel>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [カスタム放射状パネルのサンプル](http://go.microsoft.com/fwlink/?LinkID=159982)   
 [方法のトピック](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)