---
title: "チュートリアル: WPF での Win32 コントロールのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 566be72cf330f6da83987f5e693176552471f091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>チュートリアル: WPF での Win32 コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただしがある場合、かなりの投資[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]コードである可能性がありますには、少なくともを再利用すると効率的では、そのコードの一部、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]完全に修正するのではなくアプリケーションです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホストするための簡単なメカニズムを提供、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  ウィンドウで、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。  
  
 このトピックを紹介アプリケーション、 [WPF サンプルでは Win32 ListBox コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=159998)、そのホスト、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]リスト ボックス コントロールです。 この一般的な手順は、いずれかのホストに拡張できます[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウです。  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>要件  
 このトピックは、両方の基礎知識を前提と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プログラミングします。 基本的な概要については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングを参照してください[作業の開始](../../../../docs/framework/wpf/getting-started/index.md)です。 概要については[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プログラミングでは、参照してください、多数の書籍を受け、特に*プログラミング Windows* Charles Petzold でします。  
  
 このトピックに付属するサンプルが実装されているため[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]、それを利用[!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)]にアクセスする、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)][!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]です。 ある程度[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]は便利ですが必須ではありません。  
  
> [!NOTE]
>  このトピックには、関連するサンプルのコード例の数が含まれます。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 取得するか、完全なコードを閲覧[WPF サンプルでは Win32 ListBox コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=159998)です。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本手順  
 ホストするための基本的な手順を概説する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]上のウィンドウ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 残りのセクションでは、各ステップの詳細を通過します。  
  
 基本的なホスティング手順です。  
  
1.  実装する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウをホストするページ。 1 つの方法は、<xref:System.Windows.Controls.Border>にホストされているウィンドウのページのセクションを予約する要素。  
  
2.  継承されるコントロールをホストするクラスを実装する<xref:System.Windows.Interop.HwndHost>です。  
  
3.  そのクラスでは、オーバーライド、<xref:System.Windows.Interop.HwndHost>クラス メンバー<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>です。  
  
4.  含むウィンドウの子としてホストされているウィンドウを作成、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 従来は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングが明示的に作成する必要はありませんそれを使用する、ホストのページは、ウィンドウ ハンドル (HWND) を使用します。 HWND ページが表示されるを通じて、`hwndParent`のパラメーター、<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>メソッドです。 この HWND の子としてホストされているウィンドウを作成する必要があります。  
  
5.  ホスト ウィンドウを作成した後は、ホストされたウィンドウの HWND を返します。 1 つまたは複数をホストする場合[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コントロール、通常、HWND の子としてホスト ウィンドウを作成してそのホスト ウィンドウのコントロールの子を作成します。 ホスト ウィンドウにコントロールをラップする簡単な方法を提供、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]いくつかの特定と、コントロールから通知を受け取るページ[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]HWND の境界を越えて通知に関する問題です。  
  
6.  子コントロールからの通知など、ホスト ウィンドウに送信された選択したメッセージを処理します。 これには、2 つの方法があります。  
  
    -   ホストするクラスでメッセージを処理する場合は、上書き、<xref:System.Windows.Interop.HwndHost.WndProc%2A>のメソッド、<xref:System.Windows.Interop.HwndHost>クラスです。  
  
    -   たい場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、メッセージの処理、処理、<xref:System.Windows.Interop.HwndHost>クラス<xref:System.Windows.Interop.HwndHost.MessageHook>分離コードでイベント。 このイベントは、ホストされているウィンドウによって受信されるすべてのメッセージに対して発生します。 まだをオーバーライドする必要がある場合、このオプションを選択すると、 <xref:System.Windows.Interop.HwndHost.WndProc%2A>、最小限の実装のみ必要があります。  
  
7.  上書き、<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>と<xref:System.Windows.Interop.HwndHost.WndProc%2A>のメソッド<xref:System.Windows.Interop.HwndHost>です。 満たすためにこれらのメソッドをオーバーライドする必要があります、<xref:System.Windows.Interop.HwndHost>コントラクト、ですが、最小限の実装を提供する必要がありますのみです。  
  
8.  分離コード ファイルにコントロールのホスト クラスのインスタンスを作成しの子、<xref:System.Windows.Controls.Border>ウィンドウをホストするためのものでは、要素。  
  
