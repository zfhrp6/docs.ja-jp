---
title: "方法 : ScrollBar のつまみのサイズをカスタマイズする | Microsoft Docs"
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
  - "カスタマイズ (つまみのサイズを)"
  - "ScrollBar コントロール"
  - "つまみのサイズ"
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : ScrollBar のつまみのサイズをカスタマイズする
このトピックでは、<xref:System.Windows.Controls.Primitives.ScrollBar> の <xref:System.Windows.Controls.Primitives.Thumb> を固定サイズに設定する方法と <xref:System.Windows.Controls.Primitives.ScrollBar> の <xref:System.Windows.Controls.Primitives.Thumb> の最小サイズを指定する方法について説明します。  
  
## 使用例  
  
## Description  
 次の例は、固定サイズの <xref:System.Windows.Controls.Primitives.Thumb> を持つ <xref:System.Windows.Controls.Primitives.ScrollBar> を作成します。  この例では、<xref:System.Windows.Controls.Primitives.Thumb> の <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> プロパティを <xref:System.Double.NaN> に設定し、<xref:System.Windows.Controls.Primitives.Thumb> の高さを設定しています。  固定幅の <xref:System.Windows.Controls.Primitives.Thumb> を持つ水平 <xref:System.Windows.Controls.Primitives.ScrollBar> を作成するには、<xref:System.Windows.Controls.Primitives.Thumb> の幅を設定します。  
  
## コード  
 [!code-xml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## Description  
 次の例は、最小サイズの <xref:System.Windows.Controls.Primitives.Thumb> を持つ <xref:System.Windows.Controls.Primitives.ScrollBar> を作成します。  この例では、<xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A> の値を設定しています。  最小幅の <xref:System.Windows.Controls.Primitives.Thumb> を持つ水平 <xref:System.Windows.Controls.Primitives.ScrollBar> を作成するには、<xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A> の幅を設定します。  
  
## コード  
 [!code-xml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## 参照  
 [ScrollBar のスタイルとテンプレート](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)