---
title: "GridView の列ヘッダー スタイルおｙびテンプレートの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad0f7cacc8256e060bb12611bd1818b694e1e6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView の列ヘッダー スタイルおｙびテンプレートの概要
この概要説明のカスタマイズ内の列ヘッダーを使用するプロパティの優先順位、<xref:System.Windows.Controls.GridView>の表示モード、<xref:System.Windows.Controls.ListView>コントロール。  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>GridView 内の列ヘッダーをカスタマイズします。  
 コンテンツ、レイアウト、および内の列ヘッダーのスタイルを定義するプロパティ、<xref:System.Windows.Controls.GridView>が多くの関連クラス上に存在します。 これらのプロパティの一部は、または同一の次のような機能があります。  
  
 次の表に行は、同じ機能を実行したプロパティのグループを表示します。 内の列ヘッダーをカスタマイズするこれらのプロパティを使用することができます、<xref:System.Windows.Controls.GridView>です。 関連するプロパティの優先順位の順序は、一番右側の列のプロパティが最高の優先順位が右から左へです。 たとえば場合、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>に設定されている、<xref:System.Windows.Controls.GridViewColumnHeader>オブジェクトおよび<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>、関連する設定は、 <xref:System.Windows.Controls.GridViewColumn>、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>が優先されます。 このシナリオでは、<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>も何も起こりません。  
  
 **GridView で列ヘッダーに関連するプロパティ**  
  
|||||  
|-|-|-|-|  
|**クラス**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**コンテキスト メニューのプロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|利用不可|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ToolTip**<br /><br /> **プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|利用不可|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**ヘッダーのテンプレート**<br /><br /> **プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**スタイル プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>の**ヘッダー テンプレート プロパティ**テンプレートとテンプレート セレクターのプロパティをテンプレートのプロパティが優先されますの両方を設定する場合は、します。 たとえば、両方を設定する場合、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>と<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>、プロパティ、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティが優先されます。  
  
## <a name="see-also"></a>関連項目  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
