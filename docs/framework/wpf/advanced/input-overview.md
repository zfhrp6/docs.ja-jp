---
title: "入力の概要 | Microsoft Docs"
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
  - "コマンド [WPF]"
  - "入力 [WPF], 概要"
  - "キーボード フォーカス [WPF]"
  - "キーボード入力 [WPF]"
  - "タッチ イベント [WPF]"
  - "イベント ルーティング [WPF]"
  - "タッチ入力 [WPF]"
  - "操作 [WPF]"
  - "論理フォーカス [WPF]"
  - "スタイラス入力 [WPF]"
  - "テキスト入力 [WPF]"
  - "処理する入力イベント [WPF]"
  - "WPF では、入力の概要"
  - "操作イベント [WPF]"
  - "マウス入力 [WPF]"
  - "マウス キャプチャ [WPF]"
  - "フォーカス [WPF]"
  - "マウスの位置 [WPF]"
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
caps.latest.revision: 50
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 50
---
# 入力の概要
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]サブシステムは、強力な[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]マウス、キーボード、タッチ、およびスタイラスなどのさまざまなデバイスからの入力を取得します。 このトピックの説明が提供するサービス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]し、入力システムのアーキテクチャについて説明します。  
  
  
<a name="input_api"></a>   
## <a name="input-api"></a>入力 API  
 主な入力[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]露出が要素の基本クラスが見つかりました: <xref:System.Windows.UIElement>、 <xref:System.Windows.ContentElement>、 <xref:System.Windows.FrameworkElement>、および<xref:System.Windows.FrameworkContentElement>します。  基本要素の詳細については、次を参照してください。[基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)します。  これらのクラスは、キーの押下、マウス ボタン、マウス ホイール、マウスの動きをフォーカス管理、およびマウスのキャプチャなどに関連する入力イベントの機能を提供します。 入力を配置することで[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]基本要素で扱うのではなくすべての入力イベントをサービスとして、入力のアーキテクチャは、UI では、特定のオブジェクトによって明らかにして、複数の要素が入力イベントを処理するには、イベント ルーティング方法をサポートするために、入力イベントを有効にします。 多くの入力イベントでは、それらに関連付けられているイベントのペアを持っています。  たとえば、上下のイベントに関連付けられている、 <xref:System.Windows.Input.Keyboard.KeyDown>と<xref:System.Windows.Input.Keyboard.PreviewKeyDown>イベントです。  これらのイベントの違いは、ターゲット要素へのルーティング方法でです。  プレビュー イベントは、ターゲット要素にはルート要素から要素ツリーの下位トンネリングします。  バブル イベントは、ルート要素に、ターゲット要素からバブルアップします。  イベントのルーティングで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]しこの概要の後で、詳細に説明した、[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)します。  
  
### <a name="keyboard-and-mouse-classes"></a>キーボードとマウス クラス  
 入力だけでなく[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]、基本要素のクラスで、<xref:System.Windows.Input.Keyboard>クラスと<xref:System.Windows.Input.Mouse>クラスを追加提供[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]キーボードとマウスの入力を操作するためです。  
  
 入力の例[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]に、<xref:System.Windows.Input.Keyboard>クラスは、<xref:System.Windows.Input.Keyboard.Modifiers%2A>を返すプロパティ、<xref:System.Windows.Input.ModifierKeys>現在押されて、 <xref:System.Windows.Input.Keyboard.IsKeyDown%2A>メソッドで、指定したキーが押されたかどうかを決定します。  
  
 次の例では、 <xref:System.Windows.Input.Keyboard.GetKeyStates%2A>メソッドかどうかを<xref:System.Windows.Input.Key>停止状態にします。  
  
 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]  
  
 入力の例として[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]上、<xref:System.Windows.Input.Mouse>クラスが<xref:System.Windows.Input.Mouse.MiddleButton%2A>、マウスの中央ボタンの状態の取得元と<xref:System.Windows.Input.Mouse.DirectlyOver%2A>、経由では現在マウス ポインターの要素を取得します。  
  
 次の例を確認するかどうか、 <xref:System.Windows.Input.Mouse.LeftButton%2A>では、マウスは、 <xref:System.Windows.Input.MouseButtonState>状態です。  
  
 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]  
  
 <xref:System.Windows.Input.Mouse>と<xref:System.Windows.Input.Keyboard>クラスは、この概要で詳細に説明します。  
  
### <a name="stylus-input"></a>スタイラスからの入力  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]サポートが統合されて、<xref:System.Windows.Input.Stylus>します。  <xref:System.Windows.Input.Stylus>によって普及したペン入力は、[!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、マウスを使用して、マウスとしてスタイラスを処理することができます[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]が[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]もキーボードとマウスのようなモデルを使用するスタイラス デバイス抽象クラスを公開します。  スタイラスに関連する[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]「スタイラス」という単語が含まれています。  
  
 スタイラス動作できるため、マウスとして、マウスの入力だけをサポートするアプリケーションことができますまだスタイラス サポートのいくつかのレベルを自動的に取得します。 このような方法でスタイラスを使用すると、アプリケーションは、適切なスタイラス イベントを処理する機会が与えられ、対応するマウス イベントを処理します。 さらに、上位レベル サービスのインク入力などもスタイラス デバイスの抽象化を通じて利用できます。  入力としてのインクの使用に関する詳細については、次を参照してください。[インクの概要](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md)します。  
  
