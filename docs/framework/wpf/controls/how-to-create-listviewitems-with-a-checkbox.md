---
title: "方法 : CheckBox を持つ ListViewItem を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ListView コントロール"
  - "コントロール、チェック ボックス"
  - "CheckBox コントロールを ListView コントロールします。"
  - "ListView コントロールでチェック ボックス コントロール"
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : CheckBox を持つ ListViewItem を作成する
この例の列を表示する方法を示しています<xref:System.Windows.Controls.CheckBox>コントロールで、 <xref:System.Windows.Controls.ListView>を使用するコントロール、 <xref:System.Windows.Controls.GridView>します。  
  
## <a name="example"></a>例  
 含む列を作成する<xref:System.Windows.Controls.CheckBox>コントロールで、 <xref:System.Windows.Controls.ListView>、作成、 <xref:System.Windows.DataTemplate>を含む、 <xref:System.Windows.Controls.CheckBox>します。 設定し、 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>の<xref:System.Windows.Controls.GridViewColumn>に、 <xref:System.Windows.DataTemplate>します。  
  
 例を次に、 <xref:System.Windows.DataTemplate>を含む、 <xref:System.Windows.Controls.CheckBox>します。 この例で、 <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>のプロパティ、 <xref:System.Windows.Controls.CheckBox>に、 <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>のプロパティの値、 <xref:System.Windows.Controls.ListViewItem>含まれています。 したがってときに、 <xref:System.Windows.Controls.ListViewItem>を含む、<xref:System.Windows.Controls.CheckBox>が選択されている、<xref:System.Windows.Controls.CheckBox>がオンになっています。  
  
 [!code-xml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 次の例の列を作成する方法を示しています。 <xref:System.Windows.Controls.CheckBox>コントロールです。 例のセットの列に設定、 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>のプロパティ、 <xref:System.Windows.Controls.GridViewColumn>に、 <xref:System.Windows.DataTemplate>します。  
  
 [!code-xml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Control>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [操作方法に関するトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)