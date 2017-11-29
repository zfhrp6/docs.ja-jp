---
title: "方法 : ListView の列の水平方向の配置を変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], horizontal alignment [WPF]
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ed163de9a5b01a3ddab8ef42d21f38d35f48519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-horizontal-alignment-of-a-column-in-a-listview"></a>方法 : ListView の列の水平方向の配置を変更する
既定では、各列のコンテンツ、<xref:System.Windows.Controls.ListViewItem>を左揃えにします。 提供することで各列の配置を変更することができます、<xref:System.Windows.DataTemplate>と設定、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティ内の要素を<xref:System.Windows.DataTemplate>です。 このトピックで説明する方法、<xref:System.Windows.Controls.ListView>を 1 つの列のアラインメントを変更する方法と既定値は、そのコンテンツを揃えます、<xref:System.Windows.Controls.ListView>です。  
  
## <a name="example"></a>例  
 次の例では、内のデータ、`Title`と`ISBN`列を左揃え。  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 アラインメントを変更する、`ISBN`列、ことを指定する必要があります、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>の各プロパティ<xref:System.Windows.Controls.ListViewItem>は<xref:System.Windows.HorizontalAlignment.Stretch>できるように、各要素<xref:System.Windows.Controls.ListViewItem>スパンできますまたは各列の幅全体に合わせて配置します。 <xref:System.Windows.Controls.ListView>がバインドされているデータ ソースに設定するスタイルを作成する必要があります。、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>です。 次に、使用する必要があります、<xref:System.Windows.DataTemplate>を使用せずにコンテンツを表示する、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティです。 表示する、`ISBN`各テンプレートの<xref:System.Windows.DataTemplate>だけ含めることができます、<xref:System.Windows.Controls.TextBlock>を持つその<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティに設定<xref:System.Windows.HorizontalAlignment.Right>です。  
  
 次の例は、スタイルを定義および<xref:System.Windows.DataTemplate>ために必要な`ISBN`列が右揃え、および変更、<xref:System.Windows.Controls.GridViewColumn>参照に、<xref:System.Windows.DataTemplate>です。  
  
 [!code-xaml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xaml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)
