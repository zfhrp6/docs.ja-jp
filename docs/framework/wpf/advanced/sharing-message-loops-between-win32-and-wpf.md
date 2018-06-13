---
title: Win32 と WPF 間でのメッセージ ループの共有
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 35a908cc26e6b70c9acd8732521837f2b20eaf5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548816"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Win32 と WPF 間でのメッセージ ループの共有
このトピックとの相互運用のメッセージ ループを実装する方法について説明[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、既存を使用していずれかのメッセージ ループ危険にさらされる<xref:System.Windows.Threading.Dispatcher>または上に個別のメッセージ ループを作成することで、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]面を相互運用コード。  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher とメッセージ ループ  
 相互運用とキーボード イベントのサポートについては、通常のシナリオは、実装する<xref:System.Windows.Interop.IKeyboardInputSink>、または既にを実装するクラスからサブクラスを作成する<xref:System.Windows.Interop.IKeyboardInputSink>など<xref:System.Windows.Interop.HwndSource>または<xref:System.Windows.Interop.HwndHost>です。 ただし、キーボード シンクのサポートでは、相互運用の境界を越えてメッセージを送受信するときにする必要がありますすべてのメッセージ ループの要件は対処できません。 アプリケーション メッセージ ループのアーキテクチャを形式化する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供、<xref:System.Windows.Interop.ComponentDispatcher>クラスは、次に、メッセージ ループの単純なプロトコルを定義します。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> いくつかのメンバーを公開する静的クラスです。 各メソッドのスコープは暗黙的に呼び出し元のスレッドに関連付けられています。 メッセージ ループは、その中の一部を呼び出す必要があります[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)](として、次のセクションで定義) の重要な時間帯にします。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> その他のコンポーネント (など、キーボード シンク) がリッスンできるイベントを提供します。 <xref:System.Windows.Threading.Dispatcher>クラスの適切なすべての呼び出し<xref:System.Windows.Interop.ComponentDispatcher>適切な順序のメソッドです。 独自のメッセージ ループを実装している場合は、コードを呼び出す<xref:System.Windows.Interop.ComponentDispatcher>メソッドと同様にします。  
  
 呼び出す<xref:System.Windows.Interop.ComponentDispatcher>メソッドのスレッドでそのスレッドで登録されたイベント ハンドラーを呼び出すだけです。  
  
## <a name="writing-message-loops"></a>メッセージ ループの記述  
 次のチェックリストは、<xref:System.Windows.Interop.ComponentDispatcher>独自のメッセージ ループを記述する場合に使用するメンバー。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: メッセージ ループは、このスレッドがモーダルであることを示すを呼び出す必要があります。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: メッセージ ループには、このスレッドが nonmodal を元に戻すことを示すために呼び出す必要があります。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: メッセージ ループがあることを示すこのを呼び出す必要があります<xref:System.Windows.Interop.ComponentDispatcher>を発生させる、<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>イベント。 <xref:System.Windows.Interop.ComponentDispatcher> 生成しませんが、<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>場合<xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>は`true`を呼び出すメッセージ ループもかまいませんが、<xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>場合でも<xref:System.Windows.Interop.ComponentDispatcher>モーダルの状態のときに応答できません。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: メッセージ ループは、新しいメッセージが使用できることを示すためにこれを呼び出す必要があります。 戻り値を示しますリスナーがあるかどうか、<xref:System.Windows.Interop.ComponentDispatcher>イベントは、メッセージを処理します。 場合<xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>返します`true`(処理)、ディスパッチャーは何もさらに、メッセージを使用します。 場合は、戻り値は`false`、ディスパッチャーの呼び出しが予期されて、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数`TranslateMessage`、まず`DispatchMessage`です。  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>ComponentDispatcher を使用して、既存のメッセージの処理  
 次のチェックリストは、<xref:System.Windows.Interop.ComponentDispatcher>固有に依存する場合に使用するメンバー[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ ループします。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: アプリケーションをモーダルになったかどうかを返します (モーダル メッセージ ループのプッシュなど)。 <xref:System.Windows.Interop.ComponentDispatcher> クラスの数を保持しているために、この状態を追跡できます<xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>と<xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>メッセージ ループからの呼び出しです。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> および<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>イベント デリゲートの呼び出しの標準的な規則に従います。 不特定の順序でデリゲートが呼び出され、処理済みとして、最初の 1 つがメッセージをマークした場合でも、すべてのデリゲートが呼び出されます。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: アイドル プロセスを実行するには適切で効率的な期間を示します (その他の保留中のメッセージ、スレッドはありません)。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 発生しません。 スレッドがモーダルの場合。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: メッセージ ポンプを処理するすべてのメッセージに対して発生します。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: 中に処理されていないすべてのメッセージに対して発生<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>です。  
  
 メッセージと見なされますの後に処理される場合、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>イベントまたは<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>イベントを`handled`イベント データの参照によって渡されたパラメーターが`true`です。 場合、イベント ハンドラーは、メッセージを無視する必要があります`handled`は`true`別のハンドラーが最初にメッセージを処理するため、します。 両方のイベントをイベント ハンドラーは、メッセージを変更することができます。 変更したメッセージと元変更されていないメッセージではなく、ディスパッチャーをディスパッチする必要があります。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> すべてのリスナーがアーキテクチャの意図に配信されるトップレベル ウィンドウのみが対象となるメッセージをメッセージに応答コードを呼び出す必要がある HWND を含むことです。  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource が ComponentDispatcher イベントを処理する方法  
 場合、 <xref:System.Windows.Interop.HwndSource> (親のない HWND)、トップレベル ウィンドウが登録されます<xref:System.Windows.Interop.ComponentDispatcher>です。 場合<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>発生するのメッセージを使用する場合と、<xref:System.Windows.Interop.HwndSource>または、子ウィンドウ<xref:System.Windows.Interop.HwndSource>呼び出しその<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>、 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>、<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>キーボード シンクのシーケンス。  
  
 場合、<xref:System.Windows.Interop.HwndSource>トップレベル ウィンドウ (HWND である親を持つ) は行われません処理ではありません。 トップ レベル ウィンドウのみが、処理を行う必要がありますはどのような相互運用のシナリオの一部として上位レベルのウィンドウのキーボード シンクのサポートを有効にする必要.  
  
 場合<xref:System.Windows.Interop.HwndHost.WndProc%2A>上、<xref:System.Windows.Interop.HwndSource>が呼び出された最初に呼び出される適切なキーボード シンク メソッドを使用しないで、アプリケーションは、イベントを受信より高いレベルのキーボードなど<xref:System.Windows.UIElement.KeyDown>です。 ただし、キーボード シンク メソッドは呼び出されません、アクセス キーのサポートなどの適切なキーボード入力モデル機能を回避します。 これは、メッセージ ループでは正常に関連するスレッド上に通知されないしなかったために発生する可能性があります、 <xref:System.Windows.Interop.ComponentDispatcher>、または親 HWND が適切なキーボード シンク応答を呼び出せませんでした。  
  
 使用してそのメッセージのフック関数を追加した場合、キーボード シンクに移動するメッセージを HWND を送信できません可能性があります、<xref:System.Windows.Interop.HwndSource.AddHook%2A>メソッドです。 直接および not に送信されるメッセージ ポンプ レベルでメッセージが処理される可能性がありますが、`DispatchMessage`関数。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Interop.ComponentDispatcher>  
 <xref:System.Windows.Interop.IKeyboardInputSink>  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)
