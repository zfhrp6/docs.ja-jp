---
title: '方法 : バインドされたデータを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556641"
---
# <a name="how-to-convert-bound-data"></a>方法 : バインドされたデータを変換する
この例では、バインディングで使用されているデータへの変換を適用する方法を示します。  
  
 バインド中にデータを変換するを実装するクラスを作成する必要があります、<xref:System.Windows.Data.IValueConverter>インターフェイスが含まれています、<xref:System.Windows.Data.IValueConverter.Convert%2A>と<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>メソッドです。  
  
## <a name="example"></a>例  
 次の例では、年、月、および日のみが表示されるように渡された日付値に変換する日付コンバーターの実装を示します。 実装する場合、<xref:System.Windows.Data.IValueConverter>装飾を使用して実装することをお勧めは、インターフェイス、<xref:System.Windows.Data.ValueConversionAttribute>開発に示すために属性が次の例のように、変換に含まれるデータ型をツールします。  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 コンバーターを作成した後でリソースとして追加できる、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 次の例では、 *src*先の名前空間にマップ*DateConverter*が定義されています。  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後に、次の構文を使用して、バインディングでコンバーターを使用できます。 次の例では、テキストのコンテンツ、<xref:System.Windows.Controls.TextBlock>にバインドされた*StartDate*、外部データ ソースのプロパティです。  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 上記の例で参照されているスタイル リソースは、このトピックで示していないリソース セクションで定義されます。  
  
## <a name="see-also"></a>関連項目  
 [バインディングの検証の実装](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
