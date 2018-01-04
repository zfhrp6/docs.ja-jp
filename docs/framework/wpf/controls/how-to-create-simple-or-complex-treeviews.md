---
title: "方法 : 単純または複雑な TreeView を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a7e87295a50f901be0c7028bb2d6025b51c248c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="5e3dd-102">方法 : 単純または複雑な TreeView を作成する</span><span class="sxs-lookup"><span data-stu-id="5e3dd-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="5e3dd-103">この例は、単純または複雑なを作成する方法を示しています。<xref:System.Windows.Controls.TreeView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="5e3dd-104">A<xref:System.Windows.Controls.TreeView>の階層から成る<xref:System.Windows.Controls.TreeViewItem>含めることができる単純なテキスト文字列より複雑なコンテンツなどのコントロール<xref:System.Windows.Controls.Button>コントロールまたは<xref:System.Windows.Controls.StackPanel>埋め込みコンテンツを持つ。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="5e3dd-105">明示的に定義することができます、<xref:System.Windows.Controls.TreeView>コンテンツまたはデータ ソースがコンテンツを提供します。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="5e3dd-106">このトピックでは、これらの概念の例を示します。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e3dd-107">例</span><span class="sxs-lookup"><span data-stu-id="5e3dd-107">Example</span></span>  
 <span data-ttu-id="5e3dd-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のプロパティ、<xref:System.Windows.Controls.TreeViewItem>コンテンツを含むを<xref:System.Windows.Controls.TreeView>その項目が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="5e3dd-109">A<xref:System.Windows.Controls.TreeViewItem>こともできます<xref:System.Windows.Controls.TreeViewItem>コントロールとその子要素としてを使用してこれらの子要素を定義することができます、<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="5e3dd-110">次の例は、明示的に定義する方法を示しています。<xref:System.Windows.Controls.TreeViewItem>コンテンツを設定して、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>プロパティをテキスト文字列にします。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="5e3dd-111">次の例は、の子要素を定義する方法を示して、<xref:System.Windows.Controls.TreeViewItem>を定義して<xref:System.Windows.Controls.ItemsControl.Items%2A>いる<xref:System.Windows.Controls.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="5e3dd-112">次の例を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>場所、<xref:System.Windows.Data.XmlDataProvider>提供<xref:System.Windows.Controls.TreeViewItem>コンテンツと<xref:System.Windows.HierarchicalDataTemplate>コンテンツの外観を定義します。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="5e3dd-113">次の例を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>場所、<xref:System.Windows.Controls.TreeViewItem>コンテンツが含まれる<xref:System.Windows.Controls.DockPanel>コンテンツが埋め込まれているコントロール。</span><span class="sxs-lookup"><span data-stu-id="5e3dd-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="5e3dd-114">参照</span><span class="sxs-lookup"><span data-stu-id="5e3dd-114">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="5e3dd-115">TreeView の概要</span><span class="sxs-lookup"><span data-stu-id="5e3dd-115">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="5e3dd-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="5e3dd-116">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
