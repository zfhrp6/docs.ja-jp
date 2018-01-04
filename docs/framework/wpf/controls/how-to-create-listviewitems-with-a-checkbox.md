---
title: "方法 : CheckBox を持つ ListViewItem を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be87183efd8101233bd5cbda49d556d09802b630
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>方法 : CheckBox を持つ ListViewItem を作成する
この例は、の列を表示する方法を示しています。<xref:System.Windows.Controls.CheckBox>コントロールで、<xref:System.Windows.Controls.ListView>を使用するコントロール、<xref:System.Windows.Controls.GridView>です。  
  
## <a name="example"></a>例  
 含む列を作成する<xref:System.Windows.Controls.CheckBox>コントロールで、 <xref:System.Windows.Controls.ListView>、作成、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.CheckBox>です。 設定して、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>の<xref:System.Windows.Controls.GridViewColumn>を<xref:System.Windows.DataTemplate>です。  
  
 次の例は、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.CheckBox>です。 例では、バインド、<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>のプロパティ、<xref:System.Windows.Controls.CheckBox>を<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>のプロパティの値、<xref:System.Windows.Controls.ListViewItem>含まれています。 したがって、<xref:System.Windows.Controls.ListViewItem>を格納している、<xref:System.Windows.Controls.CheckBox>が選択されている、<xref:System.Windows.Controls.CheckBox>がチェックします。  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 次の例は、の列を作成する方法を示しています。<xref:System.Windows.Controls.CheckBox>コントロール。 、、の例のセットの列に設定、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>のプロパティ、<xref:System.Windows.Controls.GridViewColumn>を、<xref:System.Windows.DataTemplate>です。  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
