---
title: "チュートリアル: WPF での Win32 コントロールのホスト | Microsoft Docs"
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
  - "ホスト (Win32 コントロールを WPF で) "
  - "Win32 コード, WPF 相互運用"
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# チュートリアル: WPF での Win32 コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。  ただし、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] のコードに多くの投資を行った場合は、元のコードを全面的に記述し直すよりも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのコードの少なくとも一部を再利用する方が効率的である場合があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページで [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウをホストするためのわかりやすいメカニズムが用意されています。  
  
 このトピックでは、[WPF での Win32 ListBox コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159998)に示されている、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] リスト ボックス コントロールをホストするアプリケーションについて説明します。  この一般的な手順を拡張することにより、どの [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウでもホストできます。  
  
   
  
<a name="requirements"></a>   
## 要件  
 このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] および [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] のプログラミングに関する基本的な知識があることを前提としています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プログラミングの概要については、「[作業の開始](../../../../docs/framework/wpf/getting-started/index.md)」を参照してください。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの概要については多数の書籍が出版されているので、それらを参照してください。特に、『プログラミング Windows』\(Charles Petzold 著\) が参考になります。  
  
 このトピックに含まれるサンプルは [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] で実装されるので、[!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] を利用して、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] にアクセスします。  [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] の知識は役立ちますが、必須ではありません。  
  
> [!NOTE]
>  このトピックには、関連するサンプルからのコード例が数多く含まれています。  ただし、読みやすさのために、完全なサンプル コードは含まれていません。  コード全体については、[WPF での Win32 ListBox コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159998)を参照してください。  
  
