---
title: "Win32 と WPF 間でのメッセージ ループの共有 | Microsoft Docs"
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
  - "相互運用性 [WPF], Win32"
  - "メッセージ ループ [WPF]"
  - "共有 (メッセージ ループを)"
  - "Win32 コード, 共有 (メッセージ ループを)"
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Win32 と WPF 間でのメッセージ ループの共有
ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] と相互運用するようにメッセージ ループを実装する方法について説明します。<xref:System.Windows.Threading.Dispatcher> で公開されている既存のメッセージ ループを使用する方法と、相互運用コードの [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 側で別のメッセージ ループを作成する方法があります。  
  
## ComponentDispatcher とメッセージ ループ  
 相互運用とキーボード イベント サポートの一般的なシナリオでは、<xref:System.Windows.Interop.IKeyboardInputSink> を実装するか、<xref:System.Windows.Interop.IKeyboardInputSink> を既に実装している <xref:System.Windows.Interop.HwndSource> や <xref:System.Windows.Interop.HwndHost> などのクラスからサブクラス化します。  しかし、キーボード シンク サポートは、相互運用の境界にまたがるメッセージ送受信時のメッセージ ループの要件のすべてに対応しているとは限りません。  アプリケーションのメッセージ ループ アーキテクチャの形式化を支援するために、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、メッセージ ループが従う単純なプロトコルを定義する <xref:System.Windows.Interop.ComponentDispatcher> クラスが用意されています。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> は、複数のメンバーを公開する静的クラスです。  各メソッドのスコープは、呼び出し元のスレッドに暗黙的に関連付けられます。  メッセージ ループでは、重要な局面 \(次のセクションで定義されています\) で、それらの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] のいくつかを呼び出す必要があります。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> から提供されるイベントは、他のコンポーネント \(キーボード シンクなど\) でリッスンできます。  <xref:System.Windows.Threading.Dispatcher> クラスは、すべての適切な <xref:System.Windows.Interop.ComponentDispatcher> メソッドを適切な順序で呼び出します。  独自のメッセージ ループを実装する場合は、コードで同様に <xref:System.Windows.Interop.ComponentDispatcher> メソッドを呼び出す必要があります。  
  
 スレッドで <xref:System.Windows.Interop.ComponentDispatcher> メソッドを呼び出すと、そのスレッドに登録されたイベント ハンドラーだけが呼び出されます。  
  
## メッセージ ループの記述  
 独自のメッセージ ループを記述する場合に使用する <xref:System.Windows.Interop.ComponentDispatcher> メンバーのチェック リストを次に示します。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: 独自のメッセージ ループで、スレッドがモーダルであることを示す際に呼び出す必要があります。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: 独自のメッセージ ループで、スレッドがモーダルでなくなったことを示す際に呼び出す必要があります。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: 独自のメッセージ ループで、<xref:System.Windows.Interop.ComponentDispatcher> が <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> イベントを発生させる必要があることを示す際に呼び出す必要があります。  <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> が `true` の場合、<xref:System.Windows.Interop.ComponentDispatcher> は <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> を発生させません。しかし、モーダル状態であるために <xref:System.Windows.Interop.ComponentDispatcher> が応答できない場合でも、メッセージ ループは <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> を呼び出すことができます。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: 独自のメッセージ ループで、新しいメッセージが使用できることを示す際に呼び出す必要があります。  戻り値は、<xref:System.Windows.Interop.ComponentDispatcher> イベントのリスナーによってメッセージが処理されたかどうかを示します。  <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> が `true` \(処理済み\) を返す場合、ディスパッチャーはそのメッセージをこれ以上処理する必要がありません。  戻り値が `false` の場合、ディスパッチャーは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 関数 `TranslateMessage` を呼び出し、次に `DispatchMessage` を呼び出します。  
  
