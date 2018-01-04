---
title: "方法 : プログラムでテキストに要素を挿入する"
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
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b200489c4b7fb06f2eb98c0ec9c84da42f18a395
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="28968-102">方法 : プログラムでテキストに要素を挿入する</span><span class="sxs-lookup"><span data-stu-id="28968-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="28968-103">次の例は、2 つを使用する方法を示しています。<xref:System.Windows.Documents.TextPointer>を適用するテキスト内での範囲を指定するオブジェクト、<xref:System.Windows.Documents.Span>する要素。</span><span class="sxs-lookup"><span data-stu-id="28968-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28968-104">例</span><span class="sxs-lookup"><span data-stu-id="28968-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="28968-105">次の図は、この例の結果を示したものです。</span><span class="sxs-lookup"><span data-stu-id="28968-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="28968-106">![テキストの範囲に適用される Span 要素](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="28968-106">![A Span element applied to a range of text](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28968-107">参照</span><span class="sxs-lookup"><span data-stu-id="28968-107">See Also</span></span>  
 [<span data-ttu-id="28968-108">フロー ドキュメントの概要</span><span class="sxs-lookup"><span data-stu-id="28968-108">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
