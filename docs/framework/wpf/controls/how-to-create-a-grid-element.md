---
title: '方法 : グリッド要素を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: 9fc70b8f15c4ecb4844c9c2ff4f7eeab94e7b906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551169"
---
# <a name="how-to-create-a-grid-element"></a>方法 : グリッド要素を作成する
## <a name="example"></a>例  
 次の例は、作成しのインスタンスを使用する方法を示しています。<xref:System.Windows.Controls.Grid>いずれかを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]またはコード。 この例は、3 つ<xref:System.Windows.Controls.ColumnDefinition>オブジェクトと 3<xref:System.Windows.Controls.RowDefinition>セルするのには、9 つのグリッドを作成、ワークシートのようにオブジェクトします。 各セルには、<xref:System.Windows.Controls.TextBlock>データ、および、先頭の行を表す要素が含まれています、<xref:System.Windows.Controls.TextBlock>で、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>適用されるプロパティです。 各セルの境界線を表示するのには<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを有効にします。  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Grid>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
