---
title: "方法 : グリッド間でサイズ設定プロパティを共有する"
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
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0e3be0a0b550f6fbbc9876709094d4a23abe1a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a><span data-ttu-id="a6a58-102">方法 : グリッド間でサイズ設定プロパティを共有する</span><span class="sxs-lookup"><span data-stu-id="a6a58-102">How to: Share Sizing Properties Between Grids</span></span>
<span data-ttu-id="a6a58-103">この例は、列のサイズ変更データを共有する方法について説明し、間で行<xref:System.Windows.Controls.Grid>一貫性のあるサイズ変更を保持するために要素。</span><span class="sxs-lookup"><span data-stu-id="a6a58-103">This example shows how to share the sizing data of columns and rows between <xref:System.Windows.Controls.Grid> elements in order to keep sizing consistent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6a58-104">例</span><span class="sxs-lookup"><span data-stu-id="a6a58-104">Example</span></span>  
 <span data-ttu-id="a6a58-105">次の例を紹介 2<xref:System.Windows.Controls.Grid>要素を親の子要素として<xref:System.Windows.Controls.DockPanel>です。</span><span class="sxs-lookup"><span data-stu-id="a6a58-105">The following example introduces two <xref:System.Windows.Controls.Grid> elements as child elements of a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="a6a58-106"><xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>添付プロパティの<xref:System.Windows.Controls.Grid>親で定義された<xref:System.Windows.Controls.DockPanel>です。</span><span class="sxs-lookup"><span data-stu-id="a6a58-106">The <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> attached property of <xref:System.Windows.Controls.Grid> is defined on the parent <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="a6a58-107">例では、2 つを使用して、プロパティ値を操作する<xref:System.Windows.Controls.Button>要素以外のブール型プロパティ値の各要素は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a6a58-107">The example manipulates the property value by using two <xref:System.Windows.Controls.Button> elements; each element represents one of the Boolean property values.</span></span> <span data-ttu-id="a6a58-108">ときに、<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>にプロパティの値が設定されている`true`の各列または行のメンバー、<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>行または列のコンテンツに関係なく、サイズ変更情報を共有します。</span><span class="sxs-lookup"><span data-stu-id="a6a58-108">When the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> property value is set to `true`, each column or row member of a <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> shares sizing information, regardless of the content of a row or column.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="a6a58-109">...</span><span class="sxs-lookup"><span data-stu-id="a6a58-109">...</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a6a58-110">次のコード ビハインド例は、メソッドを処理するボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="a6a58-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event raises.</span></span> <span data-ttu-id="a6a58-111">これらのメソッド呼び出しの結果を書き込む例を<xref:System.Windows.Controls.TextBlock>使用して関連する要素が文字列として新しいプロパティ値を出力する方法を取得します。</span><span class="sxs-lookup"><span data-stu-id="a6a58-111">The example writes the results of these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a6a58-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6a58-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [<span data-ttu-id="a6a58-113">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="a6a58-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
