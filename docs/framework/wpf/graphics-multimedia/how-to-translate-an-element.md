---
title: "方法 : 要素を変換する | Microsoft Docs"
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
  - "クラス, TranslateTransform"
  - "グラフィックス, 変換"
  - "TranslateTransform クラス"
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 要素を変換する
この例では、<xref:System.Windows.Media.TranslateTransform> を使用して要素を変換 \(移動\) する方法を示します。  
  
 <xref:System.Windows.Media.TranslateTransform> クラスは、絶対配置をサポートしないパネルの内部で要素を移動する場合に特に便利です。  たとえば、要素の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに <xref:System.Windows.Media.TranslateTransform> を適用することで、<xref:System.Windows.Controls.StackPanel> または <xref:System.Windows.Controls.DockPanel> 内で要素を移動できます。  
  
 x 軸方向の要素の移動量 \([ピクセル](GTMT)単位\) を指定するには、<xref:System.Windows.Media.TranslateTransform> の <xref:System.Windows.Media.TranslateTransform.X%2A> プロパティを使用します。  y 軸方向の要素の移動量 \(ピクセル単位\) を指定するには、<xref:System.Windows.Media.TranslateTransform.Y%2A> プロパティを使用します。  最後に、要素の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに <xref:System.Windows.Media.TranslateTransform> を適用します。  
  
 次の例では、<xref:System.Windows.Media.TranslateTransform> を使用して、要素を右に 50 [ピクセル](GTMT)、下に 50 ピクセル移動します。  
  
## 使用例  
 [!code-xml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 サンプル全体については、[2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  
  
## 参照  
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)