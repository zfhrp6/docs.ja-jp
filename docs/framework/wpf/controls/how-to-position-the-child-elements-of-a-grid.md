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
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="26c28-102">方法 : グリッドの子要素を配置する</span><span class="sxs-lookup"><span data-stu-id="26c28-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="26c28-103">この例は、get を使用してで定義されているメソッドを設定する方法を示します<xref:System.Windows.Controls.Grid>子要素を配置します。</span><span class="sxs-lookup"><span data-stu-id="26c28-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26c28-104">例</span><span class="sxs-lookup"><span data-stu-id="26c28-104">Example</span></span>  
 <span data-ttu-id="26c28-105">次の例では、親<xref:System.Windows.Controls.Grid>要素 (`grid1`) を持つ 3 つの列と 3 つの行。</span><span class="sxs-lookup"><span data-stu-id="26c28-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="26c28-106">子<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) に追加、<xref:System.Windows.Controls.Grid>列の位置が 0、行の位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="26c28-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="26c28-107"><xref:System.Windows.Controls.Button> 要素は、位置を変更するに呼び出せるメソッドを表す、<xref:System.Windows.Shapes.Rectangle>内の要素、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="26c28-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="26c28-108">ユーザーには、ボタンがクリックすると、関連するメソッドがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="26c28-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="26c28-109">分離コード例を次のメソッドの処理をボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="26c28-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="26c28-110">例ではこれらのメソッド呼び出しを<xref:System.Windows.Controls.TextBlock>使用して関連する要素が文字列として新しいプロパティ値を出力する方法を取得します。</span><span class="sxs-lookup"><span data-stu-id="26c28-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="26c28-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="26c28-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="26c28-112">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="26c28-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
