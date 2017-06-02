---
title: "フォーカスの概要 | Microsoft Docs"
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
  - "アプリケーション, フォーカス"
  - "フォーカスを設定 (アプリケーションに)"
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# フォーカスの概要
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、キーボード フォーカスと論理フォーカスという、フォーカスに関する 2 つの主要な概念があります。  キーボード フォーカスはキーボード入力を受け取る要素を表し、論理フォーカスはフォーカスを持つフォーカス範囲内の要素を表します。  これらの概念については、この概要で詳しく説明します。  フォーカスを取得可能な領域を複数持つ複雑なアプリケーションを作成する場合は、これらの概念の違いを理解することが重要です。  
  
 フォーカス管理に関与する主要なクラスには、<xref:System.Windows.Input.Keyboard> クラス、<xref:System.Windows.Input.FocusManager> クラス、および <xref:System.Windows.UIElement> や <xref:System.Windows.ContentElement> などの基本要素クラスがあります。  基本要素の詳細については、「[基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard> クラスは主にキーボード フォーカスに関連し、<xref:System.Windows.Input.FocusManager> は主に論理フォーカスに関連しますが、これは絶対的な区別ではありません。  キーボード フォーカスを持つ要素は論理フォーカスも持ちますが、論理フォーカスを持つ要素は必ずしもキーボード フォーカスを持ちません。  <xref:System.Windows.Input.Keyboard> クラスを使用してキーボード フォーカスを持つ要素を設定したときには、要素に論理フォーカスも設定されるので、この違いがよくわかります。  
  
   
  
<a name="Keyboard_Focus"></a>   
## キーボード フォーカス  
 キーボード フォーカスは、現在キーボード入力を受け取っている要素を指します。  キーボード フォーカスを持つ要素は、デスクトップ全体で 1 つしかありません。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、キーボード フォーカスを持つ要素の <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> は `true` に設定されます。  <xref:System.Windows.Input.Keyboard> クラスの静的プロパティ <xref:System.Windows.Input.Keyboard.FocusedElement%2A> は、現在キーボード フォーカスを持っている要素を取得します。  
  
 要素でキーボード フォーカスを取得するためには、基本要素で <xref:System.Windows.UIElement.Focusable%2A> プロパティと <xref:System.Windows.UIElement.IsVisible%2A> プロパティを `true` に設定する必要があります。  <xref:System.Windows.Controls.Panel> 基本クラスなど一部のクラスでは <xref:System.Windows.UIElement.Focusable%2A> の既定値は `false` です。したがって、このような要素がキーボード フォーカスを取得できるようにする場合は、<xref:System.Windows.UIElement.Focusable%2A> を `true` に設定する必要があります。  
  
 キーボード フォーカスは、要素への Tab キーでの移動や特定の要素でのマウスのクリックなど、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] でのユーザー操作を通じて取得できます。  キーボード フォーカスは、<xref:System.Windows.Input.Keyboard> クラスで <xref:System.Windows.Input.Keyboard.Focus%2A> メソッドを使用してプログラムにより取得することもできます。  <xref:System.Windows.Input.Keyboard.Focus%2A> メソッドは、指定された要素にキーボード フォーカスを設定しようとします。  返される要素はキーボード フォーカスが設定された要素ですが、古いフォーカス オブジェクトまたは新しいフォーカス オブジェクトが要求をブロックする場合は、要求された要素とは異なる可能性があります。  
  
 <xref:System.Windows.Input.Keyboard.Focus%2A> メソッドを使用して、キーボード フォーカスを <xref:System.Windows.Controls.Button> に設定する例を次に示します。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 基本要素クラスの <xref:System.Windows.UIElement.IsKeyboardFocused%2A> プロパティは、要素にキーボード フォーカスがあるかどうかを示す値を取得します。  基本要素クラスの <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> プロパティは、要素またはいずれかの子ビジュアル要素にキーボード フォーカスがあるかどうかを示す値を取得します。  
  
 アプリケーションの起動時に初期フォーカスを設定する場合、フォーカスを受け取る要素は、アプリケーションによって読み込まれる初期ウィンドウのビジュアル ツリーに含まれていて、<xref:System.Windows.UIElement.Focusable%2A> と <xref:System.Windows.UIElement.IsVisible%2A> が `true` に設定されている必要があります。  初期フォーカスを設定する場所は、<xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラー内にすることをお勧めします。  <xref:System.Windows.Threading.Dispatcher> コールバックは、<xref:System.Windows.Threading.Dispatcher.Invoke%2A> または <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> を呼び出して使用することもできます。  
  
