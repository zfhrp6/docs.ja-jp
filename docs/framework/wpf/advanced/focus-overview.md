---
title: フォーカスの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 620839a0060469604d0affa6637c3cafac0f62c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548111"
---
# <a name="focus-overview"></a>フォーカスの概要
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、キーボード フォーカスと論理フォーカスという、フォーカスに関する 2 つの主要な概念があります。  キーボード フォーカスはキーボード入力を受け取る要素を指し、論理フォーカスはフォーカスを持つフォーカス範囲内の要素を指します。  これらの概念については、この概要で詳しく説明します。  フォーカスを取得可能な領域を複数持つ複雑なアプリケーションを作成する場合は、これらの概念の違いを理解することが重要です。  
  
 フォーカス管理に参加する主要なクラスは、<xref:System.Windows.Input.Keyboard>クラス、<xref:System.Windows.Input.FocusManager>クラス、および基本要素などのクラス、<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>です。  基本要素の詳細については、「[基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard>クラスでは、主にキーボード フォーカス、および<xref:System.Windows.Input.FocusManager>が論理フォーカスを中心に絶対の違いはありません。  キーボード フォーカスを持つ要素は論理フォーカスも持ちますが、論理フォーカスを持つ要素は必ずしもキーボード フォーカスを持ちません。  使用するときにこれが明らかなもの、<xref:System.Windows.Input.Keyboard>にキーボード フォーカスを持つ要素を設定するクラスが要素にも論理フォーカスを設定します。  
  

  
<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>キーボード フォーカス  
 キーボード フォーカスは、現在キーボード入力を受け取っている要素を指します。  キーボード フォーカスを持つ要素は、デスクトップ全体で 1 つしかありません。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、キーボード フォーカスを持つ要素がある<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>'éý'`true`です。  静的プロパティ<xref:System.Windows.Input.Keyboard.FocusedElement%2A>上、<xref:System.Windows.Input.Keyboard>クラスがキーボード フォーカスされている要素を取得します。  
  
 キーボード フォーカスを取得する要素の順序で、<xref:System.Windows.UIElement.Focusable%2A>と<xref:System.Windows.UIElement.IsVisible%2A>に基本要素のプロパティを設定する必要があります`true`です。  などのいくつかのクラス、<xref:System.Windows.Controls.Panel>基底クラスは、 <xref:System.Windows.UIElement.Focusable%2A> 'éý'`false`既定ではそのため、設定する必要あります<xref:System.Windows.UIElement.Focusable%2A>に`true`する場合はこのような要素がキーボード フォーカスを取得できます。  
  
 キーボード フォーカスは、要素への Tab キーでの移動や特定の要素でのマウスのクリックなど、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] でのユーザー操作を通じて取得できます。  キーボード フォーカスも取得できますプログラムを使用して、<xref:System.Windows.Input.Keyboard.Focus%2A>メソッドを<xref:System.Windows.Input.Keyboard>クラスです。  <xref:System.Windows.Input.Keyboard.Focus%2A>メソッドが指定した要素にキーボード フォーカスを試みます。  返される要素はキーボード フォーカスが設定された要素ですが、古いフォーカス オブジェクトまたは新しいフォーカス オブジェクトが要求をブロックする場合は、要求された要素とは異なる可能性があります。  
  
 次の例では、<xref:System.Windows.Input.Keyboard.Focus%2A>キーボード フォーカスを設定する方法、<xref:System.Windows.Controls.Button>です。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基本要素クラスのプロパティは、要素にキーボード フォーカスがあるかどうかを示す値を取得します。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基本要素クラスのプロパティは、要素またはその子ビジュアル要素のいずれかにキーボード フォーカスがあるかどうかを示す値を取得します。  
  
 フォーカスを受け取る要素が、アプリケーションによって読み込まれる最初のウィンドウのビジュアル ツリー内でなければなりませんにアプリケーションの起動時に初期フォーカスを設定するときと、要素があります<xref:System.Windows.UIElement.Focusable%2A>と<xref:System.Windows.UIElement.IsVisible%2A>'éý'`true`です。  初期フォーカスを設定することをお勧めの場所は、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。  A<xref:System.Windows.Threading.Dispatcher>コールバックは、呼び出すことによっても使用できます<xref:System.Windows.Threading.Dispatcher.Invoke%2A>または<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>です。  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>論理フォーカス  
 論理フォーカスとは、<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>フォーカス範囲内です。  フォーカス範囲を追跡する要素とは、<xref:System.Windows.Input.FocusManager.FocusedElement%2A>そのスコープ内で。  キーボード フォーカスがフォーカス範囲を離れると、フォーカスがある要素はキーボード フォーカスを失いますが、論理フォーカスは引き続き保持します。  キーボード フォーカスがフォーカス範囲に戻ると、フォーカスがある要素はキーボード フォーカスを取得します。  これにより、キーボード フォーカスが複数のフォーカス範囲間で変更されても、フォーカスがフォーカス範囲に戻ると、そのフォーカス範囲内のフォーカスがある要素はキーボード フォーカスを取り戻すことができます。  
  
 アプリケーションでは、複数の要素が論理フォーカスを持つことがありますが、特定のフォーカス範囲で論理フォーカスを持つ要素は 1 つだけに限られます。  
  
 キーボード フォーカスを持つ要素は、その要素が属するフォーカス範囲の論理フォーカスを持ちます。  
  
 フォーカス範囲に要素を変換できる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を設定して、<xref:System.Windows.Input.FocusManager>添付プロパティ<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>に`true`です。  コードでは、要素に変換できるフォーカス スコープを呼び出して<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>です。  
  
 次の例では、<xref:System.Windows.Controls.StackPanel>を設定してフォーカス スコープの中に、<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>添付プロパティ。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> 指定した要素のフォーカス スコープを返します。  
  
 内のクラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は既定でフォーカス範囲は<xref:System.Windows.Window>、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.ToolBar>、および<xref:System.Windows.Controls.ContextMenu>です。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> 指定したフォーカスの範囲のフォーカスがある要素を取得します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 指定したフォーカスのスコープ内には、フォーカスのある要素を設定します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 初期フォーカスのある要素の設定に通常使用されます。  
  
 フォーカス範囲にフォーカスを持つ要素を設定し、フォーカス範囲のフォーカスを持つ要素を取得する例を次に示します。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>キーボード ナビゲーション  
 <xref:System.Windows.Input.KeyboardNavigation>クラスは、のいずれかのナビゲーション キーが押されたときに既定のキーボード フォーカスのナビゲーションの実装を担当します。  ナビゲーション キーとは、Tab、Shift + Tab、Ctrl + Tab、Ctrl + Shift + Tab、上方向、下方向、左方向、および右方向の各キーを指します。  
  
 アタッチされたを設定してナビゲーション コンテナーのナビゲーション動作を変更できます<xref:System.Windows.Input.KeyboardNavigation>プロパティ<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>、 <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>、および<xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>です。  これらのプロパティが型<xref:System.Windows.Input.KeyboardNavigationMode>値には、 <xref:System.Windows.Input.KeyboardNavigationMode.Continue>、 <xref:System.Windows.Input.KeyboardNavigationMode.Local>、 <xref:System.Windows.Input.KeyboardNavigationMode.Contained>、 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>、 <xref:System.Windows.Input.KeyboardNavigationMode.Once>、および<xref:System.Windows.Input.KeyboardNavigationMode.None>です。  既定値は<xref:System.Windows.Input.KeyboardNavigationMode.Continue>、つまり、要素はナビゲーション コンテナーではありません。  
  
 次の例を作成、<xref:System.Windows.Controls.Menu>の数が<xref:System.Windows.Controls.MenuItem>オブジェクト。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>に添付プロパティを設定<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>上、<xref:System.Windows.Controls.Menu>です。  内で tab キーを使用して、フォーカスが変更されたときに、<xref:System.Windows.Controls.Menu>最初の要素にフォーカスが戻ります最後の要素に達したときに、フォーカスは各要素から移動します。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>プログラムによるフォーカスのナビゲーション  
 追加[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]を操作するにはフォーカスが<xref:System.Windows.UIElement.MoveFocus%2A>と<xref:System.Windows.UIElement.PredictFocus%2A>です。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> アプリケーションで次の要素にフォーカスを変更します。  A<xref:System.Windows.Input.TraversalRequest>方向を指定するために使用します。   <xref:System.Windows.Input.FocusNavigationDirection>に渡される<xref:System.Windows.UIElement.MoveFocus%2A>異なる方向フォーカスが移動可能などを示す<xref:System.Windows.Input.FocusNavigationDirection.First>、 <xref:System.Windows.Input.FocusNavigationDirection.Last>、<xref:System.Windows.Input.FocusNavigationDirection.Up>と<xref:System.Windows.Input.FocusNavigationDirection.Down>です。  
  
 次の例では<xref:System.Windows.FrameworkElement.MoveFocus%2A>フォーカスのある要素を変更します。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> フォーカスが変更された場合、フォーカスを受け取るオブジェクトを返します。  現時点では、のみ<xref:System.Windows.Input.FocusNavigationDirection.Up>、 <xref:System.Windows.Input.FocusNavigationDirection.Down>、 <xref:System.Windows.Input.FocusNavigationDirection.Left>、および<xref:System.Windows.Input.FocusNavigationDirection.Right>でサポートされている<xref:System.Windows.FrameworkElement.PredictFocus%2A>です。  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>フォーカス イベント  
 キーボード フォーカスに関連するイベントは<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>、<xref:System.Windows.Input.Keyboard.GotKeyboardFocus>と<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>、<xref:System.Windows.Input.Keyboard.LostKeyboardFocus>です。  アタッチされるイベントとイベントが定義されている、<xref:System.Windows.Input.Keyboard>クラスしますが、基本要素クラスの同等のルーティング イベントとしてより簡単にアクセスできます。  イベントの詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 要素がキーボード フォーカスを取得したときに発生します。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 要素がキーボード フォーカスを失ったときに発生します。  場合、<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>イベントまたは<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>イベントが処理されると<xref:System.Windows.RoutedEventArgs.Handled%2A>に設定されている`true`、フォーカスは変わりません。  
  
 次の例ではアタッチ<xref:System.Windows.UIElement.GotKeyboardFocus>と<xref:System.Windows.UIElement.LostKeyboardFocus>へのイベント ハンドラー、<xref:System.Windows.Controls.TextBox>です。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 ときに、<xref:System.Windows.Controls.TextBox>がキーボード フォーカスを取得、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>に変更が<xref:System.Windows.Media.Brushes.LightBlue%2A>です。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 ときに、<xref:System.Windows.Controls.TextBox>がキーボード フォーカスを失った、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>白に変更します。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 論理フォーカスに関連するイベントは<xref:System.Windows.UIElement.GotFocus>と<xref:System.Windows.UIElement.LostFocus>です。  これらのイベントがで定義された、<xref:System.Windows.Input.FocusManager>としてアタッチされるイベントは、ですが、 <xref:System.Windows.Input.FocusManager> CLR イベントのラッパーを公開しません。  <xref:System.Windows.UIElement> および<xref:System.Windows.ContentElement>これらのイベントをより簡単に公開します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Input.FocusManager>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.ContentElement>  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [基本要素の概要](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