9. 送信することによってホストされるウィンドウとの通信[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]メッセージとコントロールによる通知の送信など、その子ウィンドウからメッセージを処理します。  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>ページ レイアウトを実装します。  
 レイアウト、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ListBox コントロールをホストしているページは、2 つの領域で構成されます。 いくつかのページの左側にあるホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を提供するコントロール、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]を操作することができます、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コントロール。 ページの右上隅には、ホスト型のリスト ボックス コントロールの正方形の領域があります。  
  
 このレイアウトを実装するコードは、非常にシンプルです。 ルート要素が、<xref:System.Windows.Controls.DockPanel>を持つ 2 つの子要素です。 1 つは、 <xref:System.Windows.Controls.Border> ListBox コントロールをホストする要素。 200 x 200 正方形インチのページの右上隅を占有します。 2 番目、<xref:System.Windows.Controls.StackPanel>要素のセットを含む[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を設定して、リスト ボックス コントロールを操作するための情報を表示したり、コントロールを相互運用性のプロパティを公開します。 各要素の子である、<xref:System.Windows.Controls.StackPanel>の詳細については、これらの要素とは何かがどのように使用されるさまざまな要素のリファレンスを参照して、これらの次のコード例に一覧表示されますが、されません (基本的なここで説明されています。相互運用のモデルではそれらのいずれかの必要はありませんは提供されたサンプルにいくつかの対話機能を追加する)。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 コントロールをホストするクラスを実装します。  
 このサンプルのコアは、実際には、コントロール、ControlHost.cs をホストするクラスです。 継承<xref:System.Windows.Interop.HwndHost>です。 コンス トラクターは 2 つのパラメーター、高さと幅の幅と高さに対応する、 <xref:System.Windows.Controls.Border> ListBox コントロールをホストする要素。 これらの値を使って、コントロールの一致結果のサイズを確認してください、<xref:System.Windows.Controls.Border>要素。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 定数のセットもします。 これらの定数の Winuser.h をから取得されます。 主とを呼び出すときに、従来の名前を使用できるように[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 ウィンドウを作成する BuildWindowCore をオーバーライドします。  
 作成するには、このメソッドをオーバーライドする、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  ページで、によってホストされ、ウィンドウで、ページ間を接続するウィンドウです。 このサンプルでは、リスト ボックス コントロールをホストしている、2 つのウィンドウが作成されます。 1 つは、実際にホストされているウィンドウ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページ。 ListBox コントロールは、そのウィンドウの子として作成されます。  
  
 このアプローチの理由をコントロールから通知を受け取るプロセスを簡略化を開始します。 <xref:System.Windows.Interop.HwndHost>クラスでは、それをホストしているウィンドウに送信されたメッセージを処理することができます。 ホストしている場合、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]直接コントロールをコントロールの内部メッセージ ループに送信されたメッセージを受信します。 コントロールとにメッセージを送信を表示することができますが、コントロールから親ウィンドウに送信される通知を受け取ることはありません。 つまり、特にがあるないユーザーがコントロールを操作するときを検出する方法です。 代わりに、ホスト ウィンドウを作成し、そのウィンドウの子コントロールを作成します。 これにより、コントロールによって送信された通知など、ホスト ウィンドウのメッセージを処理することができます。 便宜上、ホスト ウィンドウが単純なラッパー コントロールより小さな以上であるため、パッケージが参照されます ListBox コントロールとして。  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>ListBox コントロールとホスト ウィンドウを作成します。  
 使用することができます[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]を作成し、ウィンドウ クラスを登録するコントロールのホスト ウィンドウを作成します。 はるかに簡単な方法が定義済みの「静的」ウィンドウ クラスにウィンドウを作成します。 これにより、ウィンドウ プロシージャと、コントロールから通知を受信するために必要とする最小限のコーディングが必要です。  
  
 ホスト ページを使用するとコントロールにメッセージを送信に使用できるように、コントロールの HWND は読み取り専用のプロパティを通じて公開されます。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox コントロールは、ホスト ウィンドウの子として作成されます。 両方のウィンドウの幅と高さは、前述のとおり、コンス トラクターに渡された値に設定されます。 これにより、ホスト ウィンドウとコントロールのサイズが、ページ上の予約済み領域と同じことです。  サンプルを返します、windows が作成された後、<xref:System.Runtime.InteropServices.HandleRef>ホスト ウィンドウの HWND を含むオブジェクトです。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>実装 DestroyWindow と WndProc  
 加え<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>、上書きすることも必要があります、<xref:System.Windows.Interop.HwndHost.WndProc%2A>と<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>のメソッド、<xref:System.Windows.Interop.HwndHost>です。 コントロールのメッセージは、この例では、<xref:System.Windows.Interop.HwndHost.MessageHook>の実装ではこのため、ハンドラー<xref:System.Windows.Interop.HwndHost.WndProc%2A>と<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>は最小限にします。 場合、<xref:System.Windows.Interop.HwndHost.WndProc%2A>設定、`handled`に`false`にメッセージが処理されないことを示し、0 を返します。 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>、単にウィンドウを破棄します。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>ページ上のコントロールをホストします。  
 ページ上のコントロールをホストするには、まずを作成するの新しいインスタンス、`ControlHost`クラスです。 コントロールを含む罫線要素の幅と高さを渡す (`ControlHostElement`) に、`ControlHost`コンス トラクターです。 これにより、リスト ボックスのサイズが正しくされます。 割り当てることによって、ページ上のコントロールをホストする、`ControlHost`オブジェクトを<xref:System.Windows.Controls.Decorator.Child%2A>ホストのプロパティ<xref:System.Windows.Controls.Border>です。  
  
 このサンプルにハンドラーをアタッチする、<xref:System.Windows.Interop.HwndHost.MessageHook>のイベント、`ControlHost`コントロールからメッセージを受信します。 このイベントは、ホスト ウィンドウに送信されるすべてのメッセージに対して発生します。 この場合、これらのコントロールからの通知を含む実際の ListBox コントロールをラップするウィンドウに送信されるメッセージはします。 サンプルは、コントロールから情報を取得し、その内容を変更する 1 つを呼び出します。 ページが、コントロールとやり取りする方法の詳細については、次のセクションで説明します。  
  
> [!NOTE]
>  含まれている 2 つ[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]SendMessage を宣言します。 これは、1 つを使用するために必要な`wParam`文字列と、その他に渡すパラメーターが、整数値を渡すために使用します。 データが正しくマーシャ リングすることを確認するには、各署名の個別の宣言する必要があります。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>コントロールと、ページ間の通信を実装します。  
 送信してコントロールを操作する[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]メッセージ。 コントロールは、ユーザーがそのホスト ウィンドウに通知を送信することによってこれを操作するときに通知します。 [WPF サンプルでは Win32 ListBox コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=159998)サンプルには、この数式の動作のいくつかの例を提供する UI が含まれています。  
  
-   一覧に項目を追加します。  
  
-   一覧から選択した項目を削除します。  
  
-   現在選択されている項目のテキストを表示します。  
  
-   一覧に項目の数を表示します。  
  
 ユーザーを選択できます項目、リスト ボックスをクリックすると同じような従来の[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーションです。 項目を追加することを選択すると、追加、またはによっては、表示されているデータが、ユーザーがリスト ボックスの状態を変更するたびにでを更新します。  
  
 項目を追加するには、リスト ボックス LB_ADDSTRING メッセージを送信します。 項目を削除するには、LB_GETCURSEL を現在の選択範囲のインデックスを取得し、項目を削除する LB_DELETESTRING を送信します。 サンプルも LB_GETCOUNT を送信し、項目の数を表示する表示を更新する、返される値を使用します。 SendMessage のこれら両方のインスタンスがのいずれかを使用して、[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]宣言の前のセクションで説明します。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 ユーザーが項目を選択するか、選択項目を変更、コントロールに通知ホスト ウィンドウを生成する WM_COMMAND メッセージを送信することによって、<xref:System.Windows.Interop.HwndHost.MessageHook>ページのイベントです。 ハンドラーは、ホスト ウィンドウのメイン ウィンドウ プロシージャと同じ情報を受け取ります。 ブール値への参照を渡します`handled`です。 設定する`handled`に`true`をメッセージを処理して、それ以上の処理が必要なことを示します。  
  
 WM_COMMAND は、さまざまな理由により、送信されるため、イベントを処理するかどうかを判別通知 ID を確認する必要があります。 上位ワードに ID が含まれている、`wParam`パラメーター。 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]はくださいマクロでなく、このサンプルでは、ビットごとの演算子を使用して ID を抽出 ユーザーが行われた、または場合、選択項目を変更、ID が LBN_SELCHANGE になります。  
  
 LBN_SELCHANGE が受信したときに、サンプルは、コントロール LB_GETCURSEL メッセージを送信することによって、選択した項目のインデックスを取得します。 テキストを取得するには、まずを作成する、<xref:System.Text.StringBuilder>です。 メッセージを送信する、コントロール、LB_GETTEXT です。 空の渡す<xref:System.Text.StringBuilder>オブジェクトとして、`wParam`パラメーター。 SendMessage が返されるときに、<xref:System.Text.StringBuilder>選択された項目のテキストが含まれます。 この SendMessage の使用がまだ必要別[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)]宣言します。  
  
 最後に、設定`handled`に`true`メッセージが処理されたことを示すためにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Interop.HwndHost>  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [チュートリアル: 初めての WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
