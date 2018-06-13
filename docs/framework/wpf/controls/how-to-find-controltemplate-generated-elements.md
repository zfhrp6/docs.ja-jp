---
title: '方法 : ControlTemplate によって生成された要素を検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 3d3032326a0cedc01b4a7ec8e6546044353d6b4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553911"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>方法 : ControlTemplate によって生成された要素を検索する
この例によって生成される要素を検索する方法を示しています、<xref:System.Windows.Controls.ControlTemplate>です。  
  
## <a name="example"></a>例  
 次の例は、単純なを作成するスタイル<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>クラス。  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 テンプレートが適用された後は、テンプレート内で要素を見つけ、呼び出すことができます、<xref:System.Windows.FrameworkTemplate.FindName%2A>のメソッド、<xref:System.Windows.Controls.Control.Template%2A>です。 次の例の実際の幅の値を示すメッセージ ボックスの作成、<xref:System.Windows.Controls.Grid>コントロール テンプレート内で。  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>関連項目  
 [DataTemplate によって生成された要素を検索する](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
