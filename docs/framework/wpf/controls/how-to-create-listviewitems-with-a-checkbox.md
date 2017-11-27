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
ms.openlocfilehash: 4cc6ebb3671dcc65d690fde5d4796c9034553eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>方法 : CheckBox を持つ ListViewItem を作成する
この例は、の列を表示する方法を示しています。<xref:System.Windows.Controls.CheckBox>コントロールで、<xref:System.Windows.Controls.ListView>を使用するコントロール、<xref:System.Windows.Controls.GridView>です。  
  
## <a name="example"></a>例  
 含む列を作成する<xref:System.Windows.Controls.CheckBox>コントロールで、 <xref:System.Windows.Controls.ListView>、作成、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.CheckBox>です。 設定して、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>の<xref:System.Windows.Controls.GridViewColumn>を<xref:System.Windows.DataTemplate>です。  
  
 次の例は、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.CheckBox>です。 例では、バインド、<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>のプロパティ、<xref:System.Windows.Controls.CheckBox>を<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>のプロパティの値、<xref:System.Windows.Controls.ListViewItem>含まれています。 したがって、<xref:System.Windows.Controls.ListViewItem>を格納している、<xref:System.Windows.Controls.CheckBox>が選択されている、<xref:System.Windows.Controls.CheckBox>がチェックします。  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 次の例は、の列を作成する方法を示しています。<xref:System.Windows.Controls.CheckBox>コントロール。 、、の例のセットの列に設定、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>のプロパティ、<xref:System.Windows.Controls.GridViewColumn>を、<xref:System.Windows.DataTemplate>です。  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
