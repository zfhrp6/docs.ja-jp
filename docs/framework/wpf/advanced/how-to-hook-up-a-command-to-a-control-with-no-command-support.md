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
ms.workload: dotnet
ms.openlocfilehash: 804c4ffd54a0f8cc94e8849a223b1af8b27a58b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a><span data-ttu-id="eccbe-102">方法 : コマンドをサポートしないコントロールにコマンドをフックする</span><span class="sxs-lookup"><span data-stu-id="eccbe-102">How to: Hook Up a Command to a Control with No Command Support</span></span>
<span data-ttu-id="eccbe-103">次の例にフックする方法を示しています、<xref:System.Windows.Input.RoutedCommand>を<xref:System.Windows.Controls.Control>が組み込まれていないコマンドのサポート。</span><span class="sxs-lookup"><span data-stu-id="eccbe-103">The following example shows how to hook up a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Control> which does not have built in support for the command.</span></span>  <span data-ttu-id="eccbe-104">コマンドを複数のソースに関連付けるサンプル全体については、「[カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccbe-104">For a complete sample which hooks up commands to multiple sources, see the [Create a Custom RoutedCommand Sample](http://go.microsoft.com/fwlink/?LinkID=159980) sample.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eccbe-105">例</span><span class="sxs-lookup"><span data-stu-id="eccbe-105">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="eccbe-106"> には、アプリケーション プログラマがよく使用する一般的なコマンドのライブラリが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eccbe-106"> provides a library of common commands which application programmers encounter regularly.</span></span>  <span data-ttu-id="eccbe-107">コマンドのライブラリを構成するクラスは、: <xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.ComponentCommands>、 <xref:System.Windows.Input.NavigationCommands>、 <xref:System.Windows.Input.MediaCommands>、および<xref:System.Windows.Documents.EditingCommands>です。</span><span class="sxs-lookup"><span data-stu-id="eccbe-107">The classes which comprise the command library are: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, and <xref:System.Windows.Documents.EditingCommands>.</span></span>  
  
 <span data-ttu-id="eccbe-108">静的な<xref:System.Windows.Input.RoutedCommand>これらのクラスを構成するコマンドのロジックを指定しません。</span><span class="sxs-lookup"><span data-stu-id="eccbe-108">The static <xref:System.Windows.Input.RoutedCommand> objects which make up these classes do not supply command logic.</span></span>  <span data-ttu-id="eccbe-109">コマンドのロジックは、コマンドに関連付けられて、<xref:System.Windows.Input.CommandBinding>です。</span><span class="sxs-lookup"><span data-stu-id="eccbe-109">The logic for the command is associated with the command with a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="eccbe-110">多くのコントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コマンド ライブラリ内のコマンドの一部のサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="eccbe-110">Many controls in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] have built in support for some of the commands in the command library.</span></span>  <span data-ttu-id="eccbe-111"><xref:System.Windows.Controls.TextBox>、たとえば、多くのアプリケーションの編集コマンドなどをサポート<xref:System.Windows.Input.ApplicationCommands.Paste%2A>、 <xref:System.Windows.Input.ApplicationCommands.Copy%2A>、 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、 <xref:System.Windows.Input.ApplicationCommands.Redo%2A>、および<xref:System.Windows.Input.ApplicationCommands.Undo%2A>です。</span><span class="sxs-lookup"><span data-stu-id="eccbe-111"><xref:System.Windows.Controls.TextBox>, for example, supports many of the application edit commands such as <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, and <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span></span>  <span data-ttu-id="eccbe-112">アプリケーション開発者は、コントロールで使用するこれらのコマンドを取得するのに特別な作業を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="eccbe-112">The application developer does not have to do anything special to get these commands to work with these controls.</span></span>  <span data-ttu-id="eccbe-113">場合、<xref:System.Windows.Controls.TextBox>コマンド ターゲットを使用してコマンドを処理するコマンドを実行すると、<xref:System.Windows.Input.CommandBinding>コントロールに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="eccbe-113">If the <xref:System.Windows.Controls.TextBox> is the command target when the command is executed, it will handle the command using the <xref:System.Windows.Input.CommandBinding> that is built into the control.</span></span>  
  
 <span data-ttu-id="eccbe-114">使用する方法を次に示します、<xref:System.Windows.Controls.Button>コマンドのソースとして、<xref:System.Windows.Input.ApplicationCommands.Open%2A>コマンド。</span><span class="sxs-lookup"><span data-stu-id="eccbe-114">The following shows how to use a <xref:System.Windows.Controls.Button> as the command source for the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  <span data-ttu-id="eccbe-115">A<xref:System.Windows.Input.CommandBinding>が作成される、指定された関連付ける<xref:System.Windows.Input.CanExecuteRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>で、<xref:System.Windows.Input.RoutedCommand>です。</span><span class="sxs-lookup"><span data-stu-id="eccbe-115">A <xref:System.Windows.Input.CommandBinding> is created that associates the specified <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="eccbe-116">最初に、コマンド ソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="eccbe-116">First, the command source is created.</span></span>  <span data-ttu-id="eccbe-117">A<xref:System.Windows.Controls.Button>コマンド ソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="eccbe-117">A <xref:System.Windows.Controls.Button> is used as the command source.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <span data-ttu-id="eccbe-118">次に、<xref:System.Windows.Input.ExecutedRoutedEventHandler>と<xref:System.Windows.Input.CanExecuteRoutedEventHandler>が作成されます。</span><span class="sxs-lookup"><span data-stu-id="eccbe-118">Next, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> are created.</span></span>  <span data-ttu-id="eccbe-119"><xref:System.Windows.Input.ExecutedRoutedEventHandler>だけが表示されます、<xref:System.Windows.MessageBox>コマンドが実行されることを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="eccbe-119">The <xref:System.Windows.Input.ExecutedRoutedEventHandler> simply opens a <xref:System.Windows.MessageBox> to signify that the command executed.</span></span>  <span data-ttu-id="eccbe-120"><xref:System.Windows.Input.CanExecuteRoutedEventHandler>設定、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="eccbe-120">The <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sets the <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> property to `true`.</span></span>  <span data-ttu-id="eccbe-121">通常、実行ハンドラーがより堅牢なチェックを実行し、現在のコマンド ターゲットでコマンドを実行できなかったかどうかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccbe-121">Normally, the can execute handler would perform more robust checks to see if the command could execute on the current command target.</span></span>  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 <span data-ttu-id="eccbe-122">最後に、<xref:System.Windows.Input.CommandBinding>ルートに作成された<xref:System.Windows.Window>にルーティングされたイベント ハンドラーに関連付けるアプリケーションの<xref:System.Windows.Input.ApplicationCommands.Open%2A>コマンド。</span><span class="sxs-lookup"><span data-stu-id="eccbe-122">Finally, a <xref:System.Windows.Input.CommandBinding> is created on the root <xref:System.Windows.Window> of the application that associates the routed events handlers to the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a><span data-ttu-id="eccbe-123">参照</span><span class="sxs-lookup"><span data-stu-id="eccbe-123">See Also</span></span>  
 [<span data-ttu-id="eccbe-124">コマンド実行の概要</span><span class="sxs-lookup"><span data-stu-id="eccbe-124">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="eccbe-125">コマンドをサポートするコントロールにコマンドをフックする</span><span class="sxs-lookup"><span data-stu-id="eccbe-125">Hook Up a Command to a Control with Command Support</span></span>](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