<a name="event_routing"></a>   
## <a name="event-routing"></a>イベントのルーティング  
 A <xref:System.Windows.FrameworkElement>要素のツリーを形成する、コンテンツ モデル内の子要素としての他の要素を含めることができます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、親要素は、イベントを処理してその子要素またはその他の子孫に対する入力に参加できます。 これは、小さいコントロールからコントロールの「コントロール合成に」または「合成」と呼ばれるプロセスを構築するために特に便利です。 要素ツリーおよび要素ツリーがイベントのルートに関連付ける方法の詳細については、次を参照してください。 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)します。  
  
 イベント ルーティング、複数の要素にイベントを転送するプロセスは、特定のオブジェクトまたは経路上の要素は、別の要素によって供給される場合があるイベントを (処理を介して) 重要な応答を提供するを選択できるようにします。  ルーティングされたイベントを使用して次の&3; つのルーティング メカニズムのいずれか: 直接、バブル、トンネリングします。  直接ルーティングでは、ソース要素は、通知を受け取る、唯一の要素と、イベントは、他の要素にルーティングします。 ただし、直接ルーティングされたイベントは、追加機能が標準ではなくルーティング イベントの存在のみをいくつかまだを[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベントです。 最初に通知し、イベントのソース要素と親要素で、要素ツリーをバブルは機能します。  トンネリングでは、要素ツリーのルートから開始し、元のソース要素で終わるダウンしている動作します。  ルーティングされたイベントの詳細については、次を参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]入力イベントは、通常、トンネル イベントおよびバブル イベントから成るペアになっています。  トンネル イベントには、バブル イベント「プレビュー」プレフィックスでは区別されます。  たとえば、 <xref:System.Windows.Input.Mouse.PreviewMouseMove>マウス移動イベントのトンネルのバージョンと<xref:System.Windows.Input.Mouse.MouseMove>バブル バージョンは、このイベントは、です。 要素レベルで実装があり、固有の機能のではない規則は、このイベントを組み合わせる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント システムです。 詳細については、入力イベントを WPF」セクションを参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)します。  
  
<a name="handling_input_events"></a>   
## <a name="handling-input-events"></a>入力イベントの処理  
 要素に入力を提供するには、イベント ハンドラーがその特定のイベントに関連付けられたあります。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]これは簡単です。 このイベントを待機する要素の属性として、イベントの名前を参照します。  次に、デリゲートに基づいて、定義するイベント ハンドラーの名前に属性の値を設定します。  イベント ハンドラーをなど、コードで記述する必要があります[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]分離コード ファイルに含めることができます。  
  
 キーボード イベントは、オペレーティング システムがある要素にキーボード フォーカスがあるときに発生した主なアクションをレポートするときに発生します。 マウスおよびスタイラス イベントはそれぞれが&2; つのカテゴリに分類されます。 ポインターの位置が、要素に相対的な変更を報告するイベントとデバイスのボタンの状態の変更を報告するイベントです。  
  
