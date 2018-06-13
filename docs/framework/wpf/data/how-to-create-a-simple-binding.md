---
title: '方法 : 簡単なバインディングを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555020"
---
# <a name="how-to-create-a-simple-binding"></a>方法 : 簡単なバインディングを作成する
この例は、単純なを作成する方法を示します<xref:System.Windows.Data.Binding>です。  
  
## <a name="example"></a>例  
 この例では必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。 `Person`オブジェクトがという名前空間で定義されている`SDKSample`です。  
  
 強調表示された行を含む、`<src>`次の例で要素をインスタンス化、`Person`オブジェクトを`PersonName`のプロパティの値`Joe`です。 これには、`Resources`セクションし、割り当てられている、`x:Key`です。  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 強調表示された行を含む、`<TextBlock>`要素にバインドし、<xref:System.Windows.Controls.TextBlock>コントロールを`PersonName`プロパティです。 その結果、<xref:System.Windows.Controls.TextBlock>値"Joe"とともに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
