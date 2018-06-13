---
title: '方法 : SelectedValue、SelectedValuePath、および SelectedItem を使用する'
ms.date: 03/30/2017
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
ms.openlocfilehash: 93720c0e1ac96a55fafa36479968cc3492cb0d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554795"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>方法 : SelectedValue、SelectedValuePath、および SelectedItem を使用する
この例を使用する方法を示しています、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>と<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティの値を指定する、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>の<xref:System.Windows.Controls.TreeView>です。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティを指定する方法を提供する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>の<xref:System.Windows.Controls.TreeView.SelectedItem%2A>で、<xref:System.Windows.Controls.TreeView>です。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>内のオブジェクトを表す、<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクションおよび<xref:System.Windows.Controls.TreeView>選択された項目の 1 つのプロパティの値を表示します。 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティの値を決定するために使用されるプロパティへのパスを指定する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>プロパティです。 このトピックの例では、この概念を示します。  
  
 次の例は、<xref:System.Windows.Data.XmlDataProvider>従業員情報を格納します。  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 次の例では定義、<xref:System.Windows.HierarchicalDataTemplate>を表示する、`EmployeeName`と`EmployeeWorkDay`の`Employee`です。 なお、<xref:System.Windows.HierarchicalDataTemplate>で指定されていない、`EmployeeNumber`テンプレートの一部として。  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 次の例は、<xref:System.Windows.Controls.TreeView>を使用して、以前に定義された<xref:System.Windows.HierarchicalDataTemplate>を設定して、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>プロパティを`EmployeeNumber`です。 選択した場合、`EmployeeName`で、 <xref:System.Windows.Controls.TreeView>、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティから返される、 `EmployeeInfo` 、選択した場合に対応するデータ項目`EmployeeName`です。 ただし、ため、<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>この<xref:System.Windows.Controls.TreeView>に設定されている`EmployeeNumber`、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>に設定されている、`EmployeeNumber`です。  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView の概要](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
