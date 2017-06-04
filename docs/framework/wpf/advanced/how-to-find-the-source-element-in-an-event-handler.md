---
title: "方法 : イベント ハンドラーでソース要素を検索する | Microsoft Docs"
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
  - "イベント ハンドラー, 検索 (ソース要素を)"
  - "ソース要素 (イベント ハンドラー内の)"
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : イベント ハンドラーでソース要素を検索する
この例では、イベント ハンドラーの中でソース要素を見つける方法を示します。  
  
## 使用例  
 次の例に示す、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーは、分離コード ファイルの中で宣言されているものです。  ハンドラーが結び付けられているボタンをユーザーがクリックすると、ハンドラーによってプロパティ値が変更されます。  ハンドラー コードは、イベント引数として報告されたルーティング イベント データの <xref:System.Windows.RoutedEventArgs.Source%2A> プロパティを使用して、<xref:System.Windows.RoutedEventArgs.Source%2A> 要素の <xref:System.Windows.FrameworkElement.Width%2A> プロパティの値を変更します。  
  
 [!code-xml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## 参照  
 <xref:System.Windows.RoutedEventArgs>   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)