---
title: "方法 : バインドされた項目の一覧に基づいて値を生成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3987690a1acb180ee22fa02e399accd9c5d481d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>方法 : バインドされた項目の一覧に基づいて値を生成する
<xref:System.Windows.Data.MultiBinding>使用すると、ソースのプロパティの一覧にバインディング ターゲット プロパティをバインドし、指定された入力の値を生成するロジックを適用できます。 この例は、使用する方法を示します<xref:System.Windows.Data.MultiBinding>です。  
  
## <a name="example"></a>例  
 次の例では、`NameListData` は、`PersonName` オブジェクトのコレクションを参照します。このオブジェクトは、`firstName` と `lastName` の 2 つのプロパティを含みます。 次のコード生成、<xref:System.Windows.Controls.TextBlock>最後の名前を持つ人物の姓と名の先頭を示すです。  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 姓が先の形式を生成する方法を理解するには、次に示す `NameConverter` の実装をご覧ください。  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` は、<xref:System.Windows.Data.IMultiValueConverter> インターフェイスを実装します。 `NameConverter` は、個々のバインディングから値を受け取り、それらを値のオブジェクト配列に格納します。 順序、<xref:System.Windows.Data.Binding>下にある要素が表示されます、<xref:System.Windows.Data.MultiBinding>要素は、それらの値が配列に格納されている順序。 値、<xref:System.Windows.Data.MultiBinding.ConverterParameter%2A>属性がのパラメーターの引数によって参照される、<xref:System.Windows.Data.MultiBinding.Converter%2A>メソッドで、名前を書式設定する方法を決定するパラメーターの切り替えを実行します。  
  
## <a name="see-also"></a>参照  
 [バインドされたデータを変換する](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
