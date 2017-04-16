---
title: "方法 : コマンドを有効にする | Microsoft Docs"
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
  - "CommandBindings"
  - "コマンド実行"
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : コマンドを有効にする
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でコマンド実行を使用する方法を次の例に示します。  この例では、<xref:System.Windows.Input.RoutedCommand> を <xref:System.Windows.Controls.Button> に関連付け、<xref:System.Windows.Input.CommandBinding> を作成して、<xref:System.Windows.Input.RoutedCommand> を実装するイベント ハンドラーを作成する方法を示しています。  コマンド実行の詳細については、「[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)」を参照してください。  
  
## 使用例  
 コードの最初のセクションでは、<xref:System.Windows.Controls.Button> と <xref:System.Windows.Controls.StackPanel> から構成される[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を作成し、コマンド ハンドラーと <xref:System.Windows.Input.RoutedCommand> を関連付ける <xref:System.Windows.Input.CommandBinding> を作成しています。  
  
 <xref:System.Windows.Controls.Button> の <xref:System.Windows.Input.ICommandSource.Command%2A> プロパティは、<xref:System.Windows.Input.ApplicationCommands.Close%2A> コマンドに関連付けられています。  
  
 <xref:System.Windows.Input.CommandBinding> は、ルート <xref:System.Windows.Window> の <xref:System.Windows.Input.CommandBindingCollection> に追加されます。  <xref:System.Windows.Input.CommandBinding.Executed> および <xref:System.Windows.Input.CommandBinding.CanExecute> イベント ハンドラーは、このバインディングに結び付けられ、<xref:System.Windows.Input.ApplicationCommands.Close%2A> コマンドに関連付けられます。  
  
 <xref:System.Windows.Input.CommandBinding> を使用しない場合、コマンド ロジックは実装されず、コマンドを呼び出す機構だけが実行されます。  <xref:System.Windows.Controls.Button> がクリックされると、コマンドの対象で <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> が発生し、続いて <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent> が発生します。  これらのイベントは、その特定のコマンドの <xref:System.Windows.Input.CommandBinding> を要素ツリー内で検索します。  <xref:System.Windows.RoutedEvent> は要素ツリー内をトンネリングおよびバブリングするため、<xref:System.Windows.Input.CommandBinding> を配置する場所には注意が必要です。  <xref:System.Windows.Input.CommandBinding> をコマンドの対象の兄弟、または <xref:System.Windows.RoutedEvent> のルート上にない他のノードに配置すると、<xref:System.Windows.Input.CommandBinding> にはアクセスできません。  
  
 [!code-xml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 コードの次のセクションでは、<xref:System.Windows.Input.CommandManager.Executed> および <xref:System.Windows.Input.CommandBinding.CanExecute> イベント ハンドラーを実装しています。  
  
 <xref:System.Windows.Input.CommandManager.Executed> ハンドラーは、開いているファイルを閉じるメソッドを呼び出します。  <xref:System.Windows.Input.CommandBinding.CanExecute> ハンドラーは、ファイルが開いているかどうかを判別するメソッドを呼び出します。  ファイルが開いている場合、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> は `true` に設定されます。それ以外の場合は `false` に設定されます。  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## 参照  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)