---
title: "方法 : CompositeCollection を実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b33e3a61b91c2f9e2362a270216038d61770b815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-compositecollection"></a>方法 : CompositeCollection を実装する
## <a name="example"></a>例  
 次の例として、1 つのリストを使用して複数のコレクションと、項目を表示する方法を示しています、<xref:System.Windows.Data.CompositeCollection>クラスです。 この例では`GreekGods`は、<xref:System.Collections.ObjectModel.ObservableCollection%601>の`GreekGod`カスタム オブジェクト。 データ テンプレートが定義されているように`GreekGod`オブジェクトおよび`GreekHero`オブジェクトはそれぞれ、gold およびシアン前景の色で表示されます。  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