<a name="Logical_Focus"></a>   
## 論理フォーカス  
 論理フォーカスとは、フォーカス範囲内の <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=fullName> を意味します。  フォーカス範囲とは、その範囲内の <xref:System.Windows.Input.FocusManager.FocusedElement%2A> を追跡する要素です。  キーボード フォーカスがフォーカス範囲を離れると、フォーカスがある要素はキーボード フォーカスを失いますが、論理フォーカスは引き続き保持します。  キーボード フォーカスがフォーカス範囲に戻ると、フォーカスがある要素はキーボード フォーカスを得ます。  これにより、キーボード フォーカスが複数のフォーカス範囲間で変更されても、フォーカスがフォーカス範囲に戻ると、そのフォーカス範囲内のフォーカスがある要素はキーボード フォーカスを取り戻すことができます。  
  
 アプリケーションでは、複数の要素が論理フォーカスを持つことがありますが、特定のフォーカス範囲で論理フォーカスを持つ要素は 1 つだけに限られます。  
  
 キーボード フォーカスを持つ要素は、その要素が属するフォーカス範囲の論理フォーカスを持ちます。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、<xref:System.Windows.Input.FocusManager> の添付プロパティ <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> を `true` に設定することにより、要素をフォーカス範囲にすることができます。  コードでは、<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> を呼び出して、要素をフォーカス範囲にすることができます。  
  
 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> 添付プロパティを設定して、<xref:System.Windows.Controls.StackPanel> をフォーカス範囲にする例を次に示します。  
  
 [!code-xml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> は、指定した要素のフォーカス範囲を返します。  
  
 既定でフォーカス範囲になる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のクラスは、<xref:System.Windows.Window>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.ToolBar>、および <xref:System.Windows.Controls.ContextMenu> です。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> は、指定したフォーカス範囲のフォーカスを持つ要素を取得します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> は、指定したフォーカス範囲でフォーカスを持つ要素を設定します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> は、通常、最初にフォーカスを得る要素を設定するために使用します。  
  
 フォーカス範囲にフォーカスを持つ要素を設定し、フォーカス範囲のフォーカスを持つ要素を取得する例を次に示します。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## キーボード ナビゲーション  
 <xref:System.Windows.Input.KeyboardNavigation> クラスは、ナビゲーション キーのいずれかが押されたときに、既定のキーボード フォーカスのナビゲーションを実装します。  ナビゲーション キーとは、Tab、Shift \+ Tab、Ctrl \+ Tab、Ctrl \+ Shift \+ Tab、上方向、下方向、左方向、および右方向の各キーを指します。  
  
 ナビゲーション コンテナーのナビゲーション動作は、添付 <xref:System.Windows.Input.KeyboardNavigation> プロパティの <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>、<xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>、および <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> を設定することにより変更できます。  これらのプロパティは <xref:System.Windows.Input.KeyboardNavigationMode> 型であり、指定可能な値は <xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、および <xref:System.Windows.Input.KeyboardNavigationMode> です。  既定値は <xref:System.Windows.Input.KeyboardNavigationMode> です。これは、要素がナビゲーション コンテナーではないことを意味します。  
  
 複数の <xref:System.Windows.Controls.MenuItem> オブジェクトを使用して <xref:System.Windows.Controls.Menu> を作成する例を次に示します。  <xref:System.Windows.Controls.Menu> で、<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> 添付プロパティが <xref:System.Windows.Input.KeyboardNavigationMode> に設定されます。  <xref:System.Windows.Controls.Menu> 内で Tab キーを使用してフォーカスを変更すると、各要素間をフォーカスが移動し、最後の要素に達すると最初の要素にフォーカスが戻ります。  
  
 [!code-xml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## プログラムによるフォーカスのナビゲーション  
 フォーカスを操作するための追加の [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] には、<xref:System.Windows.UIElement.MoveFocus%2A> と <xref:System.Windows.UIElement.PredictFocus%2A> があります。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> は、アプリケーション内の次の要素にフォーカスを変更します。  <xref:System.Windows.Input.TraversalRequest> は、方向を指定するために使用されます。  <xref:System.Windows.UIElement.MoveFocus%2A> に渡された <xref:System.Windows.Input.FocusNavigationDirection> は、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection> などの、フォーカスを移動できる方向を指定します。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> を使用してフォーカスがある要素を変更する例を次に示します。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> は、フォーカスが変更された場合にフォーカスを受け取るオブジェクトを返します。  現在、<xref:System.Windows.FrameworkElement.PredictFocus%2A> でサポートされているのは、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection>、および <xref:System.Windows.Input.FocusNavigationDirection> だけです。  
  
<a name="Focus_Events"></a>   
## フォーカス イベント  
 キーボード フォーカスに関連するイベントには、<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> と <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>、および <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> と <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> があります。  イベントは、<xref:System.Windows.Input.Keyboard> クラスで添付イベントとして定義されますが、基本要素クラスで等価なルーティング イベントして簡単にアクセスできます。  イベントの詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> は、要素がキーボード フォーカスを受け取ったときに発生します。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> は、要素がキーボード フォーカスを失ったときに発生します。  <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> イベントまたは <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> イベントが処理され、<xref:System.Windows.RoutedEventArgs.Handled%2A> が `true` に設定されると、フォーカスは変更されなくなります。  
  
 <xref:System.Windows.UIElement.GotKeyboardFocus> イベント ハンドラーと <xref:System.Windows.UIElement.LostKeyboardFocus> イベント ハンドラーを <xref:System.Windows.Controls.TextBox> に添付する例を次に示します。  
  
 [!code-xml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 <xref:System.Windows.Controls.TextBox> がキーボード フォーカスを取得すると、<xref:System.Windows.Controls.TextBox> の <xref:System.Windows.Controls.Control.Background%2A> プロパティが <xref:System.Windows.Media.Brushes.LightBlue%2A> に変更されます。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 <xref:System.Windows.Controls.TextBox> がキーボード フォーカスを失うと、<xref:System.Windows.Controls.TextBox> の <xref:System.Windows.Controls.Control.Background%2A> プロパティが白に戻ります。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 論理フォーカスに関連するイベントには、<xref:System.Windows.UIElement.GotFocus> および <xref:System.Windows.UIElement.LostFocus> があります。  これらのイベントは、<xref:System.Windows.Input.FocusManager> で添付イベントとして定義されますが、<xref:System.Windows.Input.FocusManager> は CLR イベント ラッパーを公開しません。  これらのイベントは、<xref:System.Windows.UIElement> と <xref:System.Windows.ContentElement> によって、より使いやすい形で公開されます。  
  
## 参照  
 <xref:System.Windows.Input.FocusManager>   
 <xref:System.Windows.UIElement>   
 <xref:System.Windows.ContentElement>   
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)