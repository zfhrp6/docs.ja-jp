---
title: '方法 : コマンドを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: 81ae2e46c4fdd8b46e2b72b9a1430437ebfe97b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545283"
---
# <a name="how-to-enable-a-command"></a>方法 : コマンドを有効にする
次の例は、のコマンドを使用する方法を示します[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。  関連付ける方法の例、<xref:System.Windows.Input.RoutedCommand>を<xref:System.Windows.Controls.Button>、作成、<xref:System.Windows.Input.CommandBinding>を実装するイベント ハンドラーを作成し、<xref:System.Windows.Input.RoutedCommand>です。  コマンド実行の詳細については、次を参照してください。、[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)です。  
  
## <a name="example"></a>例  
 コードの最初のセクションを作成、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]から構成される、<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.StackPanel>、し、作成、<xref:System.Windows.Input.CommandBinding>とコマンド ハンドラーを関連付ける、<xref:System.Windows.Input.RoutedCommand>です。  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A>のプロパティ、<xref:System.Windows.Controls.Button>に関連付けられている、<xref:System.Windows.Input.ApplicationCommands.Close%2A>コマンド。  
  
 <xref:System.Windows.Input.CommandBinding>に追加、<xref:System.Windows.Input.CommandBindingCollection>ルートの<xref:System.Windows.Window>します。 <xref:System.Windows.Input.CommandBinding.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベント ハンドラーがこのバインディングにアタッチされているしに関連付けられている、<xref:System.Windows.Input.ApplicationCommands.Close%2A>コマンド。  
  
 なし、<xref:System.Windows.Input.CommandBinding>コマンド ロジック、のみのコマンドを呼び出すメカニズムがないです。  ときに、<xref:System.Windows.Controls.Button>がクリックされると、 <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>続けてコマンド ターゲットで発生した、 <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>です。  これらのイベントを探して、要素ツリーを走査する<xref:System.Windows.Input.CommandBinding>その特定のコマンド。  注意するため<xref:System.Windows.RoutedEvent>トンネルと、要素ツリーを通じてバブルでは、注意が必要で、<xref:System.Windows.Input.CommandBinding>配置されます。   場合、<xref:System.Windows.Input.CommandBinding>コマンド ターゲットまたはのルートにないに別のノードの兄弟では、 <xref:System.Windows.RoutedEvent>、<xref:System.Windows.Input.CommandBinding>アクセスできません。  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 コードを実装の次のセクション、<xref:System.Windows.Input.CommandManager.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベント ハンドラー。  
  
 <xref:System.Windows.Input.CommandManager.Executed>ハンドラー、メソッドを呼び出して、開いているファイルを閉じます。  <xref:System.Windows.Input.CommandBinding.CanExecute>ハンドラーは、ファイルが開いているかどうかを決定するメソッドを呼び出します。  場合は、ファイルを開いて、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>に設定されている`true`、それ以外に設定されている`false`です。  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>関連項目  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)
