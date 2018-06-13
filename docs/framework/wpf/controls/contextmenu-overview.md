---
title: ContextMenu の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: e862f02e736cb8507dde5036700d751f8af0a226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552871"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="a27fd-102">ContextMenu の概要</span><span class="sxs-lookup"><span data-stu-id="a27fd-102">ContextMenu Overview</span></span>
<span data-ttu-id="a27fd-103"><xref:System.Windows.Controls.ContextMenu>クラスは、特定のコンテキストを使用して、機能を公開する要素を表します<xref:System.Windows.Controls.Menu>です。</span><span class="sxs-lookup"><span data-stu-id="a27fd-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="a27fd-104">通常、ユーザーが公開する、<xref:System.Windows.Controls.ContextMenu>で、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]をマウスのボタンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="a27fd-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="a27fd-105">このトピックでは、<xref:System.Windows.Controls.ContextMenu>要素で使用する方法の例を示します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]とコード。</span><span class="sxs-lookup"><span data-stu-id="a27fd-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="a27fd-106">ContextMenu コントロール</span><span class="sxs-lookup"><span data-stu-id="a27fd-106">ContextMenu Control</span></span>  
 <span data-ttu-id="a27fd-107">A<xref:System.Windows.Controls.ContextMenu>は特定のコントロールにアタッチされています。</span><span class="sxs-lookup"><span data-stu-id="a27fd-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="a27fd-108"><xref:System.Windows.Controls.ContextMenu>要素では、コマンドまたはなどで、特定のコントロールに関連付けられているオプションを指定する項目の一覧をユーザーに提示することができます、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="a27fd-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="a27fd-109">ユーザーがコントロールを右クリックすると、メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a27fd-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="a27fd-110">通常をクリックすると、<xref:System.Windows.Controls.MenuItem>サブメニューを開くかにより、アプリケーションは、コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a27fd-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="a27fd-111">ContextMenu の作成</span><span class="sxs-lookup"><span data-stu-id="a27fd-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="a27fd-112">次の例を作成する方法を示して、<xref:System.Windows.Controls.ContextMenu>サブメニューのあります。</span><span class="sxs-lookup"><span data-stu-id="a27fd-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="a27fd-113"><xref:System.Windows.Controls.ContextMenu>ボタン コントロールに関連付けられているコントロール。</span><span class="sxs-lookup"><span data-stu-id="a27fd-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="a27fd-114">ContextMenu へのスタイルの適用</span><span class="sxs-lookup"><span data-stu-id="a27fd-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="a27fd-115">コントロールを使用して<xref:System.Windows.Style>の動作と外観を大幅に変更することができます、<xref:System.Windows.Controls.ContextMenu>カスタム コントロールを記述することがなくです。</span><span class="sxs-lookup"><span data-stu-id="a27fd-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="a27fd-116">視覚プロパティの設定に加えて、コントロールの一部にスタイルを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a27fd-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="a27fd-117">たとえば、コントロールの一部の動作を変更するには、プロパティを使用して、または、パーツを追加したりのレイアウトを変更、<xref:System.Windows.Controls.ContextMenu>です。</span><span class="sxs-lookup"><span data-stu-id="a27fd-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="a27fd-118">次の例では、いくつかの方法でスタイルを追加して<xref:System.Windows.Controls.ContextMenu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a27fd-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="a27fd-119">最初の例では、`SimpleSysResources` という名前のスタイルを定義し、スタイルで現在のシステム設定を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a27fd-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="a27fd-120">例では、<xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A>として、<xref:System.Windows.Controls.Control.Background%2A>色と<xref:System.Windows.SystemColors.MenuTextBrushKey%2A>として、<xref:System.Windows.Controls.Control.Foreground%2A>の色、<xref:System.Windows.Controls.ContextMenu>です。</span><span class="sxs-lookup"><span data-stu-id="a27fd-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="a27fd-121">次の例では、<xref:System.Windows.Trigger>の外観を変更する要素、<xref:System.Windows.Controls.Menu>上で発生したイベントに応答、<xref:System.Windows.Controls.ContextMenu>です。</span><span class="sxs-lookup"><span data-stu-id="a27fd-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="a27fd-122">ユーザーが、メニューの外観にマウスを移動するときに、<xref:System.Windows.Controls.ContextMenu>項目を変更します。</span><span class="sxs-lookup"><span data-stu-id="a27fd-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a27fd-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a27fd-123">See Also</span></span>  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [<span data-ttu-id="a27fd-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="a27fd-124">ContextMenu</span></span>](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [<span data-ttu-id="a27fd-125">ContextMenu のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="a27fd-125">ContextMenu Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [<span data-ttu-id="a27fd-126">WPF Controls Gallery Sample</span><span class="sxs-lookup"><span data-stu-id="a27fd-126">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
