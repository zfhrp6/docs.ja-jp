---
title: "方法 : プロパティ値が変化したときにアニメーションをトリガーする | Microsoft Docs"
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
  - "アニメーション, 開始 (プロパティ値が変化したときに)"
  - "ストーリーボード, 開始 (プロパティ値が変化したときに)"
  - "トリガー (アニメーションを)"
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : プロパティ値が変化したときにアニメーションをトリガーする
この例では、<xref:System.Windows.Trigger> を使用して、プロパティ値が変更されたときに <xref:System.Windows.Media.Animation.Storyboard> を開始する方法を示します。  <xref:System.Windows.Trigger> は、<xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate>、または <xref:System.Windows.DataTemplate> の内部で使用できます。  
  
## 使用例  
 次の例では、<xref:System.Windows.Trigger> を使用して、<xref:System.Windows.Controls.Button> の <xref:System.Windows.UIElement.IsMouseOver%2A> プロパティが `true` になったときに、その <xref:System.Windows.UIElement.Opacity%2A> をアニメーション化します。  
  
 [!code-xml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 プロパティの <xref:System.Windows.Trigger> オブジェクトによって適用されるアニメーションの動作は、<xref:System.Windows.EventTrigger> アニメーション、または <xref:System.Windows.Media.Animation.Storyboard> メソッドを使用して開始されるアニメーションより複雑です。  他の <xref:System.Windows.Trigger> オブジェクトによって定義されるアニメーションで "ハンドオフ" しますが、<xref:System.Windows.EventTrigger> およびメソッドでトリガーされるアニメーションで構成されます。  
  
## 参照  
 <xref:System.Windows.Trigger>   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)