### <a name="keyboard-input-event-example"></a>キーボード入力イベントの例  
 次の例は、左矢印キーを押すを待機します。  A <xref:System.Windows.Controls.StackPanel>が作成されるが、<xref:System.Windows.Controls.Button>します。  左矢印キーを押すに接続されているを待機するイベント ハンドラー、<xref:System.Windows.Controls.Button>インスタンス。  
  
 例では、最初のセクションを作成、 <xref:System.Windows.Controls.StackPanel>と<xref:System.Windows.Controls.Button>のイベント ハンドラーをアタッチし、 <xref:System.Windows.UIElement.KeyDown>します。  
  
 [!code-xml[InputOvw#Input_OvwKeyboardExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]  
  
 2 番目のセクションでは、コードで記述し、イベント ハンドラーを定義します。  左方向キーが押されたとき、 <xref:System.Windows.Controls.Button>キーボード フォーカス、ハンドラーが実行されますと<xref:System.Windows.Controls.Control.Background%2A>の色、<xref:System.Windows.Controls.Button>が変更されました。  場合は、キーが押されたが、左矢印キーではありません、<xref:System.Windows.Controls.Control.Background%2A>の色、<xref:System.Windows.Controls.Button>開始色に変更します。  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]  
  
### <a name="mouse-input-event-example"></a>マウス入力イベントの例  
 次の例では、<xref:System.Windows.Controls.Control.Background%2A>の色、<xref:System.Windows.Controls.Button>は、マウス ポインターが入ったときに変更、<xref:System.Windows.Controls.Button>します。  <xref:System.Windows.Controls.Control.Background%2A>色が復元されるは、マウスが離れるときに、<xref:System.Windows.Controls.Button>します。  
  
 例では、最初のセクションを作成、 <xref:System.Windows.Controls.StackPanel>と<xref:System.Windows.Controls.Button>を制御し、イベント ハンドラーをアタッチ、 <xref:System.Windows.UIElement.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベントを<xref:System.Windows.Controls.Button>します。  
  
 [!code-xml[InputOvw#Input_OvwMouseExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]  
  
 例では、2 番目のセクションでは、コードで記述し、イベント ハンドラーを定義します。  マウスを移動したときに、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Control.Background%2A>の色、<xref:System.Windows.Controls.Button>に変更されます[<xref:System.Windows.Media.Brushes.SlateGray%2A>します。  マウスが離れるときに、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Control.Background%2A>の色、<xref:System.Windows.Controls.Button>に変更<xref:System.Windows.Media.Brushes.AliceBlue%2A>します。  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]  
  
<a name="text_input"></a>   
## <a name="text-input"></a>テキスト入力  
 <xref:System.Windows.ContentElement.TextInput>イベントでは、デバイスに依存しない方法でテキストの入力をリッスンすることができます。 キーボードは、テキストの入力、音声認識、手書きの主要な手段と他の入力デバイスにもテキスト入力を生成できます。  
  
 キーボード入力を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]まず送信して、適切な<xref:System.Windows.ContentElement.KeyDown>/<xref:System.Windows.ContentElement.KeyUp>イベントです。 これらのイベントが処理されないと、キーが (方向矢印などのコントロール キー) またはファンクション キーではなくテキスト、 <xref:System.Windows.ContentElement.TextInput>イベントが発生します。  常に単純な一対一マッピングの間ではない<xref:System.Windows.ContentElement.KeyDown>/<xref:System.Windows.ContentElement.KeyUp>と<xref:System.Windows.ContentElement.TextInput>イベントのため、複数のキーが入力されたテキストの単一文字を生成し、単一のキー操作で複数の文字の文字列を生成できます。  これを使用して、中国語、日本語、韓国語などの言語の場合に特に[!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)]を対応するアルファベットで使用可能な文字数千を生成します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]送信、 <xref:System.Windows.ContentElement.KeyUp>/<xref:System.Windows.ContentElement.KeyDown>イベント、<xref:System.Windows.Input.KeyEventArgs.Key%2A>に設定されている<xref:System.Windows.Input.Key?displayProperty=fullName>場合は、キーストロークがの一部になる可能性があります、 <xref:System.Windows.ContentElement.TextInput>イベント (alt キーを押しながら S キーが押された場合、たとえば)。 これにより、コードで、 <xref:System.Windows.ContentElement.KeyDown>をチェックするイベント ハンドラー <xref:System.Windows.Input.Key?displayProperty=fullName>し見つかると、発生した後のハンドラーの処理のままの場合は、 <xref:System.Windows.ContentElement.TextInput>イベントです。 これらのケースのさまざまなプロパティで、 <xref:System.Windows.Input.TextCompositionEventArgs>を引数の使用を元のキー入力を特定します。 同様に場合、[!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)]アクティブになっている<xref:System.Windows.Input.Key>プロパティの値を持つ<xref:System.Windows.Input.Key?displayProperty=fullName>、および<xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A>元のキーストロークやキー入力を提供します。  
  
 次の例のハンドラーを定義する、 <xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントとハンドラーを<xref:System.Windows.UIElement.KeyDown>イベントです。  
  
 コードまたはマークアップの最初のセグメントでは、ユーザー インターフェイスを作成します。  
  
 [!code-xml[InputOvw#Input_OvwTextInputXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]  
  
 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]  
  
 コードの&2; つ目のセグメントには、イベント ハンドラーが含まれています。  
  
 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]  
  
 入力イベントがイベントのルーティングをバブルアップため、 <xref:System.Windows.Controls.StackPanel>のどの要素に関係なくキーボード フォーカスがある入力を受け取ります。 <xref:System.Windows.Controls.TextBox>コントロールが最初に通知と`OnTextInputKeyDown`場合にのみ、ハンドラーが呼び出されます、 <xref:System.Windows.Controls.TextBox>入力を処理できませんでした。 場合、 <xref:System.Windows.UIElement.PreviewKeyDown>の代わりにイベントを使用、 <xref:System.Windows.UIElement.KeyDown> 、イベント、`OnTextInputKeyDown`ハンドラーが最初に呼び出されます。  
  
 この例では、処理ロジックの&2; 倍が書かれて —&1; つと時刻を ctrl キーを押しながら O、もう一度ボタンのイベント をクリックします。 入力イベントを直接処理する代わりに、コマンドを使用して、簡素化できます。  この概要と、コマンドが説明した[コマンドの実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)します。  
  
<a name="touch_and_manipulation"></a>   
## <a name="touch-and-manipulation"></a>タッチと操作  
 新しいハードウェアと Windows 7 オペレーティング システム内の API は、アプリケーションに同時に複数のタッチからの入力を受信する機能を提供します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]検出し、タッチが行われたときにイベントを発生させることによって、マウスやキーボードなど、他の入力に応答する場合と同様に、タッチ対応のアプリケーションを有効にします。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]タッチが発生したときのイベントの&2; つの型を公開します。 タッチ イベントと操作イベントです。 タッチ イベントでは、タッチ スクリーンとその動きにそれぞれの指の生データを提供します。 操作イベントは、入力を特定のアクションとして解釈されます。 イベントの両方の種類については、このセクションで説明します。  
  
