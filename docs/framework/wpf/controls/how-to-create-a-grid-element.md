---
title: "方法 : グリッド要素を作成する"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="f4927-102">方法 : グリッド要素を作成する</span><span class="sxs-lookup"><span data-stu-id="f4927-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="f4927-103">例</span><span class="sxs-lookup"><span data-stu-id="f4927-103">Example</span></span>  
 <span data-ttu-id="f4927-104">次の例は、作成しのインスタンスを使用する方法を示しています。<xref:System.Windows.Controls.Grid>いずれかを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]またはコード。</span><span class="sxs-lookup"><span data-stu-id="f4927-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="f4927-105">この例は、3 つ<xref:System.Windows.Controls.ColumnDefinition>オブジェクトと 3<xref:System.Windows.Controls.RowDefinition>セルするのには、9 つのグリッドを作成、ワークシートのようにオブジェクトします。</span><span class="sxs-lookup"><span data-stu-id="f4927-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="f4927-106">各セルには、<xref:System.Windows.Controls.TextBlock>データ、および、先頭の行を表す要素が含まれています、<xref:System.Windows.Controls.TextBlock>で、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>適用されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="f4927-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="f4927-107">各セルの境界線を表示するのには<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f4927-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f4927-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4927-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="f4927-109">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="f4927-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
