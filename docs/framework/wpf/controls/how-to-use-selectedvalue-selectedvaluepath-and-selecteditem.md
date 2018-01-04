---
title: "方法 : SelectedValue、SelectedValuePath、および SelectedItem を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6355ed45d7422735d1dac1e1419990e1c5bd120
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="b7079-102">方法 : SelectedValue、SelectedValuePath、および SelectedItem を使用する</span><span class="sxs-lookup"><span data-stu-id="b7079-102">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="b7079-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>と<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティの値を指定する、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>の<xref:System.Windows.Controls.TreeView>です。</span><span class="sxs-lookup"><span data-stu-id="b7079-103">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7079-104">例</span><span class="sxs-lookup"><span data-stu-id="b7079-104">Example</span></span>  
 <span data-ttu-id="b7079-105"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティを指定する方法を提供する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>の<xref:System.Windows.Controls.TreeView.SelectedItem%2A>で、<xref:System.Windows.Controls.TreeView>です。</span><span class="sxs-lookup"><span data-stu-id="b7079-105">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="b7079-106"><xref:System.Windows.Controls.TreeView.SelectedItem%2A>内のオブジェクトを表す、<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクションおよび<xref:System.Windows.Controls.TreeView>選択された項目の 1 つのプロパティの値を表示します。</span><span class="sxs-lookup"><span data-stu-id="b7079-106">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="b7079-107"><xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティの値を決定するために使用されるプロパティへのパスを指定する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b7079-107">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="b7079-108">このトピックの例では、この概念を示します。</span><span class="sxs-lookup"><span data-stu-id="b7079-108">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="b7079-109">次の例は、<xref:System.Windows.Data.XmlDataProvider>従業員情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7079-109">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="b7079-110">次の例では定義、<xref:System.Windows.HierarchicalDataTemplate>を表示する、`EmployeeName`と`EmployeeWorkDay`の`Employee`です。</span><span class="sxs-lookup"><span data-stu-id="b7079-110">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="b7079-111">なお、<xref:System.Windows.HierarchicalDataTemplate>で指定されていない、`EmployeeNumber`テンプレートの一部として。</span><span class="sxs-lookup"><span data-stu-id="b7079-111">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="b7079-112">次の例は、<xref:System.Windows.Controls.TreeView>を使用して、以前に定義された<xref:System.Windows.HierarchicalDataTemplate>を設定して、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>プロパティを`EmployeeNumber`です。</span><span class="sxs-lookup"><span data-stu-id="b7079-112">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="b7079-113">選択した場合、`EmployeeName`で、 <xref:System.Windows.Controls.TreeView>、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティから返される、 `EmployeeInfo` 、選択した場合に対応するデータ項目`EmployeeName`です。</span><span class="sxs-lookup"><span data-stu-id="b7079-113">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="b7079-114">ただし、ため、<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>この<xref:System.Windows.Controls.TreeView>に設定されている`EmployeeNumber`、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>に設定されている、`EmployeeNumber`です。</span><span class="sxs-lookup"><span data-stu-id="b7079-114">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="b7079-115">参照</span><span class="sxs-lookup"><span data-stu-id="b7079-115">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="b7079-116">TreeView の概要</span><span class="sxs-lookup"><span data-stu-id="b7079-116">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="b7079-117">方法トピック</span><span class="sxs-lookup"><span data-stu-id="b7079-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
