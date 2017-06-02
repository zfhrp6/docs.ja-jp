---
title: "方法 : ルーティング イベントを処理する | Microsoft Docs"
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
  - "バブル イベント"
  - "ルーティング イベント, 処理"
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 方法 : ルーティング イベントを処理する
[バブル](GTMT) イベントの動作と、[ルーティング イベント](GTMT) データを処理できるハンドラーを作成する方法を次の例に示します。  
  
## 使用例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、要素は、[要素ツリー](GTMT)構造体に配置されます。  親要素は、要素ツリー内で最初に子要素が発生させたイベントの処理に参加できます。  これは、[イベント ルーティング](GTMT)により可能です。  
  
 ルーティング イベントは通常、[バブル](GTMT)または[トンネル](GTMT)の 2 つのルーティング方法のいずれかに従います。  この例では、[バブル](GTMT) イベントに焦点を当て、<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=fullName> イベントを使用してルーティングの動作を示します。  
  
 次の例では、2 つの <xref:System.Windows.Controls.Button> コントロールを作成し、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 属性構文を使用してイベント ハンドラーを共通の親要素 \(この例では <xref:System.Windows.Controls.StackPanel>\) にアタッチします。  この例では、各 <xref:System.Windows.Controls.Button> 子要素の個々のイベント ハンドラーをアタッチするのではなく、属性構文を使用してイベント ハンドラーを <xref:System.Windows.Controls.StackPanel> 親要素にアタッチします。  このイベント処理パターンは、ハンドラーがアタッチされる要素の数を減らすための手法としてイベント ルーティングを使用する方法を示します。  各 <xref:System.Windows.Controls.Button> のすべての[バブル](GTMT) イベントが親要素を通じてルーティングされます。  
  
 親 <xref:System.Windows.Controls.StackPanel> 要素では、属性として指定された <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント名は、<xref:System.Windows.Controls.Button> クラスに名前を付けて部分的に修飾されます。  <xref:System.Windows.Controls.Button> クラスは、そのメンバーの一覧に <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを持つ <xref:System.Windows.Controls.Primitives.ButtonBase> 派生クラスです。  イベント ハンドラーをアタッチするためのこの部分修飾手法が必要になるのは、ルーティング イベント ハンドラーがアタッチされる要素のメンバー一覧に、処理されているイベントが存在しない場合です。  
  
 [!code-xml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを処理する例を次に示します。  この例では、イベントを処理する要素とイベントを発生させる要素を報告します。  ユーザーがいずれかのボタンをクリックすると、イベント ハンドラーが実行されます。  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## 参照  
 <xref:System.Windows.RoutedEvent>   
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)   
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)