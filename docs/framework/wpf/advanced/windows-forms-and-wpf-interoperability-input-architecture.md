---
title: "Windows フォームと WPF の相互運用性入力アーキテクチャ | Microsoft Docs"
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
  - "ElementHost のキーボードとメッセージ"
  - "入力アーキテクチャ [WPF 相互運用性]"
  - "相互運用性 [WPF], Windows フォーム"
  - "キーボードの相互運用 [WPF]"
  - "メッセージ [WPF]"
  - "モードレス ダイアログ ボックス [WPF]"
  - "モードレス フォーム"
  - "Windows フォーム [WPF], 相互運用性"
  - "Windows フォーム, WPF 相互運用"
  - "WindowsFormsHost のキーボードとメッセージ_"
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Windows フォームと WPF の相互運用性入力アーキテクチャ
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]間の相互運用を実現するには、両方のテクノロジに適切なキーボード入力処理が必要です。  ここでは、これらのテクノロジにキーボードおよびメッセージ処理を実装して、ハイブリッド アプリケーションでの円滑な相互運用を有効にする方法を説明します。  
  
 このトピックは、次の内容で構成されています。  
  
-   モードレス フォームとダイアログ ボックス  
  
-   WindowsFormsHost キーボードとメッセージ処理  
  
-   ElementHost のキーボードおよびメッセージ処理  
  
