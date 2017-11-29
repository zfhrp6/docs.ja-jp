---
title: "方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 246c144a18d7c1014096a6e37ad09b6eec5ad932
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する
この例を使用する方法を示しています、<xref:System.Windows.DataTemplate>と<xref:System.Windows.Style>の外観を指定するオブジェクト、<xref:System.Windows.Controls.ListView>を使用するコントロール、<xref:System.Windows.Controls.GridView>表示モード。  
  
## <a name="example"></a>例  
 次の例に示さ<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>列のヘッダーの外観をカスタマイズするオブジェクト、<xref:System.Windows.Controls.GridViewColumn>です。  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 次の例は、これらを使用する方法を示しています。<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>を設定するオブジェクト、<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>のプロパティ、<xref:System.Windows.Controls.GridViewColumn>です。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティは、列のセルのコンテンツを定義します。  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>は 2 つの列ヘッダーの外観をカスタマイズに使用できるいくつかのプロパティののみ、<xref:System.Windows.Controls.GridView>コントロール。 詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)を参照してください。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.DataTemplate>内のセルの外観をカスタマイズする、<xref:System.Windows.Controls.GridViewColumn>です。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 次の例は、これを使用する方法を示しています。<xref:System.Windows.DataTemplate>のコンテンツを定義する、<xref:System.Windows.Controls.GridViewColumn>セル。 代わりにこのテンプレートを使用、 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 、前に表示されるプロパティ<xref:System.Windows.Controls.GridViewColumn>例です。  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)
