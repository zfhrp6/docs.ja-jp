---
title: "方法 : コントロールの背景にテキストを描画する | Microsoft Docs"
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
  - "背景, 描画 (テキストを)"
  - "コントロール, 描画 (背景にテキストを)"
  - "描画, コントロールの背景に対するテキスト"
  - "テキスト, 描画 (コントロールの背景に)"
  - "タイポグラフィ, 描画 (コントロールの背景にテキストを)"
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : コントロールの背景にテキストを描画する
テキスト文字列を <xref:System.Windows.Media.FormattedText> オブジェクトに変換し、そのオブジェクトをコントロールの <xref:System.Windows.Media.DrawingContext> に描画することにより、コントロールの背景にテキストを直接描画できます。  この手法は、<xref:System.Windows.Controls.Canvas> や <xref:System.Windows.Controls.StackPanel> などの <xref:System.Windows.Controls.Panel> から派生したオブジェクトの背景への描画にも使用できます。  
  
 ![テキストを背景として表示するコントロール](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
カスタム テキスト背景のコントロールの例  
  
## 使用例  
 コントロールの背景に描画するには、新しい <xref:System.Windows.Media.DrawingBrush> オブジェクトを作成して、変換したテキストをオブジェクトの <xref:System.Windows.Media.DrawingContext> に描画します。  次に、新しい <xref:System.Windows.Media.DrawingBrush> をコントロールの Background プロパティに割り当てます。  
  
 <xref:System.Windows.Media.FormattedText> オブジェクトを作成し、<xref:System.Windows.Controls.Label> オブジェクトと <xref:System.Windows.Controls.Button> オブジェクトの背景に描画する方法を次のコード例に示します。  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## 参照  
 <xref:System.Windows.Media.FormattedText>   
 [書式設定されたテキストの描画](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)