## ComponentDispatcher と既存のメッセージ処理の使用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既存のメッセージ ループを利用する場合に使用する <xref:System.Windows.Interop.ComponentDispatcher> メンバーのチェックリストを次に示します。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: アプリケーションがモーダルになったかどうか \(モーダル メッセージ ループがプッシュされたなど\) を返します。  <xref:System.Windows.Interop.ComponentDispatcher> は、メッセージ ループからの <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> 呼び出しと <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> 呼び出しの回数を保持するため、この状態を追跡できます。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> イベントと <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> イベントは、デリゲート呼び出しの標準規則に従います。  デリゲートは不特定の順番で呼び出され、最初のデリゲートがメッセージを処理済みとしてマークしても、すべてのデリゲートが呼び出されます。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: アイドル処理を行うのに適切かつ効率的なタイミング \(保留状態の他のメッセージがスレッドに存在しない\) を示します。  スレッドがモーダルの場合、<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> は発生しません。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: メッセージ ポンプが処理するすべてのメッセージに対して発生します。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> の間に処理されなかったすべてのメッセージに対して発生します。  
  
 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> イベントまたは <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> イベントの後に参照渡しされる、イベント データの `handled` パラメーターが `true` の場合、メッセージは処理済みであると見なされます。  `handled` が `true` の場合は、他のイベント ハンドラーが先にそのメッセージを処理したことを意味するため、ハンドラーはそのメッセージを無視する必要があります。  どちらのイベントに対するイベント ハンドラーも、メッセージを変更する可能性があります。  ディスパッチャーは、変更前の元のメッセージではなく、変更後のメッセージをディスパッチする必要があります。  <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> はすべてのリスナーに配信されます。ただし、アーキテクチャでは、メッセージの対象の HWND を含むトップレベルのウィンドウだけがメッセージに応じてコードを呼び出すことが意図されています。  
  
## HwndSource による ComponentDispatcher イベントの処理方法  
 <xref:System.Windows.Interop.HwndSource> は、トップレベルのウィンドウである \(親 HWND を持たない\) 場合、<xref:System.Windows.Interop.ComponentDispatcher> に登録されます。  <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> が発生し、そのメッセージの対象が <xref:System.Windows.Interop.HwndSource> または子ウィンドウの場合、<xref:System.Windows.Interop.HwndSource> はその <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>、<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>、<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> のキーボード シンク シーケンスを呼び出します。  
  
 <xref:System.Windows.Interop.HwndSource> がトップレベルのウィンドウではない \(親 HWND を持つ\) 場合、処理は行われません。  トップレベルのウィンドウだけが処理の実行を求められます。また、どのようなシナリオの相互運用でも、キーボード シンクをサポートするトップレベルのウィンドウが存在することが求められます。  
  
 適切なキーボード シンク メソッドが先に呼び出されずに <xref:System.Windows.Interop.HwndHost.WndProc%2A> が <xref:System.Windows.Interop.HwndSource> に対して呼び出された場合、アプリケーションは <xref:System.Windows.UIElement.KeyDown> などの上位のキーボード イベントを受け取ります。  ただし、キーボード シンク メソッドは呼び出されません。これにより、アクセス キー サポートなどの適切なキーボード入力モデルが迂回されます。  メッセージ ループが <xref:System.Windows.Interop.ComponentDispatcher> の適切なスレッドへの通知を正しく行わなかった場合、または親 HWND が正しいキーボード シンク応答を呼び出さなかった場合に、これが発生することがあります。  
  
 キーボード シンクに送られるメッセージに <xref:System.Windows.Interop.HwndSource.AddHook%2A> を使用してフックを追加した場合、このメッセージは HWND に送信されないことがあります。  このメッセージは、メッセージ パンプ レベルで直接処理され、`DispatchMessage` 関数に送信されないことがあります。  
  
## 参照  
 <xref:System.Windows.Interop.ComponentDispatcher>   
 <xref:System.Windows.Interop.IKeyboardInputSink>   
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)   
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)