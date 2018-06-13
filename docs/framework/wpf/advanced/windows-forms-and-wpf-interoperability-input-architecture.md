---
title: Windows フォームと WPF の相互運用性入力アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: 250f34e3e5420a613bc7b1035c62af90665e71ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549060"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows フォームと WPF の相互運用性入力アーキテクチャ
間で相互運用、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]両方のテクノロジは、適切なキーボード入力の処理である必要があります。 このトピックでは、これらのテクノロジで、キーボードとメッセージをハイブリッド アプリケーションでスムーズな相互運用を有効にする処理がどのように実装する方法について説明します。  
  
 このトピックは、次の内容で構成されています。  
  
-   モードレスのフォームとダイアログ ボックス  
  
-   WindowsFormsHost キーボードとメッセージの処理  
  
-   ElementHost キーボードとメッセージの処理  
  
## <a name="modeless-forms-and-dialog-boxes"></a>モードレスのフォームとダイアログ ボックス  
 呼び出す、<xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>からモードレス フォームまたはダイアログ ボックスを開き、要素、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。  
  
 呼び出す、<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールを開くには、モードレス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ページで、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのアプリケーションです。  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost キーボードとメッセージの処理  
 によってホストされている場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]キーボードとメッセージの処理が、次が含まれます。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスからのメッセージを取得し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]によって実装されるメッセージ ループ、<xref:System.Windows.Interop.ComponentDispatcher>クラスです。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスの作成のためのサロゲート[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]その通常ことを確認するメッセージ ループ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]キーボード処理が行われます。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスが実装する、<xref:System.Windows.Interop.IKeyboardInputSink>とフォーカス管理を調整するためのインターフェイス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールに登録し、メッセージ ループを開始します。  
  
 次のセクションでは、プロセスの詳細のこれらの要素について説明します。  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>WPF のメッセージ ループからのメッセージを取得します。  
 <xref:System.Windows.Interop.ComponentDispatcher>クラスのメッセージ ループ マネージャー[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 <xref:System.Windows.Interop.ComponentDispatcher>クラスを提供する前にメッセージをフィルター処理に外部のクライアントを有効にするフック[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]それを処理します。  
  
 相互運用性の実装のハンドル、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>これによりイベント[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]する前にメッセージを処理するコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
### <a name="surrogate-windows-forms-message-loop"></a>Windows フォームのメッセージ ループをサロゲート  
 既定では、<xref:System.Windows.Forms.Application?displayProperty=nameWithType>クラスの主なメッセージ ループに含まれる[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーションです。 相互運用時に、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]メッセージ ループは、メッセージを処理しません。 そのため、このロジックを再現する必要があります。 ハンドラーを<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>イベントは、次の手順を実行します。  
  
1.  使用してメッセージをフィルター処理、<xref:System.Windows.Forms.IMessageFilter>インターフェイスです。  
  
2.  呼び出し、<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>メソッドです。  
  
3.  変換し、必要な場合に、メッセージをディスパッチします。  
  
4.  その他のコントロールがメッセージを処理しない場合は、ホスト コントロールにメッセージを渡します。  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink 実装  
 サロゲートのメッセージ ループは、キーボードの管理を処理します。 したがって、<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>メソッドは、唯一<xref:System.Windows.Interop.IKeyboardInputSink>メンバーの実装を必要とする、<xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスです。  
  
 既定では、<xref:System.Windows.Interop.HwndHost>クラスを返します`false`の<xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>実装します。 これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールを[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>の実装、<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>メソッドは、次の手順を実行します。  
  
1.  最初の検索または最終[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールに含まれています、<xref:System.Windows.Forms.Integration.WindowsFormsHost>とコントロールがフォーカスを受け取ることができます。 コントロールの選択肢は、走査の各情報によって異なります。  
  
2.  コントロールにフォーカスを設定し、返します`true`です。  
  
3.  コントロールがフォーカスを受け取ることはない場合を返します`false`です。  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost 登録  
 ウィンドウを処理するときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールが作成された、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、メッセージ ループの存在を登録する内部の静的メソッドを呼び出します。  
  
 登録の際に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、メッセージ ループを検査します。 メッセージ ループが開始されていない場合、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>イベント ハンドラーを作成します。 メッセージ ループを実行している場合と見なされます、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>イベント ハンドラーがアタッチされています。  
  
 ウィンドウ ハンドルが破棄されるときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは登録から削除します。  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost キーボードとメッセージの処理  
 によってホストされている場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]キーボードとメッセージの処理が、次が含まれます。  
  
-   <xref:System.Windows.Interop.HwndSource>、 <xref:System.Windows.Interop.IKeyboardInputSink>、および<xref:System.Windows.Interop.IKeyboardInputSite>インターフェイスの実装です。  
  
-   Tab キーと方向キー。  
  
-   コマンド キーとダイアログ ボックスのキー。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アクセラレータ処理します。  
  
 次のセクションでは、これらのパートの詳細にについて説明します。  
  
### <a name="interface-implementations"></a>インターフェイスの実装  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]フォーカスのあるコントロールのウィンドウ ハンドルにキーボード メッセージをルーティングします。 <xref:System.Windows.Forms.Integration.ElementHost>コントロールでホストされている要素にこれらのメッセージがルーティングされます。 これを実現する、<xref:System.Windows.Forms.Integration.ElementHost>コントロールには、<xref:System.Windows.Interop.HwndSource>インスタンス。 場合、<xref:System.Windows.Forms.Integration.ElementHost>コントロールにフォーカスがある、<xref:System.Windows.Interop.HwndSource>インスタンスにルーティングが処理できるように、入力ほとんどのキーボード、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>クラスです。  
  
 <xref:System.Windows.Interop.HwndSource>クラスが実装する、<xref:System.Windows.Interop.IKeyboardInputSink>と<xref:System.Windows.Interop.IKeyboardInputSite>インターフェイスです。  
  
 実装に依存しているキーボードの相互運用、<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>メソッド ハンドル TAB キーと方向をキーの入力のホスト型の要素からフォーカスを移動します。  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing と方向キー  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]選択ロジックにマップされて、<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>と<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>キー ナビゲーションのタブと矢印を実装するメソッド。 オーバーライドする、<xref:System.Windows.Forms.Integration.ElementHost.Select%2A>メソッドは、このマッピングを実現します。  
  
### <a name="command-keys-and-dialog-box-keys"></a>コマンド キーとダイアログ ボックス  
 付与する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コマンド キーおよびダイアログ キーを処理する最初のチャンス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]に接続されているコマンドの前処理、<xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>メソッドです。 オーバーライドする、<xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType>メソッドが 2 つのテクノロジを接続します。  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>メソッド、ホスト型の要素は、WM_KEYDOWN、WM_KEYUP、WM_SYSKEYDOWN、タブ、ENTER、esc キー、方向キーとキーなどのコマンド キーを含む WM_SYSKEYUP など、すべてのキー メッセージを処理できます。 キー メッセージが処理されない場合送信、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]先祖階層を処理するためです。  
  
