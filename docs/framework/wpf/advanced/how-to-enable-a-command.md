---
title: "方法 : コマンドを有効にする"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90f7f69aebf48bbc27321d3808468a2df49f793
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="c2fc0-102">方法 : コマンドを有効にする</span><span class="sxs-lookup"><span data-stu-id="c2fc0-102">How to: Enable a Command</span></span>
<span data-ttu-id="c2fc0-103">次の例は、のコマンドを使用する方法を示します[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="c2fc0-104">関連付ける方法の例、<xref:System.Windows.Input.RoutedCommand>を<xref:System.Windows.Controls.Button>、作成、<xref:System.Windows.Input.CommandBinding>を実装するイベント ハンドラーを作成し、<xref:System.Windows.Input.RoutedCommand>です。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="c2fc0-105">コマンド実行の詳細については、次を参照してください。、[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-105">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2fc0-106">例</span><span class="sxs-lookup"><span data-stu-id="c2fc0-106">Example</span></span>  
 <span data-ttu-id="c2fc0-107">コードの最初のセクションを作成、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]から構成される、<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.StackPanel>、し、作成、<xref:System.Windows.Input.CommandBinding>とコマンド ハンドラーを関連付ける、<xref:System.Windows.Input.RoutedCommand>です。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="c2fc0-108"><xref:System.Windows.Input.ICommandSource.Command%2A>のプロパティ、<xref:System.Windows.Controls.Button>に関連付けられている、<xref:System.Windows.Input.ApplicationCommands.Close%2A>コマンド。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="c2fc0-109"><xref:System.Windows.Input.CommandBinding>に追加、<xref:System.Windows.Input.CommandBindingCollection>ルートの<xref:System.Windows.Window>します。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="c2fc0-110"><xref:System.Windows.Input.CommandBinding.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベント ハンドラーがこのバインディングにアタッチされているしに関連付けられている、<xref:System.Windows.Input.ApplicationCommands.Close%2A>コマンド。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="c2fc0-111">なし、<xref:System.Windows.Input.CommandBinding>コマンド ロジック、のみのコマンドを呼び出すメカニズムがないです。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="c2fc0-112">ときに、<xref:System.Windows.Controls.Button>がクリックされると、 <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent>続けてコマンド ターゲットで発生した、 <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>です。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="c2fc0-113">これらのイベントを探して、要素ツリーを走査する<xref:System.Windows.Input.CommandBinding>その特定のコマンド。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="c2fc0-114">注意するため<xref:System.Windows.RoutedEvent>トンネルと、要素ツリーを通じてバブルでは、注意が必要で、<xref:System.Windows.Input.CommandBinding>配置されます。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="c2fc0-115">場合、<xref:System.Windows.Input.CommandBinding>コマンド ターゲットまたはのルートにないに別のノードの兄弟では、 <xref:System.Windows.RoutedEvent>、<xref:System.Windows.Input.CommandBinding>アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="c2fc0-116">コードを実装の次のセクション、<xref:System.Windows.Input.CommandManager.Executed>と<xref:System.Windows.Input.CommandBinding.CanExecute>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="c2fc0-117"><xref:System.Windows.Input.CommandManager.Executed>ハンドラー、メソッドを呼び出して、開いているファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="c2fc0-118"><xref:System.Windows.Input.CommandBinding.CanExecute>ハンドラーは、ファイルが開いているかどうかを決定するメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="c2fc0-119">場合は、ファイルを開いて、<xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A>に設定されている`true`、それ以外に設定されている`false`です。</span><span class="sxs-lookup"><span data-stu-id="c2fc0-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="c2fc0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2fc0-120">See Also</span></span>  
 [<span data-ttu-id="c2fc0-121">コマンド実行の概要</span><span class="sxs-lookup"><span data-stu-id="c2fc0-121">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
