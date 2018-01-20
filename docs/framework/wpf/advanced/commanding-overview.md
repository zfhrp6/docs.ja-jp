---
title: "コマンド実行の概要"
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
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb7d05cdf5f6a80a0a247a5f429052cc9a8368b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="commanding-overview"></a>コマンド実行の概要
<a name="introduction"></a> コマンド実行は [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の入力メカニズムであり、デバイス入力よりいっそうセマンティックなレベルでの入力処理を提供します。 コマンドの例は、多くのアプリケーションで見られる**コピー**、**切り取り**、**貼り付け**などの操作です。  
  
 この概要では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのコマンドとはどういうものか、コマンド実行モデルに含まれるクラス、アプリケーションでコマンドを作成して使用する方法を定義します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [コマンドとは](#commands_at_10000_feet)  
  
-   [WPF での簡単なコマンドの例](#simple_command)  
  
-   [WPF のコマンド実行における 4 つの主要な概念](#Four_main_Concepts)  
  
-   [コマンド ライブラリ](#Command_Library)  
  
-   [カスタム コマンドの作成](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>コマンドとは  
 コマンドには、いくつかの目的があります。 第 1 の目的は、コマンドを呼び出すセマンティクスとオブジェクトを、コマンドを実行するロジックから分離することです。 これにより、複数の異なるソースから同じコマンド ロジックを呼び出すことができ、異なるターゲットに合わせてコマンド ロジックをカスタマイズできます。 たとえば、多くのアプリケーションで使われる編集操作である**コピー**、**切り取り**、**貼り付け**は、コマンドを使って実装されていれば、異なるユーザー アクションを使って呼び出すことができます。 ユーザーは、ボタンをクリックして、メニューの項目を選択して、または Ctrl + X などのキーの組み合わせを使って、選んだオブジェクトやテキストを切り取ることができます。 コマンドを使うことにより、各種のユーザー アクションを同じロジックにバインドできます。  
  
 コマンドのもう 1 つの目的は、アクションを実行できるかどうかを示すことです。 再びオブジェクトやテキストの切り取りを例にすると、アクションは何かを選択したときにのみ意味があります。 何も選ばないでオブジェクトまたはテキストを切り取ろうとすると、何も起こりません。 ユーザーにこのことを示すため、多くのアプリケーションでは、ボタンやメニュー項目を無効にして、アクションを実行できるかどうかをユーザーが認識できるようにしています。 コマンドは、アクションは、実装することによって可能かどうかを示すことができます、<xref:System.Windows.Input.ICommand.CanExecute%2A>メソッドです。 サブスクライブするボタン、<xref:System.Windows.Input.ICommand.CanExecuteChanged>イベント場合無効にして<xref:System.Windows.Input.ICommand.CanExecute%2A>を返します`false`場合に有効にするか<xref:System.Windows.Input.ICommand.CanExecute%2A>を返します`true`です。  
  
 コマンドのセマンティクスはアプリケーションおよびクラス全体で統一できますが、アクションのロジックは対象となる特定のオブジェクトに固有です。 キーの組み合わせ Ctrl + X キーはテキスト クラス、イメージ クラス、Web ブラウザーの**切り取り**コマンドを呼び出しますが、**切り取り**操作を実行する実際のロジックは、切り取りを実行するアプリケーションによって定義されています。 A<xref:System.Windows.Input.RoutedCommand>ロジックの実装にクライアントを有効にします。 テキスト オブジェクトは選択されたテキストを切り取ってクリップボードに移動できるのに対し、イメージ オブジェクトは選択されたイメージを切り取ることができます。 アプリケーションで処理すると、<xref:System.Windows.Input.CommandManager.Executed>イベント、コマンドのターゲットにアクセスし、ターゲットの種類に応じて適切な対策を実施できます。  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>WPF での簡単なコマンドの例  
 コマンドを使用する最も簡単な方法[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して、定義済み<xref:System.Windows.Input.RoutedCommand>コマンド ライブラリ クラス; のいずれかのコマンドを処理するためのネイティブ サポートしているコントロールを使用し、コマンドを呼び出すためのネイティブ サポートしているコントロールを使用します。  <xref:System.Windows.Input.ApplicationCommands.Paste%2A>定義済みのコマンドのいずれかのコマンドは、<xref:System.Windows.Input.ApplicationCommands>クラスです。  <xref:System.Windows.Controls.TextBox>コントロールを処理するためのロジックが組み込まれています、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンド。  および<xref:System.Windows.Controls.MenuItem>クラスには、コマンドを呼び出すためのネイティブ サポート。  
  
 次の例を設定する方法を示しています、<xref:System.Windows.Controls.MenuItem>が呼び出さがクリックされたときにできるように、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンドを<xref:System.Windows.Controls.TextBox>と見なし、<xref:System.Windows.Controls.TextBox>キーボード フォーカスがあります。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF のコマンド実行における 4 つの主要な概念  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のルーティング コマンド モデルは、コマンド、コマンド ソース、コマンド ターゲット、コマンド バインディングという 4 つの主要な概念に分けることができます。  
  
-   "*コマンド*" は、実行するアクションです。  
  
-   "*コマンド ソース*" は、コマンドを呼び出すオブジェクトです。  
  
-   "*コマンド ターゲット*" は、コマンドが実行されているオブジェクトです。  
  
-   "*コマンド バインディング*" は、コマンド ロジックをコマンドにマップするオブジェクトです。  
  
 前の例で、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>は、コマンド、<xref:System.Windows.Controls.MenuItem>コマンド ソースが、<xref:System.Windows.Controls.TextBox>コマンド ターゲットでは、コマンドのバインドは、によって提供される、<xref:System.Windows.Controls.TextBox>コントロール。  常に大文字と小文字の注目すべきであること、<xref:System.Windows.Input.CommandBinding>コマンド ターゲット クラスにあるコントロールによって提供されます。  多くの場合、<xref:System.Windows.Input.CommandBinding>アプリケーション開発者によって作成する必要がありますまたは<xref:System.Windows.Input.CommandBinding>コマンド ターゲットの親にアタッチする場合があります。  
  
<a name="Commands"></a>   
### <a name="commands"></a>コマンド  
 コマンド内[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実装することによって作成された、<xref:System.Windows.Input.ICommand>インターフェイスです。  <xref:System.Windows.Input.ICommand>2 つのメソッドを公開<xref:System.Windows.Input.ICommand.Execute%2A>、および<xref:System.Windows.Input.ICommand.CanExecute%2A>、およびイベントが、<xref:System.Windows.Input.ICommand.CanExecuteChanged>です。 <xref:System.Windows.Input.ICommand.Execute%2A>コマンドに関連付けられているアクションを実行します。 <xref:System.Windows.Input.ICommand.CanExecute%2A>現在のコマンド ターゲットでコマンドを実行できるかどうかを判断します。 <xref:System.Windows.Input.ICommand.CanExecuteChanged>コマンド実行の操作を一元化コマンド マネージャーされた発生がコマンドのバインドによって実行されていないコマンドが無効になるコマンド ソースで変更が検出される場合に発生します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装<xref:System.Windows.Input.ICommand>は、<xref:System.Windows.Input.RoutedCommand>クラスし、この概要でのフォーカスが置かれています。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] での主な入力ソースは、マウス、キーボード、インク、およびルーティング コマンドです。  デバイス指向の入力を使用して、<xref:System.Windows.RoutedEvent>入力イベントが発生したアプリケーション ページで、オブジェクトに通知します。  A<xref:System.Windows.Input.RoutedCommand>に違いはありません。  <xref:System.Windows.Input.RoutedCommand.Execute%2A>と<xref:System.Windows.Input.RoutedCommand.CanExecute%2A>のメソッド、<xref:System.Windows.Input.RoutedCommand>コマンドは、アプリケーション ロジックが含まれていませんが、トンネルのルーティング イベントを発生させるし、持つオブジェクトに遭遇するまで、要素ツリーを通じてバブルではなく、、<xref:System.Windows.Input.CommandBinding>です。  <xref:System.Windows.Input.CommandBinding>これらのイベントのハンドラーを含むコマンドを実行するハンドラーであるとします。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのルーティング イベントについて詳しくは、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」をご覧ください。  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A>メソッドを<xref:System.Windows.Input.RoutedCommand>を生成、<xref:System.Windows.Input.CommandManager.PreviewExecuted>と<xref:System.Windows.Input.CommandManager.Executed>コマンド ターゲットでのイベントです。  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>メソッドを<xref:System.Windows.Input.RoutedCommand>を生成、<xref:System.Windows.Input.CommandManager.CanExecute>と<xref:System.Windows.Input.CommandManager.PreviewCanExecute>コマンド ターゲットでのイベントです。  これらのイベント トンネルおよびバブルがオブジェクトに遭遇するまで、要素ツリーを通じて、<xref:System.Windows.Input.CommandBinding>その特定のコマンド。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]一連の一般的なルーティング コマンドがいくつかのクラスに分散装置: <xref:System.Windows.Input.MediaCommands>、 <xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.NavigationCommands>、 <xref:System.Windows.Input.ComponentCommands>、および<xref:System.Windows.Documents.EditingCommands>です。  これらのクラスのみで構成、<xref:System.Windows.Input.RoutedCommand>オブジェクトとコマンドの実装ロジックではありません。  実装ロジックは、コマンドが実行されるオブジェクトに存在します。  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>コマンド ソース  
 コマンド ソースは、コマンドを呼び出すオブジェクトです。  コマンド ソースの例としては<xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.Button>、および<xref:System.Windows.Input.KeyGesture>です。  
  
 コマンド内のソース[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実装では、通常、<xref:System.Windows.Input.ICommandSource>インターフェイスです。  
  
 <xref:System.Windows.Input.ICommandSource>次の 3 つのプロパティを公開: <xref:System.Windows.Input.ICommandSource.Command%2A>、 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>、および<xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>コマンド ソースが呼び出されたときに実行されるコマンドです。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>コマンドを実行するオブジェクトです。  点に注意が[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>プロパティ<xref:System.Windows.Input.ICommandSource>のみ該当する場合は、<xref:System.Windows.Input.ICommand>は、<xref:System.Windows.Input.RoutedCommand>です。  場合、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>に設定されている、 <xref:System.Windows.Input.ICommandSource> 、対応するコマンドが、<xref:System.Windows.Input.RoutedCommand>コマンドの対象は無視されます。 場合、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>が設定された場合、キーボード フォーカスを持つ要素がコマンドの対象となります。  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>ハンドラーに情報を渡すユーザー定義データ型は、コマンドの実装です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を実装するクラス<xref:System.Windows.Input.ICommandSource>は<xref:System.Windows.Controls.Primitives.ButtonBase>、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Documents.Hyperlink>、および<xref:System.Windows.Input.InputBinding>です。  <xref:System.Windows.Controls.Primitives.ButtonBase>、 <xref:System.Windows.Controls.MenuItem>、および<xref:System.Windows.Documents.Hyperlink>がクリックされたときに、コマンドを呼び出す<xref:System.Windows.Input.InputBinding>コマンドを呼び出すときに、<xref:System.Windows.Input.InputGesture>関連付けられているで実行されます。  
  
 次の例を使用する方法を示しています、<xref:System.Windows.Controls.MenuItem>で、<xref:System.Windows.Controls.ContextMenu>用コマンドのソースとして、<xref:System.Windows.Input.ApplicationCommands.Properties%2A>コマンド。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 コマンド ソースがリッスンする通常、<xref:System.Windows.Input.RoutedCommand.CanExecuteChanged>イベント。  このイベントは、現在のコマンド ターゲットでのコマンド実行機能が変化した可能性があることを、コマンド ソースに通知します。  コマンド ソースがの現在の状態を照会できます、<xref:System.Windows.Input.RoutedCommand>を使用して、<xref:System.Windows.Input.RoutedCommand.CanExecute%2A>メソッドです。  コマンドを実行できない場合、コマンド ソースはそれ自体を無効にできます。  この例は、<xref:System.Windows.Controls.MenuItem>要素自体のコマンドを実行できませんを灰色表示します。  
  
 <xref:System.Windows.Input.InputGesture>コマンド ソースとして使用できます。  2 種類の入力ジェスチャの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、<xref:System.Windows.Input.KeyGesture>と<xref:System.Windows.Input.MouseGesture>です。  考えることができます、 <xref:System.Windows.Input.KeyGesture> CTRL + C などのキーボード ショートカットとします。  A<xref:System.Windows.Input.KeyGesture>から成る、<xref:System.Windows.Input.Key>と一連の<xref:System.Windows.Input.ModifierKeys>します。  A<xref:System.Windows.Input.MouseGesture>から成る、<xref:System.Windows.Input.MouseAction>と省略可能な一連の<xref:System.Windows.Input.ModifierKeys>します。  
  
 順序で、<xref:System.Windows.Input.InputGesture>コマンド ソースとして機能しをコマンドに関連付けられている場合があります。 これを実現するにはいくつかの方法があります。  1 つの方法は、使用する、<xref:System.Windows.Input.InputBinding>です。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Input.KeyBinding>間、<xref:System.Windows.Input.KeyGesture>と<xref:System.Windows.Input.RoutedCommand>です。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 関連付けるには別の方法、<xref:System.Windows.Input.InputGesture>を<xref:System.Windows.Input.RoutedCommand>を追加するには、<xref:System.Windows.Input.InputGesture>を<xref:System.Windows.Input.InputGestureCollection>上、<xref:System.Windows.Input.RoutedCommand>です。  
  
 次の例は、追加する方法を示します、<xref:System.Windows.Input.KeyGesture>を<xref:System.Windows.Input.InputGestureCollection>の<xref:System.Windows.Input.RoutedCommand>です。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A<xref:System.Windows.Input.CommandBinding>コマンドをコマンドを実装するイベント ハンドラーに関連付けます。  
  
 <xref:System.Windows.Input.CommandBinding>クラスに含まれる、<xref:System.Windows.Input.CommandBinding.Command%2A>プロパティ、および<xref:System.Windows.Input.CommandBinding.PreviewExecuted>、 <xref:System.Windows.Input.CommandBinding.Executed>、 <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>、および<xref:System.Windows.Input.CommandBinding.CanExecute>イベント。  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>コマンドを<xref:System.Windows.Input.CommandBinding>を関連付けています。  イベント ハンドラーにアタッチされている、<xref:System.Windows.Input.CommandBinding.PreviewExecuted>と<xref:System.Windows.Input.CommandBinding.Executed>イベントは、コマンドのロジックを実装します。  イベント ハンドラーがアタッチされている、<xref:System.Windows.Input.CommandBinding.PreviewCanExecute>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベントは、コマンドを現在のコマンド ターゲットで実行できるかどうかを判断します。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Input.CommandBinding>ルートに対する<xref:System.Windows.Window>アプリケーションのです。  <xref:System.Windows.Input.CommandBinding>関連付けます、<xref:System.Windows.Input.ApplicationCommands.Open%2A>コマンドと<xref:System.Windows.Input.CommandManager.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>ハンドラー。  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 次に、<xref:System.Windows.Input.ExecutedRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>が作成されます。  <xref:System.Windows.Input.ExecutedRoutedEventHandler>開きます、<xref:System.Windows.MessageBox>コマンドが実行されたというメッセージが文字列を表示します。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>設定、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>プロパティを`true`です。  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A<xref:System.Windows.Input.CommandBinding>ルートなどの特定のオブジェクトにアタッチされて<xref:System.Windows.Window>アプリケーションまたはコントロールのです。  オブジェクトを<xref:System.Windows.Input.CommandBinding>バインディングのスコープを定義にアタッチされています。  たとえば、<xref:System.Windows.Input.CommandBinding>接続からアクセスできるターゲット コマンドの先祖に、<xref:System.Windows.Input.CommandBinding.Executed>イベントが、<xref:System.Windows.Input.CommandBinding>接続されているコマンドの子孫をターゲットに到達できません。  これは、方法の直接の結果、<xref:System.Windows.RoutedEvent>トンネルおよびイベントを発生させるオブジェクトからバブルします。  
  
 状況によっては、<xref:System.Windows.Input.CommandBinding>はターゲットに接続された、コマンド自体などで、<xref:System.Windows.Controls.TextBox>クラスおよび<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、 <xref:System.Windows.Input.ApplicationCommands.Copy%2A>、および<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンド。 多くの場合は、アタッチする方が便利です、<xref:System.Windows.Input.CommandBinding>メインなど、コマンド ターゲットでの先祖に<xref:System.Windows.Window>またはアプリケーション オブジェクト場合に特に同じ<xref:System.Windows.Input.CommandBinding>複数のコマンド ターゲットを使用できます。  これらは、コマンド実行のインフラストラクチャを作成するときに考慮する設計上の決定です。  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>コマンド ターゲット  
 コマンド ターゲットは、コマンドが実行される要素です。  Regards すると、 <xref:System.Windows.Input.RoutedCommand>、コマンドの対象は、ルーティングの位置にある要素、<xref:System.Windows.Input.CommandManager.Executed>と<xref:System.Windows.Input.CommandManager.CanExecute>を開始します。  以前に記載されている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>プロパティ<xref:System.Windows.Input.ICommandSource>のみ該当する場合は、<xref:System.Windows.Input.ICommand>は、<xref:System.Windows.Input.RoutedCommand>です。  場合、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>に設定されている、 <xref:System.Windows.Input.ICommandSource> 、対応するコマンドが、<xref:System.Windows.Input.RoutedCommand>コマンドの対象は無視されます。  
  
 コマンド ソースは、コマンド ターゲットを明示的に設定できます。  コマンド ターゲットが定義されていない場合は、キーボード フォーカスを持つ要素がコマンド ターゲットとして使われます。  キーボード フォーカスを持つ要素をコマンド ターゲットとして使うことの、アプリケーション開発者にとっての利点の 1 つは、コマンド ターゲットを追跡しなくても、同じコマンド ソースを使って、複数のターゲットでコマンドを呼び出すことができることです。  たとえば場合、<xref:System.Windows.Controls.MenuItem>呼び出します、**貼り付け**を持つアプリケーションでコマンド、<xref:System.Windows.Controls.TextBox>コントロールと<xref:System.Windows.Controls.PasswordBox>コントロールをターゲットにできますか、<xref:System.Windows.Controls.TextBox>または<xref:System.Windows.Controls.PasswordBox>に応じてコントロールには、キーボード フォーカスがあります。  
  
 次の例では、マークアップおよび分離コードでコマンド ターゲットを明示的に設定する方法を示します。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager>はコマンドの数、関連する関数。  追加および削除するための静的メソッドのセットが提供<xref:System.Windows.Input.CommandManager.PreviewExecuted>、 <xref:System.Windows.Input.CommandManager.Executed>、 <xref:System.Windows.Input.CommandManager.PreviewCanExecute>、および<xref:System.Windows.Input.CommandManager.CanExecute>の特定の要素との間のイベント ハンドラー。  登録するための手段を提供<xref:System.Windows.Input.CommandBinding>と<xref:System.Windows.Input.InputBinding>オブジェクトを特定のクラスにドラッグします。  <xref:System.Windows.Input.CommandManager>も提供する、経由、<xref:System.Windows.Input.CommandManager.RequerySuggested>それを発生させるときに、コマンドを通知する、イベント、<xref:System.Windows.Input.ICommand.CanExecuteChanged>イベント。  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A>メソッド フォース、<xref:System.Windows.Input.CommandManager>させる、<xref:System.Windows.Input.CommandManager.RequerySuggested>イベント。  これは、条件必要があるに便利ですコマンドだが無効化/有効化の条件を<xref:System.Windows.Input.CommandManager>を認識します。  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>コマンド ライブラリ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、定義済みのコマンドのセットが用意されています。  コマンドのライブラリは、次のクラス: <xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.NavigationCommands>、 <xref:System.Windows.Input.MediaCommands>、 <xref:System.Windows.Documents.EditingCommands>、および<xref:System.Windows.Input.ComponentCommands>です。  これらのクラスなどのコマンドを入力<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.NavigationCommands.BrowseBack%2A>と<xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>、 <xref:System.Windows.Input.MediaCommands.Play%2A>、 <xref:System.Windows.Input.MediaCommands.Stop%2A>、および<xref:System.Windows.Input.MediaCommands.Pause%2A>です。  
  
 これらのコマンドの多くには、既定の入力バインディングのセットが含まれます。  たとえば、アプリケーションがコピー コマンドを処理することを指定すると、キーボード バインディング "Ctrl + C" が自動的に有効になります。また、[!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] のペン ジェスチャや音声情報などの他の入力デバイスに対するバインディングも有効になります。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使ってさまざまなコマンド ライブラリのコマンドを参照するときは、通常、静的なコマンド プロパティを公開するライブラリ クラスのクラス名を省略できます。 一般に、コマンド名に文字列としての曖昧さはなく、所有する型は、コマンドの論理グループを提供するために存在しますが、曖昧さの解消のためには必要ありません。 たとえば、詳細な `Command="ApplicationCommands.Cut"` ではなく`Command="Cut"` と指定できます。 これに組み込まれている便利なメカニズム、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コマンド プロセッサ (の型コンバーターの動作が正確には、 <xref:System.Windows.Input.ICommand>、どの、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]読み込み時にプロセッサ参照)。  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>カスタム コマンドの作成  
 コマンド ライブラリ クラスのコマンドがニーズを満たさない場合は、独自のコマンドを作成できます。  カスタム コマンドを作成するには 2 つの方法があります。  最初から起動され、実装する、<xref:System.Windows.Input.ICommand>インターフェイスです。  作成するその他の方法より一般的な方法は、<xref:System.Windows.Input.RoutedCommand>または<xref:System.Windows.Input.RoutedUICommand>です。  
  
 カスタムの作成の例については<xref:System.Windows.Input.RoutedCommand>を参照してください[カスタム RoutedCommand サンプルを作成する](http://go.microsoft.com/fwlink/?LinkID=159980)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [ICommandSource を実装する](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [方法: メニュー アイテムにコマンドを追加する](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)  
 [カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)
