---
title: "Visual Basic と WPF のイベント処理 | Microsoft Docs"
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
  - "イベント ハンドラー, Visual Basic"
  - "Visual Basic, イベント ハンドラー"
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Visual Basic と WPF のイベント処理
[!INCLUDE[TLA#tla_visualbnet](../../../../includes/tlasharptla-visualbnet-md.md)] 言語の場合に限り、言語固有の `Handles` キーワードを使用すると、イベント ハンドラーを、属性に関連付けたり <xref:System.Windows.UIElement.AddHandler%2A> メソッドを使用したりする代わりに、インスタンスに関連付けることができます。  ただし、ハンドラーをインスタンスに関連付ける `Handles` 手法にはいくつかの制限もあります。`Handles` 構文でサポートできない [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント システムの特定の[ルーティング イベント](GTMT)機能が存在するためです。  
  
## WPF アプリケーションでの "ハンドル" の使用  
 `Handles` を使用してインスタンスおよびイベントに接続されるイベント ハンドラーは、すべてインスタンスの部分クラス宣言内で定義される必要があります。これは、要素の属性値を使用して割り当てられるイベント ハンドラーの要件でもあります。  `Handles` は、<xref:System.Windows.FrameworkContentElement.Name%2A> プロパティ値を持つ \(または [x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)が宣言された\) ページの要素に対してのみ指定できます。  これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の <xref:System.Windows.FrameworkContentElement.Name%2A> によって、`Handles` 構文で必要な *Instance.Event* 参照形式をサポートするために必要なインスタンス参照が作成されるためです。  <xref:System.Windows.FrameworkContentElement.Name%2A> 参照なしで `Handles` に使用できる要素は、部分クラスを定義するルート要素インスタンスだけです。  
  
 `Handles` の後の *Instance.Event* 参照をコンマで区切ることによって、1 つのハンドラーを複数の要素に割り当てることができます。  
  
 `Handles` を使用して、複数のハンドラーを 1 つの *Instance.Event* 参照に割り当てることができます。  ハンドラーが `Handles` 参照に指定される順序は重要ではありません。同じイベントを処理するハンドラーはどのような順序でも呼び出せることを想定する必要があります。  
  
 宣言内で `Handles` を使用して追加されたハンドラーを削除するには、<xref:System.Windows.UIElement.RemoveHandler%2A> を呼び出します。  
  
 `Handles` を使用して、[ルーティング イベント](GTMT)のハンドラーをアタッチすることができます。ただしその場合には、メンバー テーブルで処理されるイベントを定義するインスタンスにハンドラーをアタッチする必要があります。  [ルーティング イベント](GTMT)の場合、`Handles` を使用してアタッチされるハンドラーは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 属性としてアタッチされるハンドラーまたは <xref:System.Windows.UIElement.AddHandler%2A> の一般的なシグネチャにアタッチされるハンドラーの場合と同じルーティング規則に従います。  つまり、イベントが既に処理済みとしてマークされている場合 \(イベント データの <xref:System.Windows.RoutedEventArgs.Handled%2A> プロパティが `True` の場合\)、`Handles` を使用してアタッチされるハンドラーは、そのイベント インスタンスに応答して呼び出されることはありません。  イベントは、ルート内の別の要素のインスタンス ハンドラーによって処理済みとしてマークされるか、ルート上の現在の要素または前の要素のクラス処理によって処理済みとしてマークされます。  トンネル\/バブルのペアになったイベントをサポートする入力イベントの場合は、トンネル ルートがイベント ペアを処理済みとしてマークしていることがあります。  ルーティング イベントの詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
## ハンドラーの追加時の "ハンドル" の制限  
 `Handles` は、[添付イベント](GTMT)のハンドラーを参照できません。  その添付イベントの `add` アクセサー メソッドを使用するか、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で *typename.eventname* イベント属性を使用する必要があります。  詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
 [ルーティング イベント](GTMT)の場合、`Handles` を使用して、インスタンス メンバー テーブルのそのイベントが存在するインスタンスにハンドラーを割り当てることしかできません。  ただし、ルーティング イベントでは通常、親要素を子要素のイベントのリスナーにすることができます。これは、親要素のメンバー テーブルにそのイベントが存在しない場合でも可能です。  属性構文では、処理するイベントを実際に定義する型を修飾する *typename.membername* 属性形式を使用してこの指定を行うことができます。  たとえば、`Button.Click` の形式で属性ハンドラーを割り当てることで、\(`Clic`k イベントが定義されていない\) 親 `Page` がボタン クリック イベントをリッスンできるようになります。  ただし、`Handles` は競合する *Instance.Event* 形式をサポートする必要があるため、*typename.membername* 形式をサポートしません。  詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
 `Handles` は、既に処理済みとしてマークされているイベントに対して呼び出されるハンドラーをアタッチすることはできません。  代わりに、コードを使用して <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> の `handledEventsToo` オーバーロードを呼び出す必要があります。  
  
> [!NOTE]
>  XAML の同じイベントにイベント ハンドラーを指定するときに、[!INCLUDE[vb_current_short](../../../../includes/vb-current-short-md.md)] で `Handles` 構文を使用しないでください。  その場合、イベント ハンドラーが 2 回呼び出されます。  
  
## WPF での "ハンドル" 機能の実装方法  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ページのコンパイル時に、中間ファイルで、<xref:System.Windows.FrameworkContentElement.Name%2A> プロパティが設定されている \(または [x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md) が宣言されている\) ページのすべての要素への `Friend` `WithEvents` 参照が宣言されます。  それぞれの名前付きインスタンスは、`Handles` を使用してハンドラーに割り当てることができる要素になる可能性があります。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 内では、[!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] によって、要素がページの `Handles` 参照に使用できるようになったことを表示できます。  ただし、これには、中間ファイルですべての `Friends` 参照を設定できるように、1 つのコンパイル パスが必要になる場合があります。  
  
## 参照  
 <xref:System.Windows.UIElement.AddHandler%2A>   
 [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)