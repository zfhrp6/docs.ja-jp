---
title: '方法 : RoutedCommand を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 75e6c435516fe2a174cf991bd41f24e1b30a212a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-routedcommand"></a>方法 : RoutedCommand を作成する
この例は、カスタムを作成する方法を示しています。<xref:System.Windows.Input.RoutedCommand>および作成することで、カスタム コマンドを実装する方法、<xref:System.Windows.Input.ExecutedRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>にアタッチすると、<xref:System.Windows.Input.CommandBinding>です。  コマンド実行の詳細については、次を参照してください。、[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)です。  
  
## <a name="example"></a>例  
 最初の手順で作成、<xref:System.Windows.Input.RoutedCommand>コマンドの定義およびインスタンス化することができます。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 アプリケーションでコマンドを使用するために、コマンドの動作を定義するイベント ハンドラーを作成する必要があります。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 次に、<xref:System.Windows.Input.CommandBinding>作成コマンドにイベント ハンドラーを関連付けます。 <xref:System.Windows.Input.CommandBinding>が特定のオブジェクトで作成します。  このオブジェクトのスコープを定義する、<xref:System.Windows.Input.CommandBinding>要素ツリー  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 最後の手順では、コマンドを呼び出すことです。  関連付けることは、コマンドを呼び出す方法の 1 つ、 <xref:System.Windows.Input.ICommandSource>、ように、<xref:System.Windows.Controls.Button>です。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 ボタンがクリックされたときに、 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 、カスタム<xref:System.Windows.Input.RoutedCommand>と呼びます。  <xref:System.Windows.Input.RoutedCommand>を発生させます、<xref:System.Windows.Input.CommandManager.PreviewExecuted>と<xref:System.Windows.Input.CommandManager.Executed>イベントにルーティングします。  これらのイベントを探して、要素ツリーを走査する<xref:System.Windows.Input.CommandBinding>この特定のコマンド。  場合、<xref:System.Windows.Input.CommandBinding>が見つかると、<xref:System.Windows.Input.ExecutedRoutedEventHandler>に関連付けられている<xref:System.Windows.Input.CommandBinding>と呼びます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Input.RoutedCommand>  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)
