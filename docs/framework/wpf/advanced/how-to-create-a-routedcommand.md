---
title: "方法 : RoutedCommand を作成する | Microsoft Docs"
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
  - "クラス, RoutedCommand, 作成"
  - "作成, RoutedCommand クラス"
  - "RoutedCommand クラス, 作成"
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : RoutedCommand を作成する
この例では、カスタム <xref:System.Windows.Input.RoutedCommand> を作成する方法、および <xref:System.Windows.Input.ExecutedRoutedEventHandler> と <xref:System.Windows.Input.CanExecuteRoutedEventHandler> を作成して <xref:System.Windows.Input.CommandBinding> に割り当てることによってカスタム コマンドを実装する方法について説明します。  コマンド実行の詳細については、「[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)」を参照してください。  
  
## 使用例  
 <xref:System.Windows.Input.RoutedCommand> の作成の最初の手順は、コマンドを定義してインスタンス化することです。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 コマンドをアプリケーションで使用するには、コマンドの実行内容を定義するイベント ハンドラーを作成する必要があります。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 次に、コマンドをイベント ハンドラーに関連付ける <xref:System.Windows.Input.CommandBinding> が作成されます。  特定のオブジェクトで <xref:System.Windows.Input.CommandBinding> が作成されます。  このオブジェクトは、要素ツリー内の <xref:System.Windows.Input.CommandBinding> のスコープを定義します。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 最後の手順では、コマンドを呼び出します。  コマンドを呼び出す方法の 1 つとして、<xref:System.Windows.Controls.Button> などの <xref:System.Windows.Input.ICommandSource> にコマンドを関連付ける方法があります。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 ボタンがクリックされると、カスタム <xref:System.Windows.Input.RoutedCommand> の <xref:System.Windows.Input.RoutedCommand.Execute%2A> メソッドが呼び出されます。  <xref:System.Windows.Input.RoutedCommand> は、<xref:System.Windows.Input.CommandManager.PreviewExecuted> および <xref:System.Windows.Input.CommandManager.Executed> の各ルーティング イベントを発生させます。  これらのイベントは、この特定のコマンドの <xref:System.Windows.Input.CommandBinding> を要素ツリー内で検索します。  <xref:System.Windows.Input.CommandBinding> が見つかった場合は、<xref:System.Windows.Input.CommandBinding> に関連付けられた <xref:System.Windows.Input.ExecutedRoutedEventHandler> が呼び出されます。  
  
## 参照  
 <xref:System.Windows.Input.RoutedCommand>   
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)