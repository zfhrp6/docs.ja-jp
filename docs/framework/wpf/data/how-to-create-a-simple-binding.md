---
title: "方法 : 簡単なバインディングを作成する"
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
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a>方法 : 簡単なバインディングを作成する
この例は、単純なを作成する方法を示します<xref:System.Windows.Data.Binding>です。  
  
## <a name="example"></a>例  
 この例では必要がある、`Person`という名前の文字列プロパティを持つオブジェクト`PersonName`です。 `Person`オブジェクトがという名前空間で定義されている`SDKSample`です。  
  
 強調表示された行を含む、`<src>`次の例で要素をインスタンス化、`Person`オブジェクトを`PersonName`のプロパティの値`Joe`です。 これには、`Resources`セクションし、割り当てられている、`x:Key`です。  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 強調表示された行を含む、`<TextBlock>`要素にバインドし、<xref:System.Windows.Controls.TextBlock>コントロールを`PersonName`プロパティです。 その結果、<xref:System.Windows.Controls.TextBlock>値"Joe"とともに表示されます。  
  
## <a name="see-also"></a>参照  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
