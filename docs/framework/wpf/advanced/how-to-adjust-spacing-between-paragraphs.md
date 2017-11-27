---
title: "方法 : 段落間の間隔を調整する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1936426b44ed667d03e4881e66a081d5097a2880
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="bd69c-102">方法 : 段落間の間隔を調整する</span><span class="sxs-lookup"><span data-stu-id="bd69c-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="bd69c-103">この例では、調整またはフロー コンテンツ内の段落の間隔を排除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd69c-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="bd69c-104">フロー コンテンツの段落の間に表示される余分なスペースは余白の段落に設定の結果したがって、段落の間隔は、それらの段落の余白を調整することによって制御できます。</span><span class="sxs-lookup"><span data-stu-id="bd69c-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="bd69c-105">2 つの段落の余分なスペースを完全になくすため、設定には、段落の余白**0**します。</span><span class="sxs-lookup"><span data-stu-id="bd69c-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="bd69c-106">段落全体を通じて等間隔に整列を実現するために<xref:System.Windows.Documents.FlowDocument>のすべての段落の統一された余白の値を設定するスタイルを使用して、<xref:System.Windows.Documents.FlowDocument>です。</span><span class="sxs-lookup"><span data-stu-id="bd69c-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="bd69c-107">ことが重要に、2 つの余白のうち大きい方ではなくを 2 倍になり、2 つの隣接する段落の余白は「折りたたま」に注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd69c-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="bd69c-108">したがって、隣接する 2 つの段落では、それぞれ 20 ピクセルと 40 ピクセルの余白がある、段落の間の結果として得られる領域は 40 (ピクセル単位)、2 つの余白の値のうち、大きい方です。</span><span class="sxs-lookup"><span data-stu-id="bd69c-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd69c-109">例</span><span class="sxs-lookup"><span data-stu-id="bd69c-109">Example</span></span>  
 <span data-ttu-id="bd69c-110">次の例は、すべての余白を設定するスタイルをで<xref:System.Windows.Documents.Paragraph>内の要素、<xref:System.Windows.Documents.FlowDocument>に**0**、内の段落の間で余分なスペースが実質的に、<xref:System.Windows.Documents.FlowDocument>です。</span><span class="sxs-lookup"><span data-stu-id="bd69c-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