### <a name="prerequisites"></a>必須コンポーネント  
 タッチに応答するアプリケーションを開発する次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]。  
  
-   Windows 7 です。  
  
-   Windows タッチをサポートするタッチ スクリーンなどのデバイス。  
  
### <a name="terminology"></a>用語  
 次の用語は、タッチが説明されているときに使用されます。  
  
-   **タッチ**は Windows 7 で認識されるユーザー入力の型です。 通常は、タッチは、タッチを検知画面に指を配置することによって開始されます。 ラップトップ コンピューターで一般的なタッチ パッドなどのデバイスはサポートしていないことタッチ デバイスは、指の位置とマウス入力の動きに単に変換する場合に注意してください。  
  
-   **マルチタッチ**同時に複数のポイントから行われるタッチです。 Windows 7 と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マルチタッチをサポートしています。 タッチのドキュメントで説明するときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マルチタッチに概念を適用します。  
  
-   A**操作**タッチがオブジェクトに適用されている物理操作として解釈されるときに発生します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、操作イベントは、変換、拡張、または回転操作としての入力を解釈します。  
  
-   A`touch device`タッチ スクリーンで&1; 本の指など、タッチ入力を生成するデバイスを表します。  
  
### <a name="controls-that-respond-to-touch"></a>タッチに応答するコントロール  
 次のコントロールにスクロールされて見えないコンテンツがある場合、コントロール全体に指をドラッグしてスクロールできます。  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.DataGrid>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
 <xref:System.Windows.Controls.ScrollViewer>を定義、 <xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=fullName>添付プロパティが有効かどうかタッチ パンは、水平、垂直方向に、これらの両方またはどちらも指定することができます。 <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=fullName>プロパティは、どの程度の速度、スクロール速度が低下し、ユーザーがタッチ スクリーンから指を離したときを指定します。 <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=fullName>添付プロパティは、スクロール オフセット平行移動操作オフセットとの比率を指定します。  
  
### <a name="touch-events"></a>タッチ イベント  
 基本クラス<xref:System.Windows.UIElement>、 <xref:System.Windows.UIElement3D>、および<xref:System.Windows.ContentElement>、サブスクライブしていることができますので、アプリケーションが応答する、タッチ イベントを定義します。 タッチ イベントは、アプリケーション オブジェクトの操作以外のものとしてタッチを解釈する場合に便利です。 たとえば、アプリケーションを&1; つまたは複数の指を描くには、ユーザーの使用は、タッチ イベントにサブスクライブです。  
  
 次の&3; つのすべてのクラスは、次のイベントを定義するクラスに関係なく同じように、動作を定義します。  
  
-   <xref:System.Windows.UIElement.TouchDown>  
  
-   <xref:System.Windows.UIElement.TouchMove>  
  
-   <xref:System.Windows.UIElement.TouchUp>  
  
-   <xref:System.Windows.UIElement.TouchEnter>  
  
-   <xref:System.Windows.UIElement.TouchLeave>  
  
-   <xref:System.Windows.UIElement.PreviewTouchDown>  
  
-   <xref:System.Windows.UIElement.PreviewTouchMove>  
  
-   <xref:System.Windows.UIElement.PreviewTouchUp>  
  
-   <xref:System.Windows.UIElement.GotTouchCapture>  
  
-   <xref:System.Windows.UIElement.LostTouchCapture>  
  
 キーボードとマウス イベントと同様には、タッチ イベントは、ルーティングされたイベントです。 始まるイベント`Preview`で始まるイベントとイベントにトンネリング`Touch`バブリング イベントです。 ルーティングされたイベントの詳細については、次を参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)します。 これらのイベントを処理する場合を呼び出して、任意の要素を基準とした、入力の位置を取得できます、 <xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A>または<xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A>メソッドです。  
  
 タッチ イベント間の相互作用を理解するには、シナリオを考えます、ユーザーを要素に&1; 本の指を設定、要素では、指を動かした要素から指を離したします。 次の図は、バブル イベント (トンネルのイベントは、わかりやすくするため省略される) の実行を示しています。  
  
 ![タッチ イベントのシーケンス。](../../../../docs/framework/wpf/advanced/media/ndp-touchevents.png "NDP_TouchEvents")  
タッチ イベント  
  
 次の一覧では、上の図でイベントの順序について説明します。  
  
1.  <xref:System.Windows.UIElement.TouchEnter>イベントを要素にユーザーが指を設定すると、1 回発生します。  
  
2.  <xref:System.Windows.UIElement.TouchDown>イベント&1; 回発生します。  
  
3.  <xref:System.Windows.UIElement.TouchMove>要素内で指を動かしたときにイベントが複数回を発生します。  
  
4.  <xref:System.Windows.UIElement.TouchUp>イベント、ユーザーが、要素から指を離したときに&1; 回発生します。  
  
5.  <xref:System.Windows.UIElement.TouchLeave>イベント&1; 回発生します。  
  
 複数の&2; 本の指を使用している場合、それぞれの指のイベントが発生します。  
  
