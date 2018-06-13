---
title: '方法 : IScrollInfo インターフェイスを使用してコンテンツをスクロールする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 8154a626c6bf48a59be0540f857c0c51d59a26c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552884"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>方法 : IScrollInfo インターフェイスを使用してコンテンツをスクロールする
この例を使用してコンテンツをスクロールする方法を示しています、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスです。  
  
## <a name="example"></a>例  
 次の例では、機能、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスです。 例は、作成、<xref:System.Windows.Controls.StackPanel>内の要素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、親の入れ子になっている<xref:System.Windows.Controls.ScrollViewer>です。 子要素、<xref:System.Windows.Controls.StackPanel>によって定義されたメソッドを使用して、論理的にスクロールできる、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスとのインスタンスへのキャスト<xref:System.Windows.Controls.StackPanel>(`sp1`) のコードにします。  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 各<xref:System.Windows.Controls.Button>で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルでスクロール動作を制御する、関連付けられたカスタム メソッドをトリガーする<xref:System.Windows.Controls.StackPanel>です。 次の例を使用する方法を示しています、<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>と<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>メソッドです。 一般的にも配置のすべてのメソッドを使用する方法を示していますを、<xref:System.Windows.Controls.Primitives.IScrollInfo>クラスを定義します。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [ScrollViewer の概要](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
