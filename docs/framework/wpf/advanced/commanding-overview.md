---
title: "コマンド実行の概要 | Microsoft Docs"
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
  - "クラス, CommandBinding"
  - "コマンド ライブラリ"
  - "CommandBindings"
  - "コマンド実行"
  - "CommandManager"
  - "コマンド, 定義"
  - "ICommandSource インターフェイス"
  - "インターフェイス, ICommandSource"
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# コマンド実行の概要
<a name="introduction"></a> コマンド実行は、デバイス入力よりも意味を持つレベルで入力を処理する [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の入力機構です。  コマンドの例としては、多くのアプリケーションで目にする **\[コピー\]**、**\[切り取り\]**、**\[貼り付け\]** などの操作があります。  
  
 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にはどんなコマンドがあるか、コマンド実行モデルに含まれるクラス、およびアプリケーションでコマンドを使用および作成する方法について説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [コマンドとは](#commands_at_10000_feet)  
  
-   [WPF の簡単なコマンドの例](#simple_command)  
  
-   [WPF のコマンド実行の 4 つの主要な概念](#Four_main_Concepts)  
  
-   [コマンド ライブラリ](#Command_Library)  
  
-   [カスタム コマンドの作成](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## コマンドとは  
 コマンドにはいくつかの目的があります。  最初の目的は、コマンドを呼び出すセマンティクスとオブジェクトを、コマンドを実行するロジックから分離することです。  これにより、複数のさまざまなソースで同じコマンド ロジックを呼び出せるようになり、コマンド ロジックをさまざまな対象用にカスタマイズできるようになります。  たとえば、多くのアプリケーションで目にする **\[コピー\]**、**\[切り取り\]**、**\[貼り付け\]** の編集操作は、コマンドを使用して実装されていれば、複数の異なるユーザー アクションから呼び出すことができます。  アプリケーションでは、ボタンのクリック、メニューの項目の選択、または Ctrl \+ X などのショートカット キーの使用によって、選択したオブジェクトまたはテキストを切り取ることができます。  コマンドを使用すると、各種類のユーザー アクションを同じロジックにバインドできます。  
  
 コマンドには、アクションが使用可能かどうかを示すという目的もあります。  オブジェクトまたはテキストの切り取りの例を続けると、アクションは何かが選択されているときにのみ効果があります。  ユーザーが何も選択せずにオブジェクトまたはテキストを切り取ろうとしても、何も行われません。  これをユーザーに示すために、多くのアプリケーションでは、ボタンとメニュー項目を無効にして、アクションを実行できるかどうかがわかるようにしています。  コマンドは、<xref:System.Windows.Input.ICommand.CanExecute%2A> メソッドを実装することで、アクションが使用可能かどうかを示すことができます。  ボタンでは、<xref:System.Windows.Input.ICommand.CanExecuteChanged> イベントにサブスクライブし、<xref:System.Windows.Input.ICommand.CanExecute%2A> が `false` を返す場合に無効にし、<xref:System.Windows.Input.ICommand.CanExecute%2A> が `true` を返す場合に有効にすることができます。  
  
 コマンドのセマンティクスはアプリケーションおよびクラスの間で一貫していますが、アクションのロジックは実行される特定のオブジェクトに固有です。  Ctrl \+ X というショートカット キーは、テキスト クラス、イメージ クラス、および Web ブラウザーで **\[切り取り\]** コマンドを呼び出しますが、**\[切り取り\]** 操作を実行するための実際のロジックは、切り取りを実行するアプリケーションによって定義されます。  <xref:System.Windows.Input.RoutedCommand> は、クライアントによるロジックの実装を可能にします。  テキスト オブジェクトでは選択されたテキストをクリップボードに切り取る一方で、イメージ オブジェクトでは選択されたイメージを切り取ることができます。  アプリケーションは、<xref:System.Windows.Input.CommandManager.Executed> イベントを処理する場合に、コマンドのターゲットにアクセスし、ターゲットの種類に応じて適切なアクションを実行できます。  
  
<a name="simple_command"></a>   
## WPF の簡単なコマンドの例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でコマンドを使用する最も簡単な方法は、コマンド ライブラリ クラスのいずれかから定義済みの <xref:System.Windows.Input.RoutedCommand> を使用すること、コマンドの処理をネイティブにサポートしているコントロールを使用すること、およびコマンドの呼び出しをネイティブにサポートしているコントロールを使用することです。  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> コマンドは、<xref:System.Windows.Input.ApplicationCommands> クラスの定義済みコマンドの 1 つです。  <xref:System.Windows.Controls.TextBox> コントロールには、<xref:System.Windows.Input.ApplicationCommands.Paste%2A> コマンドを処理するためのロジックが組み込まれており、  <xref:System.Windows.Controls.MenuItem> クラスは、コマンドの呼び出しをネイティブにサポートしています。  
  
 <xref:System.Windows.Controls.TextBox> にキーボード フォーカスがある場合に、<xref:System.Windows.Controls.MenuItem> がクリックされると <xref:System.Windows.Controls.TextBox> で <xref:System.Windows.Input.ApplicationCommands.Paste%2A> コマンドを呼び出すように <xref:System.Windows.Controls.MenuItem> を設定する方法を次の例に示します。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## WPF のコマンド実行の 4 つの主要な概念  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のルーティング コマンド モデルは、コマンド、コマンド ソース、コマンドの対象、およびコマンド バインディングの 4 つの主要な概念に分けることができます。  
  
-   *コマンド*は、実行されるアクションです。  
  
-   *コマンド ソース*は、コマンドを呼び出すオブジェクトです。  
  
-   *コマンドの対象*は、コマンドが実行されているオブジェクトです。  
  
-   *コマンド バインディング*は、コマンド ロジックをコマンドに割り当てるオブジェクトです。  
  
 前の例では、<xref:System.Windows.Input.ApplicationCommands.Paste%2A> コマンドがコマンド、<xref:System.Windows.Controls.MenuItem> がコマンド ソース、<xref:System.Windows.Controls.TextBox> がコマンドの対象であり、コマンド バインディングは <xref:System.Windows.Controls.TextBox> コントロールによって提供されています。  ただし、<xref:System.Windows.Input.CommandBinding> が、コマンドの対象クラスであるコントロールによって必ず提供されるとは限らないことに注意してください。  アプリケーション開発者が <xref:System.Windows.Input.CommandBinding> を作成する必要がある場合や、<xref:System.Windows.Input.CommandBinding> をコマンドの対象の親に割り当てる場合も多くあります。  
  
<a name="Commands"></a>   
### コマンド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコマンドを作成するには、<xref:System.Windows.Input.ICommand> インターフェイスを実装します。  <xref:System.Windows.Input.ICommand> は、<xref:System.Windows.Input.ICommand.Execute%2A> および <xref:System.Windows.Input.ICommand.CanExecute%2A> という 2 つのメソッドと、<xref:System.Windows.Input.ICommand.CanExecuteChanged> イベントを公開します。  <xref:System.Windows.Input.ICommand.Execute%2A> はコマンドに関連するアクションを実行します。<xref:System.Windows.Input.ICommand.CanExecute%2A> は現在のコマンドの対象でコマンドを実行できるかどうかを決定します。  <xref:System.Windows.Input.ICommand.CanExecuteChanged> は、コマンド実行操作を集中管理するコマンド マネージャーが、発生済みだがコマンド バインディングによってまだ実行されていないコマンドを無効にする可能性がある変更をコマンド ソース内で検出した場合に発生します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での <xref:System.Windows.Input.ICommand> の実装は <xref:System.Windows.Input.RoutedCommand> クラスです。この概要ではこのクラスを中心に説明しています。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の主な入力ソースは、マウス、キーボード、インク、およびルーティング コマンドです。  よりデバイス指向の入力では、<xref:System.Windows.RoutedEvent> を使用して、入力イベントが発生したアプリケーション ページ内のオブジェクトを通知します。  <xref:System.Windows.Input.RoutedCommand> も同じです。  <xref:System.Windows.Input.RoutedCommand> の <xref:System.Windows.Input.RoutedCommand.Execute%2A> メソッドと <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> メソッドには、コマンドのアプリケーション ロジックは含まれませんが、<xref:System.Windows.Input.CommandBinding> を持つオブジェクトを検出するまで、要素ツリー内をトンネリングおよびバブリングするルーティング イベントを発生させます。  <xref:System.Windows.Input.CommandBinding> にはこれらのイベントのハンドラーが含まれ、このハンドラーがコマンドを実行するハンドラーとなります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内でのイベント ルーティングの詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.RoutedCommand> の <xref:System.Windows.Input.RoutedCommand.Execute%2A> メソッドは、コマンドの対象で <xref:System.Windows.Input.CommandManager.PreviewExecuted> イベントと <xref:System.Windows.Input.CommandManager.Executed> イベントを発生させます。  <xref:System.Windows.Input.RoutedCommand> の <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> メソッドは、コマンドの対象で <xref:System.Windows.Input.CommandManager.CanExecute> イベントと <xref:System.Windows.Input.CommandManager.PreviewCanExecute> イベントを発生させます。  これらのイベントは、その特定のコマンドの <xref:System.Windows.Input.CommandBinding> を持つオブジェクトを検出するまで、要素ツリー内をトンネリングおよびバブリングします。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、複数のクラスに散在する一連の一般的なルーティング コマンドである <xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.ComponentCommands>、および <xref:System.Windows.Documents.EditingCommands> を提供します。  これらのクラスは、<xref:System.Windows.Input.RoutedCommand> オブジェクトのみで構成され、コマンドの実装ロジックは含まれません。  実装ロジックは、コマンドが実行されているオブジェクトに含まれます。  
  
<a name="Command_Sources"></a>   
### コマンド ソース  
 コマンド ソースは、コマンドを呼び出すオブジェクトです。  コマンド ソースには、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Input.KeyGesture> などがあります。  
  
 通常 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコマンド ソースは、<xref:System.Windows.Input.ICommandSource> インターフェイスを実装します。  
  
 <xref:System.Windows.Input.ICommandSource> は、<xref:System.Windows.Input.ICommandSource.Command%2A>、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>、および <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> の 3 つのプロパティを公開します。  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A> は、コマンド ソースが呼び出されると実行されるコマンドです。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> は、コマンドが実行される対象オブジェクトです。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、<xref:System.Windows.Input.ICommandSource> の <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> プロパティは、<xref:System.Windows.Input.ICommand> が <xref:System.Windows.Input.RoutedCommand> の場合にのみ適用されることに注意してください。  <xref:System.Windows.Input.ICommandSource> で <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> が設定されていても、対応するコマンドが <xref:System.Windows.Input.RoutedCommand> でない場合は、コマンドの対象は無視されます。  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> が設定されていない場合は、キーボード フォーカスを持つ要素がコマンドの対象になります。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> は、コマンドを実装するハンドラーに情報を渡すために使用されるユーザー定義のデータ型です。  
  
 <xref:System.Windows.Input.ICommandSource> を実装する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のクラスには、<xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Documents.Hyperlink>、および <xref:System.Windows.Input.InputBinding> があります。  <xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem>、および <xref:System.Windows.Documents.Hyperlink> は、クリックされるとコマンドを呼び出し、<xref:System.Windows.Input.InputBinding> は、それに関連付けられている <xref:System.Windows.Input.InputGesture> が実行されるとコマンドを呼び出します。  
  
 <xref:System.Windows.Controls.ContextMenu> 内の <xref:System.Windows.Controls.MenuItem> を、<xref:System.Windows.Input.ApplicationCommands.Properties%2A> コマンドのコマンド ソースとして使用する方法を次の例に示します。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 通常、コマンド ソースは、<xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> イベントをリッスンします。  このイベントは、現在のコマンドの対象でコマンドを実行できるかどうかが変更された可能性があることをコマンド ソースに通知します。  コマンド ソースは、<xref:System.Windows.Input.RoutedCommand.CanExecute%2A> メソッドを使用して <xref:System.Windows.Input.RoutedCommand> の現在のステータスを照会できます。  コマンドが実行できない場合は、コマンド ソースそのものが無効になります。  コマンドを実行できない場合に灰色表示される <xref:System.Windows.Controls.MenuItem> は、この一例です。  
  
 <xref:System.Windows.Input.InputGesture> は、コマンド ソースとして使用できます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の入力ジェスチャには、<xref:System.Windows.Input.KeyGesture> と <xref:System.Windows.Input.MouseGesture> の 2 種類があります。  <xref:System.Windows.Input.KeyGesture> は Ctrl \+ C などのキーボード ショートカットと考えることができます。  <xref:System.Windows.Input.KeyGesture> は、<xref:System.Windows.Input.Key>と、<xref:System.Windows.Input.ModifierKeys> のセットで構成されています。  <xref:System.Windows.Input.MouseGesture> は、<xref:System.Windows.Input.MouseAction> と、オプションの <xref:System.Windows.Input.ModifierKeys> のセットで構成されています。  
  
 <xref:System.Windows.Input.InputGesture> をコマンド ソースとして機能させるには、コマンドに関連付ける必要があります。  これを実現するには、いくつかの方法があります。  1 つは、<xref:System.Windows.Input.InputBinding> を使用する方法です。  
  
 <xref:System.Windows.Input.KeyGesture> と <xref:System.Windows.Input.RoutedCommand> の間に <xref:System.Windows.Input.KeyBinding> を作成する方法を次の例に示します。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 <xref:System.Windows.Input.InputGesture> を <xref:System.Windows.Input.RoutedCommand> に関連付ける別の方法は、<xref:System.Windows.Input.InputGesture> を <xref:System.Windows.Input.RoutedCommand> の <xref:System.Windows.Input.InputGestureCollection> に追加する方法です。  
  
 <xref:System.Windows.Input.KeyGesture> を <xref:System.Windows.Input.RoutedCommand> の <xref:System.Windows.Input.InputGestureCollection> に追加する方法を次の例に示します。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### CommandBinding  
 <xref:System.Windows.Input.CommandBinding> は、コマンドを実装するイベント ハンドラーにコマンドを関連付けます。  
  
 <xref:System.Windows.Input.CommandBinding> クラスには、<xref:System.Windows.Input.CommandBinding.Command%2A> プロパティと、<xref:System.Windows.Input.CommandBinding.PreviewExecuted>、<xref:System.Windows.Input.CommandBinding.Executed>、<xref:System.Windows.Input.CommandBinding.PreviewCanExecute>、および <xref:System.Windows.Input.CommandBinding.CanExecute> イベントが含まれます。  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> は、<xref:System.Windows.Input.CommandBinding> が関連付けられているコマンドです。  <xref:System.Windows.Input.CommandBinding.PreviewExecuted> イベントと <xref:System.Windows.Input.CommandBinding.Executed> イベントに割り当てられたイベント ハンドラーは、コマンド ロジックを実装します。  <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> イベントと <xref:System.Windows.Input.CommandBinding.CanExecute> イベントに割り当てられたイベント ハンドラーは、コマンドが現在のコマンドの対象で実行可能かどうかを判断します。  
  
 アプリケーションのルート <xref:System.Windows.Window> で <xref:System.Windows.Input.CommandBinding> を作成する方法を次の例に示します。  <xref:System.Windows.Input.CommandBinding> は、<xref:System.Windows.Input.ApplicationCommands.Open%2A> コマンドを <xref:System.Windows.Input.CommandManager.Executed> ハンドラーおよび <xref:System.Windows.Input.CommandBinding.CanExecute> ハンドラーに関連付けます。  
  
 [!code-xml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 次に、<xref:System.Windows.Input.ExecutedRoutedEventHandler> および <xref:System.Windows.Input.CanExecuteRoutedEventHandler> を作成します。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> は、コマンドが実行されたことを知らせる文字列を表示する <xref:System.Windows.MessageBox> を開きます。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> は、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> プロパティを `true` に設定します。  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 <xref:System.Windows.Input.CommandBinding> は、アプリケーションまたはコントロールのルート <xref:System.Windows.Window> などの特定のオブジェクトに割り当てられます。  <xref:System.Windows.Input.CommandBinding> が割り当てられたオブジェクトは、バインディングのスコープを定義します。  たとえば、コマンドの対象の先祖に割り当てられた <xref:System.Windows.Input.CommandBinding> には、<xref:System.Windows.Input.CommandBinding.Executed> イベントによって到達できますが、コマンドの対象の子孫に割り当てられた <xref:System.Windows.Input.CommandBinding> には到達できません。  これは、イベントを発生させるオブジェクトから <xref:System.Windows.RoutedEvent> がトンネリングおよびバブリングするというしくみが直接影響するからです。  
  
 場合によっては、<xref:System.Windows.Input.CommandBinding> は、<xref:System.Windows.Controls.TextBox> クラスに対する <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A>、<xref:System.Windows.Input.ApplicationCommands.Paste%2A> の各コマンドのように、コマンドの対象自体に割り当てられます。  ただし、<xref:System.Windows.Input.CommandBinding> は、特に同じ <xref:System.Windows.Input.CommandBinding> を複数のコマンドの対象で使用できる場合には、メイン <xref:System.Windows.Window> やアプリケーション オブジェクトなど、コマンドの対象の先祖に割り当てる方が便利な場合がよくあります。  これらは、コマンド実行インフラストラクチャの作成時に検討される設計上の決定事項です。  
  
<a name="Commane_Target"></a>   
### コマンドの対象  
 コマンドの対象は、コマンドが実行される要素です。  <xref:System.Windows.Input.RoutedCommand> のコマンドの対象は、<xref:System.Windows.Input.CommandManager.Executed> および <xref:System.Windows.Input.CommandManager.CanExecute> のルーティングが開始される要素です。  前に述べたように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、<xref:System.Windows.Input.ICommandSource> の <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> プロパティは、<xref:System.Windows.Input.ICommand> が <xref:System.Windows.Input.RoutedCommand> の場合にのみ適用されます。  <xref:System.Windows.Input.ICommandSource> で <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> が設定されていても、対応するコマンドが <xref:System.Windows.Input.RoutedCommand> でない場合は、コマンドの対象は無視されます。  
  
 コマンド ソースは、コマンドの対象を明示的に設定できます。  コマンドの対象が定義されていない場合は、キーボード フォーカスを持つ要素がコマンドの対象として使用されます。  キーボード フォーカスを持つ要素をコマンドの対象として使用する利点の 1 つは、アプリケーション開発者が同じコマンド ソースを使用して、コマンドの対象を追跡せずにコマンドを複数の対象で呼び出すことができることです。  たとえば、<xref:System.Windows.Controls.MenuItem> が <xref:System.Windows.Controls.TextBox> コントロールと <xref:System.Windows.Controls.PasswordBox> コントロールを持つアプリケーションで **\[貼り付け\]** コマンドを呼び出した場合、その対象は、キーボード フォーカスのあるコントロールに応じて <xref:System.Windows.Controls.TextBox> または <xref:System.Windows.Controls.PasswordBox> にすることができます。  
  
 マークアップと分離コードでコマンドの対象を明示的に設定する方法を次の例に示します。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### CommandManager  
 <xref:System.Windows.Input.CommandManager> は、多数のコマンド関連機能を提供します。  <xref:System.Windows.Input.CommandManager.PreviewExecuted>、<xref:System.Windows.Input.CommandManager.Executed>、<xref:System.Windows.Input.CommandManager.PreviewCanExecute>、および <xref:System.Windows.Input.CommandManager.CanExecute> の各イベント ハンドラーを特定の要素に対して追加および削除するための一連の静的メソッドを提供します。  <xref:System.Windows.Input.CommandBinding> オブジェクトと <xref:System.Windows.Input.InputBinding> オブジェクトを特定のクラスに登録する手段を提供します。  また、<xref:System.Windows.Input.CommandManager> は、<xref:System.Windows.Input.CommandManager.RequerySuggested> イベントを介して、<xref:System.Windows.Input.ICommand.CanExecuteChanged> イベントを発生させるタイミングをコマンドに通知する方法も提供します。  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> メソッドは、<xref:System.Windows.Input.CommandManager> に <xref:System.Windows.Input.CommandManager.RequerySuggested> イベントを強制的に発生させます。  これは、コマンドを無効または有効にする必要がある場合に役立ちますが、<xref:System.Windows.Input.CommandManager> が認識しない場合には使用しません。  
  
<a name="Command_Library"></a>   
## コマンド ライブラリ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、一連の定義済みコマンドを提供します。  コマンド ライブラリは、<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Documents.EditingCommands>、および <xref:System.Windows.Input.ComponentCommands> の各クラスから構成されます。  これらのクラスは、<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> と <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>、<xref:System.Windows.Input.MediaCommands.Play%2A>、<xref:System.Windows.Input.MediaCommands.Stop%2A>、<xref:System.Windows.Input.MediaCommands.Pause%2A> などのコマンドを提供します。  
  
 これらのコマンドの多くには、一連の既定の入力バインディングが含まれます。  たとえば、アプリケーションでコピー コマンドを処理するように指定した場合、キーボード バインディング "Ctrl\+C" が自動的に取得されます。[!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] ペン ジェスチャや音声情報など、他の入力デバイスのバインディングも取得されます。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してさまざまなコマンド ライブラリ内のコマンドを参照する場合、通常は、静的コマンド プロパティを公開するライブラリ クラスのクラス名を省略できます。  一般に、コマンド名は文字列としてあいまいではなく、所有する型は、コマンドを論理的にグループ化するために存在し、あいまいさを排除するために必要なわけではありません。  たとえば、冗長な `Command="ApplicationCommands.Cut"` ではなく、`Command="Cut"` と指定できます。  これは、コマンドの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサに組み込まれている便利なメカニズムであり \(もっと正確に言えば、これは <xref:System.Windows.Input.ICommand> の型コンバーターの動作です\)、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサが読み込み時に参照します。  
  
<a name="creating_commands"></a>   
## カスタム コマンドの作成  
 コマンド ライブラリ クラス内のコマンドが目的に合っていない場合は、独自のコマンドを作成できます。  カスタム コマンドを作成するには 2 とおりの方法があります。  1 つは、最初から作成する方法で <xref:System.Windows.Input.ICommand> インターフェイスを実装します。  もう 1 つは、<xref:System.Windows.Input.RoutedCommand> または <xref:System.Windows.Input.RoutedUICommand> を作成する方法で、こちらの方が一般的です。  
  
 カスタム <xref:System.Windows.Input.RoutedCommand> の作成の例については、[カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)を参照してください。  
  
## 参照  
 <xref:System.Windows.Input.RoutedCommand>   
 <xref:System.Windows.Input.CommandBinding>   
 <xref:System.Windows.Input.InputBinding>   
 <xref:System.Windows.Input.CommandManager>   
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [ICommandSource を実装する](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)   
 [How to: Add a Command to a MenuItem](http://msdn.microsoft.com/ja-jp/013d68a0-5373-4a68-bd91-5de574307370)   
 [カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)