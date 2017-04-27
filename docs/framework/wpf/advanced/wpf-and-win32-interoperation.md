---
title: "WPF と Win32 の相互運用性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ホスト (WPF コンテンツを Win32 ウィンドウで)"
  - "HWND 相互運用機能 [WPF]"
  - "相互運用性 [WPF], Win32"
  - "Win32 コード, WPF 相互運用"
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# WPF と Win32 の相互運用性
このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] および [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードを相互運用する方法の概要について説明します。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。  ただし、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] コードに多くの投資を行った場合は、そのコードの一部を再利用する方がより効率的である場合があります。  
  
   
  
<a name="basics"></a>   
## WPF と Win32 の相互運用の基本  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードを相互運用するための基本的な手法は 2 つあります。  
  
-   [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをホストします。  この手法では、標準の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウおよびアプリケーションのフレームワーク内で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の高度なグラフィックス機能を使用できます。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツで [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウをホストします。  この手法では、既存のカスタム [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コントロールを他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツのコンテキストで使用し、境界を越えてデータを渡すことができます。  
  
 ここでは、これらの各手法について概念的に説明します。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をホストする場合のコードを使用した説明については、「[チュートリアル: Win32 での WPF コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)」を参照してください。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] をホストする場合のコードを使用した説明については、「[チュートリアル: WPF での Win32 コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)」を参照してください。  
  
<a name="projects"></a>   
## WPF 相互運用プロジェクト  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] はマネージ コードですが、ほとんどの既存の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラムはアンマネージ [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] で記述されています。  純粋なアンマネージ プログラムから [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を呼び出すことはできません。  ただし、[!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] コンパイラで `/clr` オプションを使用すると、マネージとアンマネージの [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 呼び出しをシームレスに混在させることができる、マネージとアンマネージの混在プログラムを作成することができます。  
  
 プロジェクト レベルで、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルを [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] プロジェクトにコンパイルできないという問題があります。  これを解決するために、プロジェクトを分割する手法がいくつかあります。  
  
-   すべての [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページを含む [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] DLL をコンパイル済みのアセンブリとして作成し、[!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] 実行可能ファイルにその [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] を参照として含めます。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツの [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] 実行可能ファイルを作成し、そのファイルが [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテンツを含む [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] を参照するようにします。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] をコンパイルする代わりに、<xref:System.Windows.Markup.XamlReader.Load%2A> を使用して、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を実行時に読み込みます。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用せずに、すべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をコードで記述し、<xref:System.Windows.Application> から要素ツリーを構築します。  
  
 これらの中で最適な方法を使用してください。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] を使用したことがない場合は、相互運用のコード例に `gcnew` や `nullptr` などの "見慣れない" キーワードがあるかもしれません。古い二重アンダースコアの構文 \(`__gc`\) がこれらのキーワードによって置き換えられています。これらのキーワードを使用すると、[!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] のマネージ コードの構文がより自然になります。  [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] マネージ機能の詳細については、「[ランタイム プラットフォームのコンポーネントの拡張機能](../Topic/Component%20Extensions%20for%20Runtime%20Platforms.md)」および「[Hello, C\+\+\/CLI](http://go.microsoft.com/fwlink/?LinkId=98739)」を参照してください。  
  
<a name="hwnds"></a>   
## WPF での Hwnd の使用方法  
 ほとんどの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND 相互運用" を行うには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での HWND の使用方法を理解する必要があります。  HWND では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レンダリングと [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] レンダリングまたは [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]\/[!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] レンダリングを混在させることはできません。  混在させると、さまざまな影響が生じます。  主に、これらのレンダリング モデルを混在させるには、相互運用ソリューションを作成し、使用するレンダリング モデルごとに指定された相互運用セグメントを使用する必要があります。  また、相互運用ソリューションで実現できる動作に対する "空域" 制限がレンダリング動作によって生じます。  "空域" の概念の詳細については、「[技術領域の概要](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)」を参照してください。  
  
 画面上のすべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素が最終的に HWND によってサポートされます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> を作成すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によってトップレベルの HWND が作成され、<xref:System.Windows.Interop.HwndSource> を使用して <xref:System.Windows.Window> とその [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツが HWND 内に格納されます。  アプリケーション内の残りの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツは、その単一の HWND を共有します。  ただし、メニュー、コンボ ボックス ドロップダウン、およびその他のポップアップは例外です。  これらの要素では独自のトップレベル ウィンドウが作成されます。このため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] メニューは、そのメニューを格納するウィンドウ HWND の端を越える可能性があります。  <xref:System.Windows.Interop.HwndHost> を使用して HWND を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内に格納すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND に対して新しい子 HWND を配置する方法が [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] から [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] に通知されます。  
  
 HWND の関連概念として、各 HWND 内および各 HWND 間の透過性が挙げられます。  これは、「[技術領域の概要](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)」でも解説されています。  
  
<a name="hosting_a_wpf_page"></a>   
## Microsoft Win32 ウィンドウでの WPF コンテンツのホスト  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をホストするキーとなるのは、<xref:System.Windows.Interop.HwndSource> クラスです。  このクラスは [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツをラップし、その [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツを子ウィンドウとして[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に組み込むことができます。  次の方法では、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を単一のアプリケーションに統合します。  
  
1.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ \(コンテンツのルート要素\) をマネージ クラスとして実装します。  通常、このクラスは、複数の子要素を格納できるクラスやルート要素として使用されるクラスのいずれか \(<xref:System.Windows.Controls.DockPanel> や <xref:System.Windows.Controls.Page> など\) から継承されます。  以降の手順では、このクラスを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスと呼び、そのクラスのインスタンスを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトと呼びます。  
  
2.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] アプリケーションを [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)] で実装します。  既存のアンマネージ [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] アプリケーションから始める場合、通常、`/clr` コンパイラ フラグが含まれるようにプロジェクトの設定を変更して、アプリケーションでマネージ コードを呼び出すことができるようにできます \(`/clr` コンパイルをサポートするための要件の詳細については、ここでは説明しません\)。  
  
3.  スレッド処理モデルをシングル スレッド アパートメント \(STA: Single Threaded Apartment\) に設定します。  このスレッド処理モデルを使用するのは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のみです。  
  
4.  ウィンドウ プロシージャで WM\_CREATE 通知を処理します。  
  
5.  ハンドラー \(またはハンドラーが呼び出す関数\) で、次の手順を実行します。  
  
    1.  `parent` パラメーターとして親ウィンドウ HWND を持つ新しい <xref:System.Windows.Interop.HwndSource> オブジェクトを作成します。  
  
    2.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスのインスタンスを作成します。  
  
    3.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトへの参照を <xref:System.Windows.Interop.HwndSource> オブジェクトの <xref:System.Windows.Interop.HwndSource.RootVisual%2A> プロパティに割り当てます。  
  
    4.  <xref:System.Windows.Interop.HwndSource> オブジェクトの <xref:System.Windows.Interop.HwndSource.Handle%2A> プロパティにウィンドウ ハンドル \(HWND\) が格納されます。  アプリケーションのアンマネージ部分で使用できる HWND を取得するには、`Handle.ToPointer()` を HWND にキャストします。  
  
6.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトへの参照を保持する静的フィールドを含むマネージ クラスを実装します。  このクラスを使用すると、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コードから [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトへの参照を取得できますが、さらに、<xref:System.Windows.Interop.HwndSource> が不注意によりガベージ コレクトされることを回避できます。  
  
7.  ハンドラーを 1 つ以上の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクト イベントにアタッチして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトから通知を受信します。  
  
8.  静的フィールドに格納した参照を使用してプロパティの設定やメソッドの呼び出しなどを行い、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ オブジェクトと通信します。  
  
> [!NOTE]
>  個別のアセンブリを生成して参照する場合、手順 1. の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ クラスの定義の一部またはすべてを、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でコンテンツ クラスの既定の部分クラスを使用して行うことができます。通常は、<xref:System.Windows.Application> オブジェクトを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のコンパイルの一部としてアセンブリに含めますが、その <xref:System.Windows.Application> を相互運用の一部として使用することにはなりません。単に、アプリケーションによって参照される [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルの 1 つ以上のルート クラスを使用し、その部分クラスを参照します。  手順の残りの部分は、基本的に前述の手順と同様です。  
>   
>  これらの各手順のコードを使用した説明については、「[チュートリアル: Win32 での WPF コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)」を参照してください。  
  
<a name="hosting_an_hwnd"></a>   
## WPF での Microsoft Win32 ウィンドウのホスト  
 他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツ内で [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ウィンドウをホストするキーとなるのは、<xref:System.Windows.Interop.HwndHost> クラスです。  このクラスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素ツリーに追加できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素でウィンドウをラップします。  また、<xref:System.Windows.Interop.HwndHost> は、ホストされたウィンドウのメッセージの処理などのタスクを実行できるようにする [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] もサポートします。  基本手順は次のとおりです。  
  
1.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの要素ツリーを作成します \(コードまたはマークアップで作成できます\)。  <xref:System.Windows.Interop.HwndHost> の実装を子要素として追加できる適切な許可ポイントを要素ツリーで検索します。  この手順では以後、この要素を予約要素と呼びます。  
  
2.  <xref:System.Windows.Interop.HwndHost> からの派生クラスを作成し、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンテンツを保持するオブジェクトを作成します。  
  
3.  そのホスト クラスで、<xref:System.Windows.Interop.HwndHost> の <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> メソッドをオーバーライドします。  ホストされたウィンドウの HWND を返します。  返されたウィンドウの子ウィンドウとして実際のコントロールをラップすることもできます。ホスト ウィンドウでコントロールをラップすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンテンツでコントロールからの通知を簡単に受信できます。  この手法により、ホストされたコントロールの境界でのメッセージ処理に関するいくつかの [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 問題を修正できます。  
  
4.  <xref:System.Windows.Interop.HwndHost> の <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> メソッドと <xref:System.Windows.Interop.HwndHost.WndProc%2A> メソッドをオーバーライドします。  これは、クリーンアップの処理およびホストされたコンテンツへの参照の削除を行うためです \(特に、アンマネージ オブジェクトへの参照を作成した場合\)。  
  
5.  分離コード ファイルで、コントロール ホスト クラスのインスタンスを作成し、予約要素の子にします。  通常は、<xref:System.Windows.FrameworkElement.Loaded> などのイベント ハンドラーを使用するか、部分クラス コンストラクターを使用します。  ただし、ランタイム動作によって相互運用コンテンツを追加することもできます。  
  
6.  コントロールの通知などの選択されたウィンドウ メッセージを処理します。  処理方法は 2 つあります。  どちらも同様にメッセージ ストリームにアクセスできるようにするため、どちらを選択するかは、多くの場合、プログラミングの便宜上の理由によって決まります。  
  
    -   <xref:System.Windows.Interop.HwndHost> の <xref:System.Windows.Interop.HwndHost.WndProc%2A> メソッドのオーバーライドで、シャットダウン メッセージだけでなくすべてのメッセージのメッセージ処理を実装します。  
  
    -   <xref:System.Windows.Interop.HwndHost.MessageHook> イベントを処理して、ホスト [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素でメッセージを処理します。  このイベントは、ホストされたウィンドウのメイン ウィンドウ プロシージャに送信されるすべてのメッセージに対して発生します。  
  
    -   メッセージは、<xref:System.Windows.Interop.HwndHost.WndProc%2A> を使用するプロセスで発生したウィンドウからは処理できません。  
  
7.  プラットフォーム呼び出しを使用してアンマネージ `SendMessage` 関数を呼び出し、ホストされたウィンドウと通信します。  
  
 次の手順に従って、マウス入力で動作するアプリケーションを作成します。  <xref:System.Windows.Interop.IKeyboardInputSink> インターフェイスを実装して、ホストされたウィンドウで Tab キーによる移動がサポートされるようにすることができます。  
  
 これらの各手順のコードを使用した説明については、「[チュートリアル: WPF での Win32 コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)」を参照してください。  
  
### WPF 内の HWND  
 <xref:System.Windows.Interop.HwndHost> は特殊なコントロールであると考えることができます   \(技術的には、<xref:System.Windows.Interop.HwndHost> は <xref:System.Windows.Controls.Control> 派生クラスではなく、<xref:System.Windows.FrameworkElement> 派生クラスですが、相互運用のためのコントロールと見なすことができます\)。<xref:System.Windows.Interop.HwndHost> は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の残りの部分が、ホストされたコンテンツは入力を描画および処理する別のコントロールに似たオブジェクトであると見なすように、ホストされたコンテンツの基になる [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 特性を抽出します。  通常、<xref:System.Windows.Interop.HwndHost> は他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement> と同様に動作しますが、出力 \(描画とグラフィックス\) および入力 \(マウスとキーボード\) には、基になる HWND のサポート内容の制限に基づく重要な違いがいくつかあります。  
  
#### 出力動作の顕著な違い  
  
-   <xref:System.Windows.Interop.HwndHost> の基底クラスである <xref:System.Windows.FrameworkElement> には、UI の変更に関係する多くのプロパティが用意されています。  これには、親要素内の要素のレイアウトを変更する <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=fullName> などのプロパティが含まれます。  ただし、これらのプロパティの多くは、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] で有効な等価機能が存在しても、それに対応付けられていません。  非常に多くのプロパティとその意味がレンダリング テクノロジ固有でありすぎるために、対応付けをしても役に立ちません。  そのため、<xref:System.Windows.Interop.HwndHost> で <xref:System.Windows.FrameworkElement.FlowDirection%2A> などのプロパティを設定しても効果がありません。  
  
-   <xref:System.Windows.Interop.HwndHost> は、回転、拡大縮小、傾斜、または変換の影響を受けません。  
  
-   <xref:System.Windows.Interop.HwndHost> では、<xref:System.Windows.UIElement.Opacity%2A> プロパティ \(アルファ ブレンディング\) はサポートされません。  <xref:System.Windows.Interop.HwndHost> 内のコンテンツでアルファ情報を含む <xref:System.Drawing> 操作が実行される場合、それ自体は違反ではありませんが、<xref:System.Windows.Interop.HwndHost> 全体では不透明度 \= 1.0 \(100%\) のみがサポートされます。  
  
-   <xref:System.Windows.Interop.HwndHost> は、同じトップレベル ウィンドウの他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素の上に表示されます。  ただし、<xref:System.Windows.Controls.ToolTip> または <xref:System.Windows.Controls.ContextMenu> で生成されるメニューは独立したトップレベル ウィンドウであるため、<xref:System.Windows.Interop.HwndHost> で正しく動作します。  
  
-   <xref:System.Windows.Interop.HwndHost> は、親 <xref:System.Windows.UIElement> のクリッピング領域に対応しません。  これは、<xref:System.Windows.Interop.HwndHost> クラスをスクロール領域または <xref:System.Windows.Controls.Canvas> に格納しようとする場合に問題となる可能性があります。  
  
#### 入力動作の顕著な違い  
  
-   通常、入力デバイスは、<xref:System.Windows.Interop.HwndHost> がホストする [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 領域内がスコープとなり、入力イベントは [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] に直接移動します。  
  
-   <xref:System.Windows.Interop.HwndHost> の上にマウスがあるとき、アプリケーションは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マウス イベントを受け取らず、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の <xref:System.Windows.UIElement.IsMouseOver%2A> プロパティの値は `false` になります。  
  
-   <xref:System.Windows.Interop.HwndHost> にキーボード フォーカスがあるとき、アプリケーションは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] キーボード イベントを受け取らず、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> プロパティの値は `false` になります。  
  
-   <xref:System.Windows.Interop.HwndHost> 内にあるフォーカスが <xref:System.Windows.Interop.HwndHost> 内の別のコントロールに移動したとき、アプリケーションは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の <xref:System.Windows.UIElement.GotFocus> イベントまたは <xref:System.Windows.UIElement.LostFocus> イベントを受け取りません。  
  
-   関連するスタイラス プロパティおよびイベントは類似しており、スタイラスが <xref:System.Windows.Interop.HwndHost> 上にあるときは情報を報告しません。  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## Tab キーによる移動、ニーモニック、およびアクセラレータ  
 <xref:System.Windows.Interop.IKeyboardInputSink> インターフェイスおよび <xref:System.Windows.Interop.IKeyboardInputSite> インターフェイスを使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] が混在するアプリケーションでシームレスなキーボード操作を実現できます。  
  
-   [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] コンポーネントと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コンポーネント間の Tab キーによる移動  
  
-   フォーカスが Win32 コンポーネント内にある場合と WPF コンポーネント内にある場合の両方で動作するニーモニックおよびアクセラレータ  
  
 <xref:System.Windows.Interop.HwndHost> クラスと <xref:System.Windows.Interop.HwndSource> クラスはどちらも <xref:System.Windows.Interop.IKeyboardInputSink> の実装を提供しますが、より高度なシナリオで必要な入力メッセージが一部処理されない場合があります。  適切なメソッドをオーバーライドして、必要なキーボード動作を確保してください。  
  
 インターフェイスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 領域と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 領域間の遷移で発生する処理をサポートするだけです。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 領域では、Tab キーによる移動動作は、Tab キーによる移動の [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 実装ロジック \(ある場合\) によって完全に制御されます。  
  
## 参照  
 <xref:System.Windows.Interop.HwndHost>   
 <xref:System.Windows.Interop.HwndSource>   
 <xref:System.Windows.Interop>   
 [チュートリアル: WPF での Win32 コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)   
 [チュートリアル: Win32 での WPF コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)