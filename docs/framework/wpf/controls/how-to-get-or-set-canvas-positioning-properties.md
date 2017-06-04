---
title: "方法 : Canvas の配置プロパティを取得または設定する | Microsoft Docs"
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
  - "Canvas コントロール, 設定 (位置決めのプロパティを)"
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Canvas の配置プロパティを取得または設定する
この例では、<xref:System.Windows.Controls.Canvas> 要素の配置メソッドを使用して子要素を配置する方法を示します。  この例では、<xref:System.Windows.Controls.ListBoxItem> 内のコンテンツを使用して配置の値を表し、その値を、配置に必要な引数である <xref:System.Double> のインスタンスに変換します。  次に、この値を文字列に戻し、<xref:System.Windows.Controls.Canvas.GetLeft%2A> メソッドを使用して <xref:System.Windows.Controls.TextBlock> 要素にテキストとして表示します。  
  
## 使用例  
 次の例では、11 個の選択可能な <xref:System.Windows.Controls.ListBoxItem> 要素を持つ <xref:System.Windows.Controls.ListBox> 要素を作成します。  <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> イベントは、後続のコード ブロックで定義される `ChangeLeft` カスタム メソッドをトリガーします。  
  
 各 <xref:System.Windows.Controls.ListBoxItem> は、<xref:System.Double> 値を表します。この値は、<xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Canvas.SetLeft%2A> メソッドが受け入れる引数の 1 つです。  <xref:System.Windows.Controls.ListBoxItem> を使用して <xref:System.Double> のインスタンスを表すためには、最初に <xref:System.Windows.Controls.ListBoxItem> を正しいデータ型に変換する必要があります。  
  
 [!code-xml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 ユーザーが <xref:System.Windows.Controls.ListBox> の選択項目を変更すると、`ChangeLeft` カスタム メソッドが呼び出されます。  このメソッドは <xref:System.Windows.Controls.ListBoxItem> を <xref:System.Windows.LengthConverter> オブジェクトに渡します。このオブジェクトは、<xref:System.Windows.Controls.ListBoxItem> の <xref:System.Windows.Controls.ContentControl.Content%2A> を <xref:System.Double> のインスタンスに変換します \(この値は、<xref:System.Windows.Controls.Control.ToString%2A> メソッドを使用して既に <xref:System.String> に変換されていることに注意してください\)。  この値は、`text1` オブジェクトの位置を変更するために、<xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Canvas.SetLeft%2A> メソッドと <xref:System.Windows.Controls.Canvas.GetLeft%2A> メソッドに渡されます。  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.Canvas>   
 <xref:System.Windows.Controls.ListBoxItem>   
 <xref:System.Windows.LengthConverter>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)