---
title: "方法 : ContextMenuOpening イベントを処理する | Microsoft Docs"
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
  - "ContextMenuOpening イベント"
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : ContextMenuOpening イベントを処理する
イベント データの <xref:System.Windows.RoutedEventArgs.Handled%2A> プロパティを `true` に設定すると、アプリケーション内で <xref:System.Windows.FrameworkElement.ContextMenuOpening> イベントを処理することによって、既存のコンテキスト メニューを表示前に調整したり、表示されないようにしたりすることができます。  一般に、イベント データの <xref:System.Windows.RoutedEventArgs.Handled%2A> を `true` に設定するのは、メニュー全体を新しい <xref:System.Windows.Controls.ContextMenu> オブジェクトに置き換えるために行い、これには操作の取り消しと新しいオープン操作の開始が必要になることがあります。  <xref:System.Windows.FrameworkElement.ContextMenuOpening> イベントのハンドラーを作成する場合、<xref:System.Windows.Controls.ContextMenu> コントロールと、コントロール全般のコンテキスト メニューのオープンと配置に応答するサービスとの間のタイミングの問題について理解している必要があります。  このトピックでは、コンテキスト メニューのさまざまな開き方に対応するコード テクニックを示し、タイミングの問題が関係する状況について説明します。  
  
 <xref:System.Windows.FrameworkElement.ContextMenuOpening> イベントの処理には、次のようなシナリオがあります。  
  
-   表示前にメニュー項目を調整する。  
  
-   表示前にメニュー全体を置き換える。  
  
-   既存のどのコンテキスト メニューも表示されないようにする。  
  
## 使用例  
  
## 表示前にメニュー項目を調整する  
 既存のメニュー項目の調整は比較的単純で、最も一般的なシナリオです。  アプリケーションの現在の状態の情報や、コンテキスト メニューの対象となるオブジェクトのプロパティとして取得される特定の状態情報に応じて、コンテキスト メニューのオプションを増減する場合に行います。  
  
 一般的な方法は、まずイベントのソース \(右クリックされた特定のコントロール\) を取得し、そのソースの <xref:System.Windows.FrameworkElement.ContextMenu%2A> プロパティを取得する方法です。  通常、<xref:System.Windows.Controls.ItemsControl.Items%2A> コレクションを調べてコンテキスト メニュー内にどのメニュー項目が既に存在するかを確認し、このコレクションに適切な新しいメニュー項目 <xref:System.Windows.Controls.MenuItem> を追加するか、このコレクションからメニュー項目を削除します。  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## 表示前にメニュー全体を置き換える  
 もう 1 つのシナリオは、コンテキスト メニュー全体を置き換える場合です。  もちろん、前の方法を応用して、既存のコンテキスト メニューからすべてのメニュー項目を削除し、新しいメニュー項目を項目 0 から順に追加することもできます。  しかし、コンテキスト メニューのすべての項目を置き換えるよりわかりやすい方法は、新しい <xref:System.Windows.Controls.ContextMenu> を作成してこれに新しい項目を追加してから、コントロールの <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName> プロパティを、作成した新しい <xref:System.Windows.Controls.ContextMenu> になるように設定することです。  
  
 次のコードは、<xref:System.Windows.Controls.ContextMenu> を置き換える単純なハンドラーのコードです。  このコードで参照しているカスタムの `BuildMenu` メソッドが分離されているのは、複数のサンプル ハンドラーからこれを呼び出すためです。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 ただし、この手法を <xref:System.Windows.FrameworkElement.ContextMenuOpening> のハンドラーに適用する場合は、<xref:System.Windows.Controls.ContextMenu> を設定するオブジェクトに既存のコンテキスト メニューが存在しないと、タイミングの問題が発生することがあります。  ユーザーがコントロールを右クリックすると、既存の <xref:System.Windows.Controls.ContextMenu> が空または null の場合も <xref:System.Windows.FrameworkElement.ContextMenuOpening> が発生します。  しかし、このような場合は、ソース要素に設定した新しい <xref:System.Windows.Controls.ContextMenu> の取得が遅れるので、表示に間に合いません。  また、ユーザーがここで再度右クリックすると、今度は新しい <xref:System.Windows.Controls.ContextMenu> が表示され、値は null でなくなり、ハンドラーの 2 回目の実行でメニューが正しく置き換えられて表示されます。  これを回避するには、次の 2 つの方法が考えられます。  
  