<a name="basic_procedure"></a>   
## 基本手順  
 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページで [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウをホストするための基本手順を説明します。  残りのセクションでは、各手順の詳細について説明します。  
  
 基本的なホスト手順は次のとおりです。  
  
1.  ウィンドウをホストする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページを実装します。  1 つの方法は、<xref:System.Windows.Controls.Border> 要素を作成し、ホストされるウィンドウのページのセクションを予約することです。  
  
2.  <xref:System.Windows.Interop.HwndHost> から継承するコントロールをホストするクラスを実装します。  
  
3.  そのクラスで、<xref:System.Windows.Interop.HwndHost> クラス メンバーの <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> をオーバーライドします。  
  
4.  ホストされるウィンドウを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページを含むウィンドウの子として作成します。  従来の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プログラミングでは明示的に利用する必要はありませんが、ホストするページは、ハンドル \(HWND\) を持つウィンドウです。  ページの HWND は、<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> メソッドの `hwndParent` パラメーターを通じて受け取ります。  ホストされるウィンドウは、この HWND の子として作成する必要があります。  
  
5.  ホスト ウィンドウを作成したら、ホストされるウィンドウの HWND を返します。  1 つ以上の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールをホストする場合、通常は、ホスト ウィンドウを HWND の子として作成し、コントロールをそのホスト ウィンドウの子にします。  複数のコントロールを 1 つのホスト ウィンドウにラップすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページでそれらのコントロールから通知を受信することが簡素化され、HWND 境界を越えた通知に関する [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] での問題を処理できます。  
  
6.  子コントロールからの通知など、ホスト ウィンドウに送信されたメッセージを選択して処理します。  これには、2 つの方法があります。  
  
    -   ホストするクラスでメッセージを処理する場合は、<xref:System.Windows.Interop.HwndHost> クラスの <xref:System.Windows.Interop.HwndHost.WndProc%2A> メソッドをオーバーライドします。  
  
    -   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でメッセージを処理する場合は、分離コードで <xref:System.Windows.Interop.HwndHost> クラスの <xref:System.Windows.Interop.HwndHost.MessageHook> イベントを処理します。  このイベントは、ホストされるウィンドウで受信されるメッセージごとに発生します。  このオプションを選択する場合でも <xref:System.Windows.Interop.HwndHost.WndProc%2A> をオーバーライドする必要がありますが、最小限の実装だけで十分です。  
  
7.  <xref:System.Windows.Interop.HwndHost> の <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> メソッドと <xref:System.Windows.Interop.HwndHost.WndProc%2A> メソッドをオーバーライドします。  <xref:System.Windows.Interop.HwndHost> コントラクトを満たすためにはこれらのメソッドをオーバーライドする必要がありますが、場合によっては最小限の実装だけで十分です。  
  
8.  分離コード ファイルで、コントロール ホスト クラスのインスタンスを作成し、ウィンドウをホストする目的の <xref:System.Windows.Controls.Border> 要素の子にします。  
  
9. ホストされるウィンドウに [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] メッセージを送信し、コントロールから送信された通知など、その子ウィンドウからのメッセージを処理して、そのウィンドウと通信します。  
  
<a name="page_layout"></a>   
## ページ レイアウトの実装  
 ListBox コントロールをホストする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページのレイアウトは、2 つの領域で構成されます。  ページの左側では、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールを操作するための[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を提供する、いくつかの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールをホストします。  ページの右上隅には、ホストされる ListBox コントロールを表す正方形の領域があります。  
  
 このレイアウトを実装するコードは、非常に単純です。  ルート要素は、2 つの子要素を持つ <xref:System.Windows.Controls.DockPanel> です。  1 つ目は、ListBox コントロールをホストする <xref:System.Windows.Controls.Border> 要素です。  これは、ページの右上隅の 200 × 200 の正方形部分を使用します。  2 つ目は、情報を表示したり、公開されている相互運用プロパティを設定して ListBox コントロールを操作できる一連の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールを含む <xref:System.Windows.Controls.StackPanel> 要素です。  <xref:System.Windows.Controls.StackPanel> の子である各要素については、どのような要素があり、それらが何を実行するかについての詳細について、使用されている各要素のリファレンス資料で参照してください。これらの要素は、次のサンプル コードにリストされていますが、ここでは説明しません \(それらは基本相互運用モデルには不要で、サンプルの対話性を強化するために提供されています\)。  
  
 [!code-xml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## Microsoft Win32 コントロールをホストするクラスの実装  
 このサンプルの中核は、コントロールを実際にホストする ControlHost.cs というクラスです。  このクラスは、<xref:System.Windows.Interop.HwndHost> から継承されます。  コンストラクターは、高さと幅の 2 つのパラメーターを使用します。これらのパラメーターは、ListBox コントロールをホストする <xref:System.Windows.Controls.Border> 要素の高さと幅に対応します。  これらの値を後から使用して、コントロールのサイズが <xref:System.Windows.Controls.Border> 要素と一致するようにします。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 また、一連の定数もあります。  これらの定数の多くは Winuser.h から取得され、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 関数を呼び出すときには従来の名前を使用できます。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### Microsoft Win32 ウィンドウを作成するための BuildWindowCore のオーバーライド  
 このメソッドをオーバーライドして、ページでホストされる [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウを作成し、ウィンドウとページの間を接続します。  このサンプルでは ListBox コントロールをホストするため、2 つのウィンドウが作成されます。  1 つは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページで実際にホストされるウィンドウです。  ListBox コントロールは、そのウィンドウの子として作成されます。  
  
 この方法を使用するのは、コントロールから通知を受信するプロセスを簡単にするためです。  <xref:System.Windows.Interop.HwndHost> クラスを使用することにより、ホストしているウィンドウに送信されるメッセージを処理できます。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールを直接ホストする場合は、コントロールの内部メッセージ ループに送信されたメッセージを受信します。  コントロールを表示してそのコントロールにメッセージを送信できますが、コントロールがその親ウィンドウに送信する通知は受信されません。  これが意味することはいくつかありますが、その 1 つは、ユーザーがコントロールと対話していることを検出する手段がないことです。  そのため、代わりにホスト ウィンドウを作成し、コントロールをそのウィンドウの子にします。  この方法を使用すると、コントロールがホスト ウィンドウに対して送信する通知を含め、ホスト ウィンドウのメッセージを処理できます。  ホスト ウィンドウは、コントロールの単純なラッパーとほとんど変わりないため、便宜上、パッケージは ListBox コントロールとして参照されます。  
  
<a name="create_the_window_and_listbox"></a>   
#### ホスト ウィンドウと ListBox コントロールの作成  
 [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] を使用して、ウィンドウ クラスを作成、登録するなどの方法で、コントロールのホスト ウィンドウを作成できます。  ただし、定義済みの "静的" ウィンドウ クラスを使用してウィンドウを作成した方がはるかに簡単です。  この方法では、コントロールから通知を受信するために必要なウィンドウ プロシージャが提供されるので、最小限のコーディングだけで済みます。  
  
 コントロールの HWND は読み取り専用プロパティを通じて公開されるため、ホスト ページは HWND を使用してコントロールにメッセージを送信できます。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox コントロールは、ホスト ウィンドウの子として作成されます。  両方のウィンドウの高さと幅は、既に説明したように、コンストラクターに渡される値に設定されます。  このため、ホスト ウィンドウとコントロールのサイズは、ページ上の予約された領域と同じになります。  ウィンドウが作成されると、このサンプルでは、ホスト ウィンドウの HWND を含む <xref:System.Runtime.InteropServices.HandleRef> オブジェクトが返されます。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### DestroyWindow と WndProc の実装  
 <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> に加え、<xref:System.Windows.Interop.HwndHost> の <xref:System.Windows.Interop.HwndHost.WndProc%2A> メソッドと <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> メソッドもオーバーライドする必要があります。  この例では、コントロールのメッセージが <xref:System.Windows.Interop.HwndHost.MessageHook> ハンドラーで処理されるため、少なくとも <xref:System.Windows.Interop.HwndHost.WndProc%2A> と <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> の実装が必要です。  <xref:System.Windows.Interop.HwndHost.WndProc%2A> の場合は、`handled` を `false` に設定して、メッセージが処理されなかったことを示し、0 を返します。  <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> の場合は、単純にウィンドウを破棄します。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## ページでのコントロールのホスト  
 ページ上のコントロールをホストするには、最初に `ControlHost` クラスの新しいインスタンスを作成します。  コントロールを含む境界線要素 \(`ControlHostElement`\) の高さと幅を、`ControlHost` コンストラクターに渡します。  これにより、ListBox のサイズが正しく設定されます。  次に、ホストの <xref:System.Windows.Controls.Border> の <xref:System.Windows.Controls.Decorator.Child%2A> プロパティに `ControlHost` オブジェクトを割り当てて、ページ上のコントロールをホストします。  
  
 このサンプルでは、`ControlHost` の <xref:System.Windows.Interop.HwndHost.MessageHook> イベントにハンドラーをアタッチしてコントロールからのメッセージを受信します。  このイベントは、ホストされているウィンドウに送信されたすべてのメッセージに対して発生します。  この場合、これらのメッセージは、コントロールからの通知を含め、実際の ListBox コントロールをラップするウィンドウに送信されます。  このサンプルでは、SendMessage を呼び出して、コントロールから情報を取得し、そのコンテンツを変更します。  ページとコントロールとの通信方法の詳細については、次のセクションで説明します。  
  
> [!NOTE]
>  SendMessage には 2 つの[!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 宣言があります。  2 つ必要なのは、一方は `wParam` パラメーターを使用して文字列を渡し、もう一方は同じパラメーターを使用して整数を渡すためです。  データが正しくマーシャリングされるために、各署名に対して個別の宣言が必要です。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## コントロールとページ間の通信の実装  
 コントロールに [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] メッセージを送信して、コントロールを操作します。  コントロールは、そのホスト ウィンドウに通知を送信することで、ユーザーがコントロールと対話したことを通知します。  [WPF での Win32 ListBox コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159998)には、この動作の次のようないくつかの例を示す UI が含まれています。  
  
-   リストへの項目の追加  
  
-   リストからの選択した項目の削除  
  
-   現在選択されている項目のテキストの表示  
  
-   リスト内の項目数の表示  
  
 ユーザーは、従来の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションと同様に、リスト ボックス内の項目をクリックして選択することもできます。  表示されているデータは、ユーザーが項目を選択、追加して、リスト ボックスの状態を変更するたびに更新されます。  
  
 項目を追加するには、リスト ボックスに LB\_ADDSTRING メッセージを送信します。  項目を削除するには、LB\_GETCURSEL を送信して現在の選択のインデックスを取得してから、LB\_DELETESTRING を送信して項目を削除します。  このサンプルでは、LB\_GETCOUNT も送信し、返された値を使用することにより、項目数を示す表示を更新します。  SendMessage のこれらのインスタンスはどちらも、前のセクションで説明した [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 宣言の 1 つを使用しています。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 ユーザーが項目を選択したり、選択内容を変更すると、コントロールはホスト ウィンドウに WM\_COMMAND メッセージを送信して通知し、その結果、ページの <xref:System.Windows.Interop.HwndHost.MessageHook> イベントが発生します。  ハンドラーは、ホスト ウィンドウのメイン ウィンドウ プロシージャと同じ情報を受け取ります。  また、ブール値 `handled` への参照を渡します。  メッセージが処理済みになり、これ以上の処理が不要であることを示すには、`handled` を `true` に設定します。  
  
 WM\_COMMAND はさまざまな理由で送信されるため、通知 ID を調べて、処理するイベントかどうかを判断する必要があります。  ID は、`wParam` パラメーターの上位ワードに格納されています。  [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] には HIWORD マクロがないため、このサンプルではビット単位の演算子を使用して ID を抽出します。  ユーザーが選択や選択の変更を行うと、ID は LBN\_SELCHANGE になります。  
  
 サンプルは、LBN\_SELCHANGE を受け取ると、コントロールに LB\_GETCURSEL メッセージを送信することにより、選択した項目のインデックスを取得します。  テキストを取得するには、最初に <xref:System.Text.StringBuilder> を作成します。  その後、コントロールに LB\_GETTEXT メッセージを送信します。  空の <xref:System.Text.StringBuilder> オブジェクトを `wParam` パラメーターとして渡します。  SendMessage が返るときに、<xref:System.Text.StringBuilder> には選択した項目のテキストが含まれます。  SendMessage を使用するには、さらに別の [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] 宣言が必要です。  
  
 最後に、`handled` を `true` に設定して、メッセージが処理されたことを示します。  
  
## 参照  
 <xref:System.Windows.Interop.HwndHost>   
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)