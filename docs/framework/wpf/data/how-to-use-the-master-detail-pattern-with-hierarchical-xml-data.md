---
title: "方法 : 階層 XML データでマスター詳細パターンを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ef460664b3701f4942b8c28b8e39f891d7c871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>方法 : 階層 XML データでマスター詳細パターンを使用する
この例を使用したマスター/詳細シナリオを実装する方法を示しています。[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ。  
  
## <a name="example"></a>例  
 この例は、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ バージョンので説明した例[階層データをマスター/詳細形式のパターンを使用して](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)です。 この例では、データ ファイルが`League.xml`です。 注方法、3 番目の<xref:System.Windows.Controls.ListBox>コントロールは、2 番目の選択範囲の変更を追跡<xref:System.Windows.Controls.ListBox>にバインドしてその<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>プロパティです。  
  
 [!code-xaml[MasterDetailXml#HowTo1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
