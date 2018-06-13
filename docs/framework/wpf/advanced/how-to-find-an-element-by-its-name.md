---
title: '方法 : 要素を名前で検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: e2d176c9334c0a1d4c10819e0dc9f2c408e41d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543577"
---
# <a name="how-to-find-an-element-by-its-name"></a>方法 : 要素を名前で検索する
この例を使用する方法を説明する、<xref:System.Windows.FrameworkElement.FindName%2A>要素を検索する方法、<xref:System.Windows.FrameworkElement.Name%2A>値。  
  
## <a name="example"></a>例  
 この例では、名前を使用して、特定の要素を検索するメソッドは、ボタンのイベント ハンドラーとして書き込まれます。 `stackPanel` <xref:System.Windows.FrameworkElement.Name%2A>ルートの<xref:System.Windows.FrameworkElement>検索対象を示し、メソッドの例、視覚的に、検出された要素をキャストしてとして<xref:System.Windows.Controls.TextBlock>のいずれかを変更して、<xref:System.Windows.Controls.TextBlock>表示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]プロパティです。  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