### <a name="manipulation-events"></a>操作イベント  
 アプリケーションが、オブジェクトを操作するユーザーを有効の場合、 <xref:System.Windows.UIElement>クラスは、操作イベントを定義します。 タッチの位置のレポートを簡単にタッチ イベントとは異なり、操作イベントは、入力の解釈方法を報告します。 ストアには、操作、変換、拡張、および回転の&3; 種類があります。 次の一覧では、3 種類の操作を呼び出す方法について説明します。  
  
-   オブジェクト上に指を置き、平行移動操作を呼び出すためのタッチ スクリーンで指を移動します。 これは通常、オブジェクトを移動します。  
  
-   オブジェクトに&2; 本の指を配置し、離したり近づけたり拡大と縮小操作を呼び出すために、指を移動します。 通常、これのサイズは、オブジェクトを変更します。  
  
-   オブジェクトを&2; 本の指を保存し、本の指の周りの回転操作を呼び出すために互いを回転します。 これは通常、オブジェクトを回転します。  
  
 操作の&1; つ以上の型に同時に発生します。  
  
 オブジェクトを操作に応答すると、オブジェクトが、慣性があることができます。 物理世界をシミュレーションして、オブジェクトがあることがあります。 たとえば、ハードにプッシュする場合に、テーブル上でブックをプッシュした場合はすぎると、書籍は引き続き、リリース後に移動します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]オブジェクトからユーザーの指を離した後に操作イベントを発生させることによってこの動作をシミュレートできます。  
  
 ユーザーが移動、サイズ変更、およびオブジェクトを回転させることができるアプリケーションを作成する方法については、次を参照してください。[チュートリアル: 初めてのタッチ アプリケーションの作成](../../../../docs/framework/wpf/advanced/walkthrough-creating-your-first-touch-application.md)します。  
  
 <xref:System.Windows.UIElement>次の操作イベントを定義します。  
  
-   <xref:System.Windows.UIElement.ManipulationStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationStarted>  
  
-   <xref:System.Windows.UIElement.ManipulationDelta>  
  
-   <xref:System.Windows.UIElement.ManipulationInertiaStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationCompleted>  
  
-   <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>  
  
 既定では、 <xref:System.Windows.UIElement>これらの操作イベントを受信しません。 操作イベントを受信する、 <xref:System.Windows.UIElement>、 <xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=fullName>に`true`します。  
  
#### <a name="the-execution-path-of-manipulation-events"></a>操作イベントの実行パス  
 ここでユーザー「オブジェクトをスロー」シナリオを検討してください。 短距離間のタッチ スクリーンで指を移動するユーザー、オブジェクト上に指を置きし、移動中に指を離します。 この結果は、オブジェクトがユーザーの指の下に移動し、ユーザーが指を離した後を移動しているです。  
  
 次の図は、操作イベントと各イベントに関する重要な情報の実行パスを示します。  
  
 ![操作イベントのシーケンス。](../../../../docs/framework/wpf/advanced/media/ndp-manipulationevents.png "NDP_ManipulationEvents")  
操作イベント  
  
 次の一覧では、上の図でイベントの順序について説明します。  
  
1.  <xref:System.Windows.UIElement.ManipulationStarting>イベント オブジェクトのユーザーが指を置いたときに発生します。 このイベントでは特に、使用する設定、 <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>プロパティです。 後続のイベントで、操作の位置が基準にでは、 <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>します。 以外のイベントで<xref:System.Windows.UIElement.ManipulationStarting>、このプロパティは読み取り専用ため、 <xref:System.Windows.UIElement.ManipulationStarting>イベントは、このプロパティを設定するだけの時間。  
  
2.  <xref:System.Windows.UIElement.ManipulationStarted>イベントが次に発生します。 このイベントは、操作の始点を報告します。  
  
3.  <xref:System.Windows.UIElement.ManipulationDelta>イベントがタッチ スクリーンでユーザーの指の移動として複数回に発生します。 <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>のプロパティ、 <xref:System.Windows.Input.ManipulationDeltaEventArgs>クラスは、操作が、移動、拡張、または平行移動として解釈されるかどうかを報告します。 これは、ほとんどのオブジェクトを操作するための作業を実行する場所です。  
  
4.  <xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント、ユーザーの指のオブジェクトとの接続が失われるときに発生します。 このイベントでは、慣性による処理中の操作の減速を指定することができます。 これは、オブジェクトから選択した場合、別の物理領域または属性をエミュレートできますのでです。 たとえば、アプリケーションには、現実世界のアイテムを表す&2; つのオブジェクトが含まれているし、もう一方よりも&1; つです。 重いオブジェクトを軽量のオブジェクトよりも高速減速を行うことができます。  
  
5.  <xref:System.Windows.UIElement.ManipulationDelta>慣性を実行すると、イベントが複数回を発生します。 このイベントは発生、ユーザーの指がタッチ スクリーンの間で移動するとき、およびメモ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]慣性をシミュレートします。 つまり、 <xref:System.Windows.UIElement.ManipulationDelta>前に、と後に発生する、 <xref:System.Windows.UIElement.ManipulationInertiaStarting>イベントです。 <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=fullName>プロパティ レポートかどうか、 <xref:System.Windows.UIElement.ManipulationDelta>そのプロパティをチェックし、その値に応じて、さまざまなアクションを実行できるように、イベントが、慣性の中に発生します。  
  
