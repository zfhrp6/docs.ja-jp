---
title: '方法 : グリッドの子要素を配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 62508deee1b10b4a1287360f971b3699e57d4243
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552150"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>方法 : グリッドの子要素を配置する
この例は、get を使用してで定義されているメソッドを設定する方法を示します<xref:System.Windows.Controls.Grid>子要素を配置します。  
  
## <a name="example"></a>例  
 次の例では、親<xref:System.Windows.Controls.Grid>要素 (`grid1`) を持つ 3 つの列と 3 つの行。 子<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) に追加、<xref:System.Windows.Controls.Grid>列の位置が 0、行の位置は 0 です。 <xref:System.Windows.Controls.Button> 要素は、位置を変更するに呼び出せるメソッドを表す、<xref:System.Windows.Shapes.Rectangle>内の要素、<xref:System.Windows.Controls.Grid>です。 ユーザーには、ボタンがクリックすると、関連するメソッドがアクティブになります。  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 分離コード例を次のメソッドの処理をボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生します。 例ではこれらのメソッド呼び出しを<xref:System.Windows.Controls.TextBlock>使用して関連する要素が文字列として新しいプロパティ値を出力する方法を取得します。  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Grid>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
