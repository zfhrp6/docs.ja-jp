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
# <a name="how-to-create-simple-or-complex-treeviews"></a>方法 : 単純または複雑な TreeView を作成する
この例は、単純または複雑なを作成する方法を示しています。<xref:System.Windows.Controls.TreeView>コントロール。  
  
 A<xref:System.Windows.Controls.TreeView>の階層から成る<xref:System.Windows.Controls.TreeViewItem>含めることができる単純なテキスト文字列より複雑なコンテンツなどのコントロール<xref:System.Windows.Controls.Button>コントロールまたは<xref:System.Windows.Controls.StackPanel>埋め込みコンテンツを持つ。 明示的に定義することができます、<xref:System.Windows.Controls.TreeView>コンテンツまたはデータ ソースがコンテンツを提供します。 このトピックでは、これらの概念の例を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のプロパティ、<xref:System.Windows.Controls.TreeViewItem>コンテンツを含むを<xref:System.Windows.Controls.TreeView>その項目が表示されます。 A<xref:System.Windows.Controls.TreeViewItem>こともできます<xref:System.Windows.Controls.TreeViewItem>コントロールとその子要素としてを使用してこれらの子要素を定義することができます、<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティです。  
  
 次の例は、明示的に定義する方法を示しています。<xref:System.Windows.Controls.TreeViewItem>コンテンツを設定して、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>プロパティをテキスト文字列にします。  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 次の例は、の子要素を定義する方法を示して、<xref:System.Windows.Controls.TreeViewItem>を定義して<xref:System.Windows.Controls.ItemsControl.Items%2A>いる<xref:System.Windows.Controls.Button>コントロール。  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>場所、<xref:System.Windows.Data.XmlDataProvider>提供<xref:System.Windows.Controls.TreeViewItem>コンテンツと<xref:System.Windows.HierarchicalDataTemplate>コンテンツの外観を定義します。  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.TreeView>場所、<xref:System.Windows.Controls.TreeViewItem>コンテンツが含まれる<xref:System.Windows.Controls.DockPanel>コンテンツが埋め込まれているコントロール。  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView の概要](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
