---
title: "方法 : FontSizeConverter クラスを使用する | Microsoft Docs"
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
  - "FontSizeConverter オブジェクト"
  - "タイポグラフィ, FontSizeConverter オブジェクト"
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : FontSizeConverter クラスを使用する
## 使用例  
 この例では、<xref:System.Windows.FontSizeConverter> のインスタンスを作成し、それを使用してフォント サイズを変更する方法を説明します。  
  
 この例では、`changeSize` という名前のカスタム メソッドを定義します。このメソッドは、別の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルで定義されている <xref:System.Windows.Controls.ListBoxItem> のコンテンツを、まず <xref:System.Double> のインスタンスに変換し、その後で <xref:System.String> に変換します。  このメソッドは <xref:System.Windows.Controls.ListBoxItem> を <xref:System.Windows.FontSizeConverter> オブジェクトに渡します。このオブジェクトは、<xref:System.Windows.Controls.ListBoxItem> の <xref:System.Windows.Controls.ContentControl.Content%2A> を <xref:System.Double> のインスタンスに変換します。  その後、この値は、<xref:System.Windows.Controls.TextBlock> 要素の <xref:System.Windows.Controls.TextBlock.FontSize%2A> プロパティの値として戻されます。  
  
 また、この例では、`changeFamily` という名前の第 2 のカスタム メソッドも定義されています。  このメソッドは、<xref:System.Windows.Controls.ListBoxItem> の <xref:System.Windows.Controls.ContentControl.Content%2A> を <xref:System.String> に変換した後、その値を <xref:System.Windows.Controls.TextBlock> 要素の <xref:System.Windows.Controls.TextBlock.FontFamily%2A> プロパティに渡します。  
  
 この例は実行できません。  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## 参照  
 <xref:System.Windows.FontSizeConverter>