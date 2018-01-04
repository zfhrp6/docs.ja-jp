---
title: "メニューの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ab5092b1bc9db22390a18b2c1cb1ad5725a2037
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="menu-overview"></a><span data-ttu-id="4e25b-102">メニューの概要</span><span class="sxs-lookup"><span data-stu-id="4e25b-102">Menu Overview</span></span>
<span data-ttu-id="4e25b-103"><xref:System.Windows.Controls.Menu>クラスでは、コマンドおよび階層の順序でイベント ハンドラーに関連付けられている要素を整理することができます。</span><span class="sxs-lookup"><span data-stu-id="4e25b-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="4e25b-104">各<xref:System.Windows.Controls.Menu>要素のコレクションを含みます<xref:System.Windows.Controls.MenuItem>要素。</span><span class="sxs-lookup"><span data-stu-id="4e25b-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="4e25b-105">メニュー コントロール</span><span class="sxs-lookup"><span data-stu-id="4e25b-105">Menu Control</span></span>  
 <span data-ttu-id="4e25b-106"><xref:System.Windows.Controls.Menu>コントロール コマンドまたはアプリケーションのオプションを指定する項目の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e25b-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="4e25b-107">通常をクリックすると、<xref:System.Windows.Controls.MenuItem>サブメニューを開くかにより、アプリケーションは、コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e25b-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="4e25b-108">メニューの作成</span><span class="sxs-lookup"><span data-stu-id="4e25b-108">Creating Menus</span></span>  
 <span data-ttu-id="4e25b-109">次の例を作成、<xref:System.Windows.Controls.Menu>内のテキストを操作する、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="4e25b-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="4e25b-110"><xref:System.Windows.Controls.Menu>が含まれています<xref:System.Windows.Controls.MenuItem>使用するオブジェクト、 <xref:System.Windows.Controls.MenuItem.Command%2A>、 <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>、および<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>プロパティおよび<xref:System.Windows.Controls.MenuItem.Checked>、 <xref:System.Windows.Controls.MenuItem.Unchecked>、および<xref:System.Windows.Controls.MenuItem.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="4e25b-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="4e25b-111">キーボード ショートカット付きのメニュー項目</span><span class="sxs-lookup"><span data-stu-id="4e25b-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="4e25b-112">キーボード ショートカットは、キーボードで入力できる文字の組み合わせ<xref:System.Windows.Controls.Menu>コマンド。</span><span class="sxs-lookup"><span data-stu-id="4e25b-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="4e25b-113">たとえば、**コピー**のショートカットは CTRL+C です。</span><span class="sxs-lookup"><span data-stu-id="4e25b-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="4e25b-114">キーボード ショートカットやメニュー項目に使用する 2 つのプロパティ-<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>または<xref:System.Windows.Controls.MenuItem.Command%2A>です。</span><span class="sxs-lookup"><span data-stu-id="4e25b-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="4e25b-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="4e25b-115">InputGestureText</span></span>  
 <span data-ttu-id="4e25b-116">次の例を使用する方法を示しています、<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>にキーボード ショートカット テキストを割り当てるプロパティを<xref:System.Windows.Controls.MenuItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4e25b-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="4e25b-117">これは、キーボード ショートカットをメニュー項目に配置するだけです。</span><span class="sxs-lookup"><span data-stu-id="4e25b-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="4e25b-118">コマンドでは関連付けません、<xref:System.Windows.Controls.MenuItem>です。</span><span class="sxs-lookup"><span data-stu-id="4e25b-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="4e25b-119">アプリケーションでは、アクションを実行するために、ユーザーの入力を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e25b-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="4e25b-120">コマンド</span><span class="sxs-lookup"><span data-stu-id="4e25b-120">Command</span></span>  
 <span data-ttu-id="4e25b-121">使用する次の例に示します、<xref:System.Windows.Controls.MenuItem.Command%2A>プロパティに関連付けるには、**開く**と**保存**コマンドと<xref:System.Windows.Controls.MenuItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4e25b-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="4e25b-122">コマンドのプロパティはコマンドに関連付けるだけでなく、 <xref:System.Windows.Controls.MenuItem>、もショートカットとして使用する入力ジェスチャ テキストを提供しています。</span><span class="sxs-lookup"><span data-stu-id="4e25b-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="4e25b-123"><xref:System.Windows.Controls.MenuItem>クラスもあります、<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>プロパティをコマンドが発生した要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="4e25b-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="4e25b-124">場合<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>が設定された場合、キーボード フォーカスを持つ要素は、コマンドを受信します。</span><span class="sxs-lookup"><span data-stu-id="4e25b-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="4e25b-125">コマンドの詳細については、[Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e25b-125">For more information about commands, see [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="4e25b-126">メニューのスタイル指定</span><span class="sxs-lookup"><span data-stu-id="4e25b-126">Menu Styling</span></span>  
 <span data-ttu-id="4e25b-127">コントロールのスタイル設定を大幅に変更の動作と外観<xref:System.Windows.Controls.Menu>をカスタム コントロールを記述しなくても制御します。</span><span class="sxs-lookup"><span data-stu-id="4e25b-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="4e25b-128">視覚プロパティの設定に加えて適用することも、<xref:System.Windows.Style>コントロールの各部分に、プロパティを使用してコントロールの一部の動作を変更または追加部分を追加またはコントロールのレイアウトを変更します。</span><span class="sxs-lookup"><span data-stu-id="4e25b-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="4e25b-129">次の例では、いくつかの方法を追加する、<xref:System.Windows.Style>を<xref:System.Windows.Controls.Menu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4e25b-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="4e25b-130">最初のコード例では定義、<xref:System.Windows.Style>と呼ばれる`Simple`を自分のスタイルで現在のシステム設定を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4e25b-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="4e25b-131">このコードは、`MenuHighlightBrush`の色をメニューの背景色として、 `MenuTextBrush`の色をメニューの前景色として割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4e25b-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="4e25b-132">ブラシを割り当てるには、リソース キーを使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4e25b-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="4e25b-133">次のサンプルは<xref:System.Windows.Trigger>要素の外観を変更できる、<xref:System.Windows.Controls.MenuItem>で発生するイベントに応答、<xref:System.Windows.Controls.Menu>です。</span><span class="sxs-lookup"><span data-stu-id="4e25b-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="4e25b-134">上でマウスを移動すると、 <xref:System.Windows.Controls.Menu>、前景色を指定し、メニュー項目のフォント特性を変更します。</span><span class="sxs-lookup"><span data-stu-id="4e25b-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4e25b-135">参照</span><span class="sxs-lookup"><span data-stu-id="4e25b-135">See Also</span></span>  
 [<span data-ttu-id="4e25b-136">WPF Controls Gallery Sample</span><span class="sxs-lookup"><span data-stu-id="4e25b-136">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