## モードレス フォームとダイアログ ボックス  
 モードレス フォームまたはダイアログ ボックスを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションから開くには、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素で <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> メソッドを呼び出します。  
  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ベースのアプリケーションでモードレス [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページを開くには、<xref:System.Windows.Forms.Integration.ElementHost> コントロールで <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> メソッドを呼び出します。  
  
## WindowsFormsHost キーボードとメッセージ処理  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションでホストされている場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のキーボードおよびメッセージ処理は、次の要素から構成されます。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスは、<xref:System.Windows.Interop.ComponentDispatcher> クラスで実装される [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] メッセージ ループからメッセージを取得します。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスは、通常の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] キーボード処理が行われるように、サロゲート [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] メッセージ ループを作成します。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスは、<xref:System.Windows.Interop.IKeyboardInputSink> インターフェイスを実装して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] とフォーカス管理を調整します。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは自身を登録し、それらのメッセージ ループを開始します。  
  
 以下のセクションでは、これらのプロセスの各部分について詳しく説明します。  
  
### WPF メッセージ ループからのメッセージの取得  
 <xref:System.Windows.Interop.ComponentDispatcher> クラスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のメッセージ ループ マネージャーを実装します。  <xref:System.Windows.Interop.ComponentDispatcher> クラスはフックを提供して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がメッセージを処理する前に外部のクライアントによってそれらのメッセージが処理されるようにします。  
  
 相互運用性の実装は <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> イベントを処理し、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールよりも前にメッセージを処理できるようにします。  
  
### サロゲート Windows フォーム メッセージ ループ  
 既定では、<xref:System.Windows.Forms.Application?displayProperty=fullName> クラスに [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーションの主要なメッセージ ループが含まれています。  相互運用中、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] メッセージ ループはメッセージを処理しません。  したがって、このロジックを再現する必要があります。  <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> イベントのハンドラーは、次の手順を実行します。  
  
1.  <xref:System.Windows.Forms.IMessageFilter> インターフェイスを使用してメッセージをフィルター処理します。  
  
2.  <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=fullName> メソッドを呼び出します。  
  
3.  必要な場合は、メッセージを変換してディスパッチします。  
  
4.  他のコントロールがメッセージを処理しない場合、ホストしているコントロールにメッセージを渡します。  
  
### IKeyboardInputSink の実装  
 サロゲート メッセージ ループは、キーボード管理を処理します。  したがって、<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=fullName> メソッドは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスで実装を必要とする唯一の <xref:System.Windows.Interop.IKeyboardInputSink> メンバーです。  
  
 既定では、<xref:System.Windows.Interop.HwndHost> クラスは、その <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> の実装に対して `false` を返します。  これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールから [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールへの Tab キーによる移動はできなくなります。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> の <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=fullName> メソッドの  実装は、次の手順を実行します。  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールに含まれ、フォーカスを受け取ることができる [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の最初または最後のコントロールを見つけます。  コントロールの選択肢は、検査情報によって異なります。  
  
2.  コントロールにフォーカスを設定し、`true` を返します。  
  
3.  コントロールがフォーカスを受け取ることができない場合は、`false` を返します。  
  
### WindowsFormsHost の登録  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールへのウィンドウ ハンドルが作成されると、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは、メッセージ ループに対してその存在を登録する内部の静的メソッドを呼び出します。  
  
 登録中、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールはメッセージ ループを調べます。  メッセージ ループが開始されていない場合、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> イベント ハンドラーが作成されます。  <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> イベント ハンドラーがアタッチされている場合、メッセージ ループは実行中と見なされます。  
  
 ウィンドウ ハンドルが破棄されると、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは自身の登録を解除します。  
  
## ElementHost のキーボードおよびメッセージ処理  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーションでホストされている場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のキーボードおよびメッセージ処理は、次の要素から構成されます。  
  
-   <xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.IKeyboardInputSink> インターフェイス実装、および <xref:System.Windows.Interop.IKeyboardInputSite> インターフェイス実装。  
  
-   Tab キーと方向キー。  
  
-   コマンド キーとダイアログ ボックス キー。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アクセラレータ処理。  
  
 以下のセクションでは、これらの各部分について詳しく説明します。  
  
### インターフェイスの実装  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]では、キーボード メッセージが、フォーカスを持つコントロールのウィンドウ ハンドルにルーティングされます。  <xref:System.Windows.Forms.Integration.ElementHost> コントロールでは、これらのメッセージはホストされている要素にルーティングされます。  これを実現するために、<xref:System.Windows.Forms.Integration.ElementHost> コントロールは、<xref:System.Windows.Interop.HwndSource> インスタンスを提供します。  <xref:System.Windows.Forms.Integration.ElementHost> コントロールにフォーカスが設定されている場合、<xref:System.Windows.Interop.HwndSource> インスタンスはほとんどのキーボード入力をルーティングして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> クラスで処理できるようにします。  
  
 <xref:System.Windows.Interop.HwndSource> クラスは、<xref:System.Windows.Interop.IKeyboardInputSink> インターフェイスと <xref:System.Windows.Interop.IKeyboardInputSite> インターフェイスを実装します。  
  
 キーボードの相互運用では、<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> メソッドの実装に依存して、ホストされている要素からフォーカスを移動する Tab キーおよび方向キーの入力を処理します。  
  
### Tab キーと方向キー  
 Tab キーおよび方向キーによる移動を実装するために、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の選択ロジックは <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> メソッドと <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> メソッドにマッピングされます。  <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> メソッドをオーバーライドして、このマッピングを実現します。  
  
### コマンド キーとダイアログ ボックス キー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対して、コマンド キーとダイアログ キーを処理する最初の機会を提供するために、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コマンドの事前処理が <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> メソッドに関連付けられます。  <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=fullName> メソッドをオーバーライドすると、2 つのテクノロジが関連付けられます。  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> メソッドを使用すると、ホストされた要素は、Tab キー、Enter キー、Esc キー、方向キーなどのコマンド キーを含む、WM\_KEYDOWN、WM\_KEYUP、WM\_SYSKEYDOWN、WM\_SYSKEYUP などのキー メッセージを処理できます。  キー メッセージが処理されない場合、そのキー メッセージは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]の先祖の階層に送られ、処理されます。  
  
### アクセラレータ処理  
 アクセラレータを正しく処理するには、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アクセラレータ処理を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> クラスに関連付ける必要があります。  また、すべての WM\_CHAR メッセージは、ホストされている要素に正しくルーティングされる必要があります。  
  
 <xref:System.Windows.Interop.HwndSource> の <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> メソッドの既定の実装は `false` を返すため、WM\_CHAR メッセージは次のロジックを使用して処理されます。  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=fullName> メソッドは、すべての WM\_CHAR メッセージがホストされている要素に転送されるようにオーバーライドされます。  
  
-   Alt キーが押された場合、メッセージは WM\_SYSCHAR になります。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は、このメッセージを <xref:System.Windows.Forms.Control.IsInputChar%2A> メソッドを通して事前に処理しません。  したがって、<xref:System.Windows.Forms.Control.ProcessMnemonic%2A> メソッドは、登録済みのアクセラレータを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> に照会するためにオーバーライドされます。  登録済みのアクセラレータが見つかった場合、<xref:System.Windows.Input.AccessKeyManager> はそのアクセラレータを処理します。  
  
-   Alt キーが押されない場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> クラスは未処理の入力を処理します。  入力がアクセラレータである場合、<xref:System.Windows.Input.AccessKeyManager> がそのアクセラレータを処理します。  処理されていない WM\_CHAR メッセージに対して <xref:System.Windows.Input.InputManager.PostProcessInput> イベントが処理されます。  
  
 ユーザーが Alt キーを押すと、アクセラレータのビジュアル キューがフォーム全体に示されます。  この動作をサポートするために、アクティブ フォーム上のすべての <xref:System.Windows.Forms.Integration.ElementHost> コントロールは、フォーカスがどのコントロールに設定されているかに関係なく、WM\_SYSKEYDOWN メッセージを受け取ります。  
  
 メッセージは、アクティブ フォーム内の <xref:System.Windows.Forms.Integration.ElementHost> コントロールにだけ送信されます。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>   
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>   
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)