---
title: "方法 : コマンドをサポートしないコントロールにコマンドをフックする"
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
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f38a6f900ee2b253708da4b63bdc2f474fa3ab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>方法 : コマンドをサポートしないコントロールにコマンドをフックする
次の例にフックする方法を示しています、<xref:System.Windows.Input.RoutedCommand>を<xref:System.Windows.Controls.Control>が組み込まれていないコマンドのサポート。  コマンドを複数のソースに関連付けるサンプル全体については、「[カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)」を参照してください。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、アプリケーション プログラマがよく使用する一般的なコマンドのライブラリが用意されています。  コマンドのライブラリを構成するクラスは、: <xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.ComponentCommands>、 <xref:System.Windows.Input.NavigationCommands>、 <xref:System.Windows.Input.MediaCommands>、および<xref:System.Windows.Documents.EditingCommands>です。  
  
 静的な<xref:System.Windows.Input.RoutedCommand>これらのクラスを構成するコマンドのロジックを指定しません。  コマンドのロジックは、コマンドに関連付けられて、<xref:System.Windows.Input.CommandBinding>です。  多くのコントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コマンド ライブラリ内のコマンドの一部のサポートが組み込まれています。  <xref:System.Windows.Controls.TextBox>、たとえば、多くのアプリケーションの編集コマンドなどをサポート<xref:System.Windows.Input.ApplicationCommands.Paste%2A>、 <xref:System.Windows.Input.ApplicationCommands.Copy%2A>、 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、 <xref:System.Windows.Input.ApplicationCommands.Redo%2A>、および<xref:System.Windows.Input.ApplicationCommands.Undo%2A>です。  アプリケーション開発者は、コントロールで使用するこれらのコマンドを取得するのに特別な作業を行う必要はありません。  場合、<xref:System.Windows.Controls.TextBox>コマンド ターゲットを使用してコマンドを処理するコマンドを実行すると、<xref:System.Windows.Input.CommandBinding>コントロールに組み込まれています。  
  
 使用する方法を次に示します、<xref:System.Windows.Controls.Button>コマンドのソースとして、<xref:System.Windows.Input.ApplicationCommands.Open%2A>コマンド。  A<xref:System.Windows.Input.CommandBinding>が作成される、指定された関連付ける<xref:System.Windows.Input.CanExecuteRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>で、<xref:System.Windows.Input.RoutedCommand>です。  
  
 最初に、コマンド ソースが作成されます。  A<xref:System.Windows.Controls.Button>コマンド ソースとして使用されます。  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 次に、<xref:System.Windows.Input.ExecutedRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>が作成されます。  <xref:System.Windows.Input.ExecutedRoutedEventHandler>だけが表示されます、<xref:System.Windows.MessageBox>コマンドが実行されることを示すためにします。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>設定、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>プロパティを`true`です。  通常、実行ハンドラーがより堅牢なチェックを実行し、現在のコマンド ターゲットでコマンドを実行できなかったかどうかを参照してください。  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 最後に、<xref:System.Windows.Input.CommandBinding>ルートに作成された<xref:System.Windows.Window>にルーティングされたイベント ハンドラーに関連付けるアプリケーションの<xref:System.Windows.Input.ApplicationCommands.Open%2A>コマンド。  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>関連項目  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [コマンドをサポートするコントロールにコマンドをフックする](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
