---
title: "方法 : ThicknessConverter オブジェクトを使用する | Microsoft Docs"
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
  - "境界線の太さ"
  - "ThicknessConverter オブジェクト"
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ThicknessConverter オブジェクトを使用する
## 使用例  
 この例では、<xref:System.Windows.ThicknessConverter> のインスタンスを作成し、それを使用して境界線の太さを変更する方法を説明します。  
  
 この例では、`changeThickness` という名前のカスタム メソッドを定義します。このメソッドは、まず別の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルで定義されている <xref:System.Windows.Controls.ListBoxItem> のコンテンツを <xref:System.Windows.Thickness> のインスタンスに変換し、次にそのコンテンツを <xref:System.String> に変換します。  このメソッドは、<xref:System.Windows.Controls.ListBoxItem> を <xref:System.Windows.ThicknessConverter> オブジェクトに渡します。このオブジェクトは、<xref:System.Windows.Controls.ListBoxItem> の <xref:System.Windows.Controls.ContentControl.Content%2A> を <xref:System.Windows.Thickness> のインスタンスに変換します。  その後、この値は、<xref:System.Windows.Controls.Border> の <xref:System.Windows.Controls.Border.BorderThickness%2A> プロパティの値として戻されます。  
  
 この例は実行できません。  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## 参照  
 <xref:System.Windows.Thickness>   
 <xref:System.Windows.ThicknessConverter>   
 <xref:System.Windows.Controls.Border>   
 [How to: Change the Margin Property](http://msdn.microsoft.com/ja-jp/8a313efd-5f99-4097-b4c1-8fa49d8379a2)   
 [How to: Convert a ListBoxItem to a new Data Type](http://msdn.microsoft.com/ja-jp/7a080b88-184e-4b27-bb61-d42bafba9727)   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)