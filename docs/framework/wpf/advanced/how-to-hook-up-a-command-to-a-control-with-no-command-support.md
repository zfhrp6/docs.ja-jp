---
title: "方法 : コマンドをサポートしないコントロールにコマンドをフックする | Microsoft Docs"
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
  - "クラス, コントロール, 添付 (RoutedCommand を)"
  - "クラス, RoutedCommand, 添付 (コントロールに)"
  - "Control クラス, 添付 (RoutedCommand を)"
  - "RoutedCommand クラス, 添付 (コントロールに)"
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : コマンドをサポートしないコントロールにコマンドをフックする
コマンドのサポートが組み込まれていない <xref:System.Windows.Controls.Control> に <xref:System.Windows.Input.RoutedCommand> をフックする方法を次の例に示します。  コマンドを複数のソースにフックするサンプル全体については、[カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)を参照してください。  
  
## 使用例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、アプリケーション プログラマがよく使用する一般的なコマンドのライブラリが用意されています。  このコマンド ライブラリには、<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.ComponentCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands>、および <xref:System.Windows.Documents.EditingCommands> クラスが含まれています。  
  
 これらのクラスを構成する静的な <xref:System.Windows.Input.RoutedCommand> オブジェクトには、コマンド ロジックが用意されていません。  コマンドのロジックは、<xref:System.Windows.Input.CommandBinding> でコマンドに関連付けられます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の多くのコントロールには、コマンド ライブリにある一部のコマンドのサポートが組み込まれています。  たとえば、<xref:System.Windows.Controls.TextBox> は、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A>、<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Redo%2A>、<xref:System.Windows.Input.ApplicationCommands.Undo%2A> などの多くのアプリケーション編集コマンドをサポートしています。  アプリケーション開発者は、コントロールで使用するこれらのコマンドを取得するのに特別な作業を行う必要はありません。  <xref:System.Windows.Controls.TextBox> がコマンド ターゲットである場合は、コマンドを実行すると、コントロールに組み込まれている <xref:System.Windows.Input.CommandBinding> を使用してコマンドを処理します。  
  
 <xref:System.Windows.Controls.Button> を <xref:System.Windows.Input.ApplicationCommands.Open%2A> コマンドのコマンド ソースとして使用する方法を次に示します。  指定した <xref:System.Windows.Input.CanExecuteRoutedEventHandler> と、<xref:System.Windows.Input.RoutedCommand> を持つ <xref:System.Windows.Input.CanExecuteRoutedEventHandler> を関連付ける <xref:System.Windows.Input.CommandBinding> を作成します。  
  
 最初に、コマンド ソースを作成します。  コマンド ソースには、<xref:System.Windows.Controls.Button> を使用します。  
  
 [!code-xml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 次に、<xref:System.Windows.Input.ExecutedRoutedEventHandler> および <xref:System.Windows.Input.CanExecuteRoutedEventHandler> を作成します。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> は、コマンドが実行されたことを知らせるために、<xref:System.Windows.MessageBox> を開くだけです。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> は、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> プロパティを `true` に設定します。  通常、実行可能ハンドラーは、そのコマンドが現在のコマンドの対象で実行可能かどうかについて、より信頼性の高いチェックを実行します。  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 最後に、アプリケーションのルート <xref:System.Windows.Window> で、ルーティング イベント ハンドラーを <xref:System.Windows.Input.ApplicationCommands.Open%2A> コマンドに関連付ける <xref:System.Windows.Input.CommandBinding> を作成します。  
  
 [!code-xml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## 参照  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [コマンドをサポートするコントロールにコマンドをフックする](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)