6.  <xref:System.Windows.UIElement.ManipulationCompleted>イベントが発生して、慣性の操作が終了した場合。 後のすべて、 <xref:System.Windows.UIElement.ManipulationDelta>イベントが発生する、 <xref:System.Windows.UIElement.ManipulationCompleted>イベントは、操作が完了したことを通知するために発生します。  
  
 <xref:System.Windows.UIElement>も定義して、 <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>イベントです。 このイベントが発生したときに、 <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A>メソッドが呼び出される、 <xref:System.Windows.UIElement.ManipulationDelta>イベントです。 <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>イベント オブジェクトの境界に達すると、視覚的なフィードバックを提供するには、アプリケーションまたはコンポーネントを有効にします。 たとえば、<xref:System.Windows.Window>クラスのハンドル、 <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>を若干移動の端が発生した場合にウィンドウが発生するイベントです。  
  
 呼び出して、操作を取り消すことができます、<xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>メソッドを除く任意の操作イベントのイベント引数を<xref:System.Windows.UIElement.ManipulationBoundaryFeedback>イベントです。 呼び出すと<xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>操作イベントが発生した不要になった、およびタッチのマウス イベントが発生します。 次の表では、時間が、操作が取り消されると発生するマウス イベント間のリレーションシップについて説明します。  
  
|キャンセルが呼び出されるイベント|入力が既に発生したために発生するマウス イベント|  
|----------------------------------------|-----------------------------------------------------------------|  
|<xref:System.Windows.UIElement.ManipulationStarting>と<xref:System.Windows.UIElement.ManipulationStarted>|マウス ダウン イベント。|  
|<xref:System.Windows.UIElement.ManipulationDelta>|マウス ボタンを押す、マウス イベントに移動します。|  
|<xref:System.Windows.UIElement.ManipulationInertiaStarting>と<xref:System.Windows.UIElement.ManipulationCompleted>|マウスの移動、およびマウス イベント アップ ダウン マウスです。|  
  
 呼び出す場合<xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>メソッドが返す操作は、慣性が、`false`入力では、マウス イベントは発生しません。  
  