### <a name="accelerator-processing"></a>アクセラレータの処理  
 アクセラレータを正しく処理する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アクセラレータ処理に接続されている必要があります、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>クラスです。 さらに、ホストされている要素にすべての WM_CHAR メッセージを正しくルーティングする必要があります。  
  
 既定<xref:System.Windows.Interop.HwndSource>の実装、<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>メソッドを返します。 `false`、WM_CHAR メッセージは、次のロジックを使用して処理されます。  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType>メソッドをオーバーライドして、ホスト型の要素をすべての WM_CHAR メッセージが転送されることを確認してください。  
  
-   ALT キーが押されると、メッセージが wm_syschar です。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 経由でこのメッセージを前処理せず、<xref:System.Windows.Forms.Control.IsInputChar%2A>メソッドです。 したがって、<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>メソッドがオーバーライドされるクエリに、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>登録済みのアクセラレータをします。 登録済みのアクセラレータが見つかった場合、<xref:System.Windows.Input.AccessKeyManager>はそれを処理します。  
  
-   ALT キーが押されていない場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>クラスは、未処理の入力を処理します。 入力が、アクセラレータの場合、<xref:System.Windows.Input.AccessKeyManager>はそれを処理します。 <xref:System.Windows.Input.InputManager.PostProcessInput>イベントが処理されなかった WM_CHAR メッセージを処理します。  
  
 ユーザーは、ALT キーを押すと、アクセラレータの視覚的な手掛かりがフォーム全体に表示されます。 この動作をサポートするためにすべて<xref:System.Windows.Forms.Integration.ElementHost>はアクティブなフォーム上のコントロールがコントロールにフォーカスがある、WM_SYSKEYDOWN のメッセージを受信します。  
  
 のみメッセージが送信される<xref:System.Windows.Forms.Integration.ElementHost>でアクティブなフォームのコントロールです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
