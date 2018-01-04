---
title: "方法 : 複雑なグリッドを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9dfb913407622f3cbd9a067a94cc6400b501e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="53e24-102">方法 : 複雑なグリッドを作成する</span><span class="sxs-lookup"><span data-stu-id="53e24-102">How to: Create a Complex Grid</span></span>
<span data-ttu-id="53e24-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.Grid>月間予定表のようなレイアウトを作成します。</span><span class="sxs-lookup"><span data-stu-id="53e24-103">This example shows how to use a <xref:System.Windows.Controls.Grid> to create layout that looks like a monthly calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53e24-104">例</span><span class="sxs-lookup"><span data-stu-id="53e24-104">Example</span></span>  
 <span data-ttu-id="53e24-105">次の例を使用して 8 つの行と 8 つの列の定義、<xref:System.Windows.Controls.RowDefinition>と<xref:System.Windows.Controls.ColumnDefinition>クラスです。</span><span class="sxs-lookup"><span data-stu-id="53e24-105">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="53e24-106">使用して、<xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType>と<xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType>と共にアタッチされるプロパティ、<xref:System.Windows.Shapes.Rectangle>要素で、さまざまな列と行の背景色を入力します。</span><span class="sxs-lookup"><span data-stu-id="53e24-106">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="53e24-107">この設計は、複数の要素が内の各セル内に存在できるため、可能な<xref:System.Windows.Controls.Grid>、原則違い<xref:System.Windows.Controls.Grid>と<xref:System.Windows.Documents.Table>です。</span><span class="sxs-lookup"><span data-stu-id="53e24-107">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>  
  
 <span data-ttu-id="53e24-108">例では、使用する垂直グラデーション<xref:System.Windows.Shapes.Shape.Fill%2A>ビジュアルのプレゼンテーションや予定表の読みやすさを向上するために行と列。</span><span class="sxs-lookup"><span data-stu-id="53e24-108">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows in order to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="53e24-109">スタイルの<xref:System.Windows.Controls.TextBlock>要素は、日付と曜日を表します。</span><span class="sxs-lookup"><span data-stu-id="53e24-109">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="53e24-110"><xref:System.Windows.Controls.TextBlock>要素は、セル内を使用して絶対位置、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティと、アプリケーションのスタイル内で定義されている配置プロパティです。</span><span class="sxs-lookup"><span data-stu-id="53e24-110"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="53e24-111">参照</span><span class="sxs-lookup"><span data-stu-id="53e24-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [<span data-ttu-id="53e24-112">純色およびグラデーションによる塗りつぶしの概要</span><span class="sxs-lookup"><span data-stu-id="53e24-112">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="53e24-113">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="53e24-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="53e24-114">テーブルの概要</span><span class="sxs-lookup"><span data-stu-id="53e24-114">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
