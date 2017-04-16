---
title: "方法 : 要素を名前で検索する | Microsoft Docs"
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
  - "要素, 検索 (名前で)"
  - "FindName メソッド"
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 要素を名前で検索する
<xref:System.Windows.FrameworkElement.FindName%2A> メソッドを使用して要素をその <xref:System.Windows.FrameworkElement.Name%2A> 値で検索する方法を次の例に示します。  
  
## 使用例  
 この例では、特定の要素をその名前で検索するメソッドを、ボタンのイベント ハンドラーとして作成しています。  `stackPanel` は、検索対象のルート <xref:System.Windows.FrameworkElement> の <xref:System.Windows.FrameworkElement.Name%2A> で、この例のメソッドは、見つかった要素を <xref:System.Windows.Controls.TextBlock> としてキャストし、<xref:System.Windows.Controls.TextBlock> で表示可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] プロパティの 1 つを変更することで、視覚的に示します。  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]