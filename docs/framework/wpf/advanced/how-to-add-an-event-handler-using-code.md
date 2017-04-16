---
title: "方法 : コードを使用してイベント ハンドラーを追加する | Microsoft Docs"
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
  - "イベント ハンドラー, 追加"
  - "XAML, 追加 (イベント ハンドラーを)"
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : コードを使用してイベント ハンドラーを追加する
コードを使用して要素にイベント ハンドラーを追加する方法を次の例に示します。  
  
 イベント ハンドラーを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 要素に追加する際に、その要素を含むマークアップ ページが既に読み込まれている場合は、コードを使用してハンドラーを追加する必要があります。  また、コードのみを使用してアプリケーションの要素ツリーを構築し、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して要素の宣言をしない場合は、特定のメソッドを呼び出して、構築された要素ツリーにイベント ハンドラーを追加することができます。  
  
## 使用例  
 最初に定義した既存のページに、新しい <xref:System.Windows.Controls.Button> を追加する [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] での例を次に示します。  分離コード ファイルはイベント ハンドラー メソッドを実装し、そのメソッドを新しいイベント ハンドラーとして <xref:System.Windows.Controls.Button> に追加します。  
  
 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] の例では、`+=` 演算子を使用してイベントにハンドラーを割り当てます。  これは、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] のイベント処理モデルでハンドラーを割り当てる際に使用する演算子と同じです。  [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] では、イベント ハンドラーを追加する手段としてこの演算子はサポートされていません。  代わりに、次の 2 つの手法のいずれかを使用する必要があります。  
  
-   <xref:System.Windows.UIElement.AddHandler%2A> メソッドを `AddressOf` 演算子と共に使用して、イベント ハンドラー実装を参照します。  
  
-   イベント ハンドラー定義の一部として `Handles` キーワードを使用します。  この方法はここでは説明しません。「[Visual Basic と WPF のイベント処理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
 [!code-xml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  最初に解析した [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページでイベント ハンドラーを追加すると、非常に簡単です。  イベント ハンドラーを追加するオブジェクト要素内で、処理するイベント名と一致する属性を追加します。  次に、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページの分離コード ファイルで定義したイベント ハンドラー メソッドの名前として、その属性の値を指定します。  詳細については、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」または「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
## 参照  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)