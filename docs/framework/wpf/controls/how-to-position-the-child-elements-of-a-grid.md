---
title: "方法 : グリッドの子要素を配置する"
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
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ca385e1aee10fb10ac3e912999aec3a11d03ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="fcd93-102">方法 : グリッドの子要素を配置する</span><span class="sxs-lookup"><span data-stu-id="fcd93-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="fcd93-103">この例は、get を使用してで定義されているメソッドを設定する方法を示します<xref:System.Windows.Controls.Grid>子要素を配置します。</span><span class="sxs-lookup"><span data-stu-id="fcd93-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcd93-104">例</span><span class="sxs-lookup"><span data-stu-id="fcd93-104">Example</span></span>  
 <span data-ttu-id="fcd93-105">次の例では、親<xref:System.Windows.Controls.Grid>要素 (`grid1`) を持つ 3 つの列と 3 つの行。</span><span class="sxs-lookup"><span data-stu-id="fcd93-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="fcd93-106">子<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) に追加、<xref:System.Windows.Controls.Grid>列の位置が 0、行の位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="fcd93-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="fcd93-107"><xref:System.Windows.Controls.Button>要素は、位置を変更するに呼び出せるメソッドを表す、<xref:System.Windows.Shapes.Rectangle>内の要素、<xref:System.Windows.Controls.Grid>です。</span><span class="sxs-lookup"><span data-stu-id="fcd93-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="fcd93-108">ユーザーには、ボタンがクリックすると、関連するメソッドがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="fcd93-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="fcd93-109">分離コード例を次のメソッドの処理をボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="fcd93-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="fcd93-110">例ではこれらのメソッド呼び出しを<xref:System.Windows.Controls.TextBlock>使用して関連する要素が文字列として新しいプロパティ値を出力する方法を取得します。</span><span class="sxs-lookup"><span data-stu-id="fcd93-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fcd93-111">参照</span><span class="sxs-lookup"><span data-stu-id="fcd93-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="fcd93-112">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="fcd93-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
