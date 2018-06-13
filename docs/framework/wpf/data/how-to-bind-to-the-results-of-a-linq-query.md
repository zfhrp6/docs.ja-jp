---
title: '方法 : LINQ クエリの結果にバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d374bb69b6b7e022497403b9591b27e9ad7e2395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554994"
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