1.  <xref:System.Windows.FrameworkElement.ContextMenuOpening> ハンドラーが実行されるコントロールには常に <xref:System.Windows.Controls.ContextMenu> のプレースホルダーが少なくとも 1 個存在するようにし、このプレースホルダーをハンドラー コードで置き換えます。  この場合、前の例のハンドラーを使用できますが、通常は、最初のマークアップでプレースホルダー <xref:System.Windows.Controls.ContextMenu> を割り当てる必要があります。  
  
     [!code-xml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  事前のロジックに基づいて、<xref:System.Windows.Controls.ContextMenu> の初期値が null である場合を想定します。  <xref:System.Windows.Controls.ContextMenu> が null であるかを調べることもでき、また、ハンドラーが少なくとも 1 回は実行されているかどうかを示すフラグをコード内で使用するという方法もあります。  <xref:System.Windows.Controls.ContextMenu> が表示されるものと想定した場合、ハンドラーでイベント データの <xref:System.Windows.RoutedEventArgs.Handled%2A> を `true` に設定します。  コンテキスト メニューの表示に応答する <xref:System.Windows.Controls.ContextMenuService> に対し、イベント データの <xref:System.Windows.RoutedEventArgs.Handled%2A> の値 `true` は、そのイベントを発生させたコンテキスト メニューおよびコントロールの組み合わせの表示取り消し要求を表します。  
  
 これで、問題のありそうなコンテキスト メニューは表示しないようにしたので、次は、新しいコンテキスト メニューを設定してそれを表示します。  新しいコンテキスト メニューの設定は、基本的には前のハンドラーと同じです。新しい <xref:System.Windows.Controls.ContextMenu> を作成し、コントロールのソースの <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName> プロパティに設定します。  この場合、最初の表示処理を取り消しているので、新しいコンテキスト メニューを強制的に表示する追加手順が必要になります。  強制的に表示するには、ハンドラー内で <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=fullName> プロパティを `true` に設定します。  この場合、ハンドラー内でコンテキスト メニューを開くと <xref:System.Windows.FrameworkElement.ContextMenuOpening> イベントが再度発生することになるので、注意が必要です。  ハンドラーに再入すると無限再帰を引き起こします。  <xref:System.Windows.FrameworkElement.ContextMenuOpening> イベント ハンドラー内からコンテキスト メニューを開く場合に必ず、`null` かどうかを調べたり、フラグを使用したりする必要があるのはこのためです。  
  
## 既存のどのコンテキスト メニューも表示されないようにする  
 メニューを一切表示しないようにするハンドラーの作成という最後のシナリオは、一般的ではありません。  あるコントロールでコンテキスト メニューを表示しないようにする場合、ユーザーが要求したときにそのメニューが表示されないようにするよりも他に適切な方法があると考えられます。  それでも、ハンドラーを使用してコンテキスト メニューが一切表示されないようにする場合は、ハンドラーでイベント データの <xref:System.Windows.RoutedEventArgs.Handled%2A> を `true` に設定するだけでできます。  コンテキスト メニューの表示に応答する <xref:System.Windows.Controls.ContextMenuService> は、コントロールに関して発生したイベントのイベント データを調べます。  いずれかの時点でそのイベントの <xref:System.Windows.RoutedEventArgs.Handled%2A> がオンになっていた場合、そのイベントを発生させたコンテキスト メニューのオープン操作は抑制されます。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## 参照  
 <xref:System.Windows.Controls.ContextMenu>   
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName>   
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [ContextMenu の概要](../../../../docs/framework/wpf/controls/contextmenu-overview.md)