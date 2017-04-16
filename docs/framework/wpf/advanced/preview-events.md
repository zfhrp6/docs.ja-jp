---
title: "プレビュー イベント | Microsoft Docs"
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
  - "イベント, プレビュー"
  - "イベント, 非表示"
  - "プレビュー イベント"
  - "非表示イベント"
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# プレビュー イベント
プレビュー イベントはトンネル イベントとも呼ばれ、アプリケーション ルートから、イベントの発生元でありイベント データでソースとして報告される要素へ向かって経路をたどるルーティング イベントです。  すべてのイベント シナリオが、プレビュー イベントをサポートする、または必要とするわけではありません。このトピックでは、プレビュー イベントが存在する状況、アプリケーションまたはコンポーネントによるプレビュー イベントの処理方法、およびカスタム コンポーネントまたはカスタム クラスにプレビュー イベントを作成することが適切な状況について説明します。  
  
## プレビュー イベントと入力  
 一般に、Preview イベントを処理する場合、イベント データでイベントを処理済みとしてマークする際に注意が必要です。  Preview イベントを発生元 \(イベント データで発生元として報告される要素\) 以外の要素で処理すると、そのイベントを発生元の要素で処理する機会がなくなります。  このような状態が目的である場合もあります。複合コントロール内の要素間の場合などです。  
  
 特に入力イベントでは、Preview イベントは、イベント データのインスタンスを対のバブル イベントと共有もします。  Preview イベントのクラス ハンドラーを使用して入力イベントを処理済みとしてマークすると、そのバブル入力イベントのクラス ハンドラーは呼び出されません。  また、Preview イベントのインスタンス ハンドラーを使用してイベントを処理済みとしてマークすると、通常、そのバブル イベントのハンドラーは呼び出されません。  イベントが処理済みとしてマークされてもクラス ハンドラーまたはインスタンス ハンドラーが呼び出されるようにこれらを登録またはアタッチするオプションもありますが、この手法は一般には使用されません。  
  
 クラス処理、およびクラス処理と Preview イベントの関係性の詳細については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
### コントロールによるイベント抑制の回避  
 Preview イベントがよく使用されるシナリオの 1 つは、複合コントロールで入力イベントを処理する場合です。  コントロールの作成者は、特定のイベントがコントロールから生成されるのを抑制し、コンポーネントで定義された別のイベント \(より多くの情報を含むイベントや、より具体的な動作を表すイベント\) に置き換える場合もあります。  たとえば、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> は、<xref:System.Windows.Controls.Button> またはその複合要素によって発生する <xref:System.Windows.UIElement.MouseLeftButtonDown> および <xref:System.Windows.UIElement.MouseLeftButtonDown> バブル イベントを抑制し、マウスをキャプチャすることと、常にその <xref:System.Windows.Controls.Button> 自体で発生する <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを発生させることを優先します。  イベントおよびそのそのデータはルートに沿ったままですが、<xref:System.Windows.Controls.Button> においてイベント データが <xref:System.Windows.RoutedEventArgs.Handled%2A> としてマークされるので、`handledEventsToo` の場合に動作するように指定されているイベントのハンドラーのみが呼び出されます。  アプリケーションのルートに近い方の他の要素で、コントロールで抑制されたイベントをまた処理する必要がある場合、1 つの代替手段は、`handledEventsToo` を `true` として指定して、コードでハンドラーをアタッチすることです。  ただし通常は、ルーティング方向を変更して、入力イベントに対応する Preview になるように処理する方がより簡単です。  たとえば、コントロールで <xref:System.Windows.UIElement.MouseLeftButtonDown> を抑制する場合、代わりに、ハンドラーを <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> へアタッチしてみてください。  この方法が有効なのは、<xref:System.Windows.UIElement.MouseLeftButtonDown> のような基本要素入力イベントの場合のみです。  これらの入力イベントはトンネル\/バブルのペアを使用し、両方のイベントを発生させ、イベント データを共有します。  
  
 これらの方法には、それぞれ悪影響や制限事項があります。  Preview イベントを処理する場合の悪影響は、その時点でイベントを処理すると、バブル イベントを処理するハンドラーが無効になる可能性がある点です。したがって、通常は、イベント ルートの Preview 部分で処理された時点ではまだ、イベントを処理済みとしてマークしない方がよいという点が制限となります。  `handledEventsToo` 手法の制限は、`handledEventsToo` ハンドラーは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で属性として指定できない点です。このようなイベント ハンドラーは、アタッチ対象の要素へのオブジェクト参照を取得してからコードを使用して登録する必要があります。  
  
## 参照  
 [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)