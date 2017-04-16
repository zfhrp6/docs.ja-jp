---
title: "方法 : LINQ クエリの結果にバインドする | Microsoft Docs"
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
  - "バインド (LINQ クエリの結果に) [WPF]"
  - "実行 (LINQ クエリを) [WPF], バインド (結果に)"
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : LINQ クエリの結果にバインドする
この例では、LINQ クエリを実行し、その結果にバインドする方法について説明します。  
  
## 使用例  
 次の例では、2 つのリスト ボックスを作成します。  最初のリスト ボックスには 3 つのリスト項目が含まれます。  
  
 [!code-xml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 最初のリスト ボックスから項目を選択すると、次のイベント ハンドラーが呼び出されます。  この例では、`Tasks` は `Task` オブジェクトのコレクションです。  `Task` クラスには、`Priority` という名前のプロパティがあります。  このイベント ハンドラーは、優先順位値が選択された `Task` オブジェクトのコレクションを返す LINQ クエリを実行し、それを <xref:System.Windows.FrameworkElement.DataContext%2A> として設定します。  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 2 つ目のリスト ボックスは、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 値が `{Binding}` に設定されているため、そのコレクションにバインドされます。  その結果、返されたコレクションが `myTaskTemplate` <xref:System.Windows.DataTemplate> に基づいて表示されます。  
  
## 参照  
 [XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)   
 [コレクションにバインドして選択に基づく情報を表示する](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)   
 [WPF Version 4.5 の新機能](../../../../docs/framework/wpf/getting-started/whats-new.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)