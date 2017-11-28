---
title: "方法 : LINQ クエリの結果にバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e77a0c698dae0330877c54422c15e14c82376891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>方法 : LINQ クエリの結果にバインドする
この例では、LINQ クエリを実行し、結果にバインドする方法を示します。  
  
## <a name="example"></a>例  
 次の例では、次の 2 つのリスト ボックスを作成します。 最初のリスト ボックスには、次の 3 つのリスト項目が含まれています。  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 最初のリスト ボックスから項目を選択すると、次のイベント ハンドラーを呼び出します。 この例では`Tasks`のコレクションは、`Task`オブジェクト。 `Task`クラスという名前のプロパティには`Priority`します。 このイベント ハンドラーのコレクションを返す LINQ クエリを実行する`Task`オブジェクトを選択した優先度値を持ち、として設定し、 <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 に、2 番目のリスト ボックスがそのコレクションにバインドその<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>に値が設定されている`{Binding}`です。 その結果、返されるコレクションが表示されます (に基づいて、 `myTaskTemplate` <xref:System.Windows.DataTemplate>)。  
  
## <a name="see-also"></a>関連項目  
 [XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [コレクションにバインドして選択に基づく情報を表示する](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [WPF Version 4.5 の新機能](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