### <a name="the-relationship-between-touch-and-manipulation-events"></a>タッチと操作イベント間のリレーションシップ  
 A <xref:System.Windows.UIElement>タッチ イベントを常に表示されることができます。 ときに、 <xref:System.Windows.UIElement.IsManipulationEnabled%2A>にプロパティが設定されている`true`、 <xref:System.Windows.UIElement>タッチと操作の両方のイベントを受け取ることができます。  場合、<xref:System.Windows.UIElement.TouchDown>イベントが処理されない (つまり、 <xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティは、 `false`)、操作のロジックが要素にタッチをキャプチャし、操作イベントを生成します。 場合、 <xref:System.Windows.RoutedEventArgs.Handled%2A>にプロパティが設定されている`true`で、<xref:System.Windows.UIElement.TouchDown>イベント、操作のロジックが操作イベントを生成しません。 次の図は、タッチ イベントと操作イベント間のリレーションシップを示しています。  
  
 ![タッチ イベントと操作イベント間のリレーションシップ](../../../../docs/framework/wpf/advanced/media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents")  
タッチ イベントと操作イベント  
  
 次の一覧では、前の図に示されているタッチ、および操作のイベント間の関係について説明します。  
  
-   最初のタッチ デバイスが生成するとき、<xref:System.Windows.UIElement.TouchDown>でイベントを<xref:System.Windows.UIElement>、操作のロジックが、 <xref:System.Windows.UIElement.CaptureTouch%2A>を生成するメソッド、 <xref:System.Windows.UIElement.GotTouchCapture>イベントです。  
  
-   ときに、 <xref:System.Windows.UIElement.GotTouchCapture>発生すると、操作のロジックが、 <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=fullName>を生成するメソッド、 <xref:System.Windows.UIElement.ManipulationStarting>イベントです。  
  
-   ときに、 <xref:System.Windows.UIElement.TouchMove>イベントが発生した、操作のロジックを生成、 <xref:System.Windows.UIElement.ManipulationDelta>する前に発生するイベント、 <xref:System.Windows.UIElement.ManipulationInertiaStarting>イベントです。  
  
-   最後デバイスをタッチすると、要素を発生させます、<xref:System.Windows.UIElement.TouchUp>イベント、操作のロジックを生成、 <xref:System.Windows.UIElement.ManipulationInertiaStarting>イベントです。  
  
<a name="focus"></a>   
## <a name="focus"></a>フォーカス  
 フォーカスに関連する&2; つの主要な概念がある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: キーボード フォーカスと論理フォーカスします。  
  
### <a name="keyboard-focus"></a>キーボード フォーカス  
 キーボード フォーカスはキーボード入力を受け取る要素を指します。  1 つだけ要素デスクトップ全体でキーボード フォーカスがあることができます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、キーボード フォーカスを持つ要素がある<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>設定`true`します。  静的な<xref:System.Windows.Input.Keyboard>メソッド<xref:System.Windows.Input.Keyboard.FocusedElement%2A>キーボード フォーカスされている要素を返します。  
  
 要素のタブ オーダーをかなど、特定の要素上にマウス ポインターをクリックして、キーボード フォーカスを取得できます、 <xref:System.Windows.Controls.TextBox>します。  キーボード フォーカスを使用してプログラムを使用して取得も可能、<xref:System.Windows.Input.Keyboard.Focus%2A>メソッドを<xref:System.Windows.Input.Keyboard>クラスです。  <xref:System.Windows.Input.Keyboard.Focus%2A>キーボード フォーカスの指定した要素を提供しようとします。  によって返される要素<xref:System.Windows.Input.Keyboard.Focus%2A>キーボード フォーカスされている要素です。  
  
 キーボード フォーカスを取得する要素の順序で、 <xref:System.Windows.UIElement.Focusable%2A>プロパティおよび<xref:System.Windows.UIElement.IsVisible%2A>にプロパティを設定する必要があります**true**します。  などのいくつかのクラス<xref:System.Windows.Controls.Panel>が<xref:System.Windows.UIElement.Focusable%2A>に設定`false`既定ではこのため、ありますこのプロパティを設定する`true`する場合はその要素にフォーカスを取得できません。  
  
 次の例では使用<xref:System.Windows.Input.Keyboard.Focus%2A>キーボード フォーカスを設定する、<xref:System.Windows.Controls.Button>します。  アプリケーションの初期フォーカスを設定することをお勧めの場所は、 <xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーです。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 キーボード フォーカスの詳細については、次を参照してください。[フォーカス概要](../../../../docs/framework/wpf/advanced/focus-overview.md)します。  
  
### <a name="logical-focus"></a>論理フォーカス  
 論理フォーカスとは、 <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=fullName>フォーカス範囲内です。  アプリケーションでは、論理フォーカスのある複数の要素がありますされる可能性しますが、ありますのみ特定のフォーカスの範囲で論理フォーカスのある&1; つの要素。  
  
 フォーカス範囲を追跡するコンテナー要素とは、 <xref:System.Windows.Input.FocusManager.FocusedElement%2A>そのスコープ内で。  フォーカスは、フォーカスの範囲を離れる、フォーカスがある要素にキーボード フォーカスは失われますが、論理フォーカスを保持します。  フォーカスのスコープに戻ると、フォーカスがある要素はキーボード フォーカスを取得します。  これにより、複数のフォーカス範囲の間で変更にキーボード フォーカスが、フォーカス範囲内でフォーカスがある要素がフォーカスが戻るときに、フォーカスがある要素がすることを保証します。  
  
 フォーカスの範囲内に要素を変換できます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を設定して、 <xref:System.Windows.Input.FocusManager>添付プロパティ<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>に`true`、またはコードを使用して添付プロパティを設定して、 <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>メソッドです。  
  
 次の例では、 <xref:System.Windows.Controls.StackPanel>を設定してフォーカス スコープ内に、 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A>添付プロパティです。  
  
 [!code-xml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 内のクラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は既定でフォーカス範囲である<xref:System.Windows.Window>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.ToolBar>、および<xref:System.Windows.Controls.ContextMenu>します。  
  
 キーボード フォーカスを持つ要素には、; に属しているフォーカス範囲の論理フォーカスがあります。したがって、と共に要素にフォーカスを設定する、<xref:System.Windows.Input.Keyboard.Focus%2A>メソッドを<xref:System.Windows.Input.Keyboard>要素キーボード フォーカス、論理フォーカスを提供するクラスまたは基本要素クラスを試みます。  
  
 フォーカスの範囲内のフォーカスがある要素を調べるには使用<xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>します。 フォーカスのスコープにフォーカスがある要素を変更するには、使用<xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>します。  
  
 論理フォーカスの詳細については、次を参照してください。[フォーカス概要](../../../../docs/framework/wpf/advanced/focus-overview.md)します。  
  
<a name="mouse_position"></a>   
## <a name="mouse-position"></a>マウスの位置  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]入力[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]の座標空間に関して役に立つ情報を提供します。  たとえば、調整`(0,0)`は左上隅の座標が、ツリー内のどの要素の左上隅ですか? 入力先である要素。 イベント ハンドラーに関連付けられている要素ですか。 または、別のものですか。 混乱を避けるために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]入力[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]マウス経由で取得した座標に使用する場合は、参照、フレームを指定することが必要です。 <xref:System.Windows.Input.Mouse.GetPosition%2A>メソッドは、指定した要素に相対的なマウス ポインターの座標を返します。  
  
<a name="mouse_capture"></a>   
## <a name="mouse-capture"></a>マウスのキャプチャ  
 具体的には、マウス デバイスは、マウスのキャプチャと呼ばれるモーダル特性を保持します。 マウスのキャプチャはその他の操作画面に表示される、基準に関連するマウス ポインターの位置が必ずしも行われないように、ドラッグ アンド ドロップ操作が開始されると、入力の遷移状態を維持するために使用されます。 ドラッグ中に、ユーザーは、ドラッグ アンド ドロップ、マウスのキャプチャがドラッグ元によって保持されている間、ほとんどのマウスを置いたときのキューを不適切なためを中止せずクリックしてできません。 入力システムを公開[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]マウスのキャプチャの状態を決定するだけでなく[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]強制的に特定の要素をマウスのキャプチャまたはマウスのキャプチャ状態をオフにすることができます。 ドラッグ アンド ドロップ操作の詳細については、次を参照してください。[ドラッグ アンド ドロップの概要](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)します。  
  
<a name="commands"></a>   
## <a name="commands"></a>コマンド  
 コマンドは、デバイスの入力よりもより意味的なレベルでの入力の処理を有効にします。  コマンドは、単純なディレクティブなど`Cut`、 `Copy`、 `Paste`、または`Open`です。  コマンドは、コマンド ロジックを集中管理するために便利です。  アクセスできるように、同じコマンド、<xref:System.Windows.Controls.Menu>の<xref:System.Windows.Controls.ToolBar>、または、ショートカット キー。 コマンドには、コマンドが使用できなくなったときに、コントロールを無効にするためのメカニズムも提供します。  
  
 <xref:System.Windows.Input.RoutedCommand>は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装<xref:System.Windows.Input.ICommand>します。  ときに、 <xref:System.Windows.Input.RoutedCommand>が実行される、 <xref:System.Windows.Input.CommandManager.PreviewExecuted>と<xref:System.Windows.Input.CommandManager.Executed>イベントがどのトンネルおよび要素ツリーでバブルのようなその他の入力のコマンドのターゲットで発生します。  コマンド ターゲットが設定されていない場合は、キーボード フォーカスを持つ要素がコマンドの対象となります。  コマンドを実行するロジックに接続されている、 <xref:System.Windows.Input.CommandBinding>します。  ときに、 <xref:System.Windows.Input.CommandManager.Executed>イベントに達すると、 <xref:System.Windows.Input.CommandBinding> 、特定のコマンド、 <xref:System.Windows.Input.ExecutedRoutedEventHandler>で、 <xref:System.Windows.Input.CommandBinding>が呼び出されます。  このハンドラーは、コマンドの操作を実行します。  
  
 コマンド実行の詳細については、次を参照してください。[コマンドの実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]構成される一般的なコマンドのライブラリが用意されて<xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.MediaCommands>、 <xref:System.Windows.Input.ComponentCommands>、 <xref:System.Windows.Input.NavigationCommands>、および<xref:System.Windows.Documents.EditingCommands>、独自に定義することもできます。  
  
 次の例を設定する方法を示しています、 <xref:System.Windows.Controls.MenuItem>が呼び出すことがクリックされたとき、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンドを<xref:System.Windows.Controls.TextBox>と見なし、 <xref:System.Windows.Controls.TextBox>キーボード フォーカスがあります。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
 内のコマンドの詳細については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[コマンドの実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)します。  
  
<a name="the_input_system_and_base_elements"></a>   
## <a name="the-input-system-and-base-elements"></a>入力システムと基本要素  
 入力イベントによって定義された接続されているイベントなど、<xref:System.Windows.Input.Mouse>、<xref:System.Windows.Input.Keyboard>、および<xref:System.Windows.Input.Stylus>クラスが入力システムによって生成され、ヒット実行時に、ビジュアル ツリーをテストに基づくオブジェクト モデルの特定の位置に挿入します。  
  
 各イベントを<xref:System.Windows.Input.Mouse>、<xref:System.Windows.Input.Keyboard>、および<xref:System.Windows.Input.Stylus>基本要素のクラスはアタッチされるイベントを再公開も、定義<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>として新しいルーティングされたイベント。 基本要素のルーティング イベントは、元のアタッチされるイベントを処理し、イベント データを再利用するクラスによって生成されます。  
  
 入力イベントは、基本要素の入力イベントの実装を通じて特定のソース要素に関連付けられてになるは、論理とビジュアル ツリーのオブジェクトの組み合わせに基づいており、アプリケーション コードで処理できるイベント ルートの残りの部分を介してルーティングすることができます。  一般に、各デバイスに関連する入力イベント処理にルーティングされたイベントを使用する方が便利です<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>より直感的なイベント ハンドラーの構文両方で使用できるため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]およびコード。 代わりに、プロセスを開始した、接続されているイベントを処理することもできますが、いくつかの問題が発生するとします。 基本要素のクラス処理によって、添付されたイベントをマークすると、アタッチされるイベントのハンドラーを接続するために実際のイベントの構文ではなく、アクセサー メソッドを使用する必要があります。  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>次の内容  
 いくつかの手法の入力を処理するようになりましたがある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  さまざまな種類の入力イベント、およびによって使用されるルーティングされたイベント メカニズムをよりよく把握も必要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
 その他のリソースがあることを説明する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フレームワーク要素やイベントの詳細にルーティングします。 詳細については、次の概要を参照して[コマンドの実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)、[フォーカス概要](../../../../docs/framework/wpf/advanced/focus-overview.md)、 [Base 要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)、 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)、および[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)します。  
  
## <a name="see-also"></a>関連項目  
 [フォーカスの概要](../../../../docs/framework/wpf/advanced/focus-overview.md)   
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [ルーティングされたイベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [プロパティ](../../../../docs/framework/wpf/advanced/properties-wpf.md)