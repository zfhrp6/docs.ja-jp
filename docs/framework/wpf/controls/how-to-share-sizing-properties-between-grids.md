---
title: '方法 : グリッド間でサイズ設定プロパティを共有する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: a85c0c36ef99e6501afddaca7f26acd2928da1ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550866"
---
# <a name="how-to-share-sizing-properties-between-grids"></a>方法 : グリッド間でサイズ設定プロパティを共有する
この例は、列のサイズ変更データを共有する方法について説明し、間で行<xref:System.Windows.Controls.Grid>一貫性のあるサイズ変更を保持するために要素。  
  
## <a name="example"></a>例  
 次の例を紹介 2<xref:System.Windows.Controls.Grid>要素を親の子要素として<xref:System.Windows.Controls.DockPanel>です。 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>添付プロパティの<xref:System.Windows.Controls.Grid>親で定義された<xref:System.Windows.Controls.DockPanel>です。  
  
 例では、2 つを使用して、プロパティ値を操作する<xref:System.Windows.Controls.Button>要素以外のブール型プロパティ値の各要素は 1 つです。 ときに、<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>にプロパティの値が設定されている`true`の各列または行のメンバー、<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>行または列のコンテンツに関係なく、サイズ変更情報を共有します。  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 次のコード ビハインド例は、メソッドを処理するボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを発生させます。 これらのメソッド呼び出しの結果を書き込む例を<xref:System.Windows.Controls.TextBlock>使用して関連する要素が文字列として新しいプロパティ値を出力する方法を取得します。  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
