---
title: "方法 : GridLengthConverter オブジェクトを作成および使用する | Microsoft Docs"
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
  - "グリッド コントロール, 作成, GridLengthConverter オブジェクト"
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : GridLengthConverter オブジェクトを作成および使用する
## 使用例  
 <xref:System.Windows.GridLengthConverter> のインスタンスを作成および使用する方法の例を次に示します。  この例では、`changeCol` というカスタム メソッドを定義します。このメソッドは <xref:System.Windows.Controls.ListBoxItem> を <xref:System.Windows.GridLengthConverter> に渡し、そこで <xref:System.Windows.Controls.ListBoxItem> の <xref:System.Windows.Controls.ContentControl.Content%2A> が <xref:System.Windows.GridLength> のインスタンスに変換されます。  変換された値は、<xref:System.Windows.Controls.ColumnDefinition> 要素の <xref:System.Windows.Controls.ColumnDefinition.Width%2A> プロパティの値として戻されます。  
  
 また、この例では、`changeColVal` という名前の第 2 のカスタム メソッドも定義されています。  このカスタム メソッドは、<xref:System.Windows.Controls.Slider> の <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> を <xref:System.String> に変換した後、その値を要素の <xref:System.Windows.Controls.ColumnDefinition.Width%2A> として <xref:System.Windows.Controls.ColumnDefinition> に返します。  
  
 <xref:System.Windows.Controls.ListBoxItem> のコンテンツは、別の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルで定義されます。  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## 参照  
 <xref:System.Windows.GridLengthConverter>   
 <xref:System.Windows.GridLength>