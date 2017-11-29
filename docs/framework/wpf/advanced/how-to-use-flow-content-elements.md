---
title: "方法: フロー コンテンツ要素を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1350a380e97631ac290e57de64fec696535fecc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="7205e-102">方法: フロー コンテンツ要素を使用する</span><span class="sxs-lookup"><span data-stu-id="7205e-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="7205e-103">次の例では、さまざまなフロー コンテンツ要素および関連付けられた属性の宣言型の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7205e-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="7205e-104">例で使用される要素および属性には、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7205e-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="7205e-105"><xref:System.Windows.Documents.Bold> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="7205e-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> 属性</span><span class="sxs-lookup"><span data-stu-id="7205e-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="7205e-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> 属性</span><span class="sxs-lookup"><span data-stu-id="7205e-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="7205e-108"><xref:System.Windows.Documents.Italic> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="7205e-109"><xref:System.Windows.Documents.LineBreak> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="7205e-110"><xref:System.Windows.Documents.List> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="7205e-111"><xref:System.Windows.Documents.ListItem> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="7205e-112"><xref:System.Windows.Documents.Paragraph> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="7205e-113"><xref:System.Windows.Documents.Run> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="7205e-114"><xref:System.Windows.Documents.Section> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="7205e-115"><xref:System.Windows.Documents.Span> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="7205e-116"><xref:System.Windows.Documents.Typography.Variants%2A>属性 (上付き文字と下付き文字)</span><span class="sxs-lookup"><span data-stu-id="7205e-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="7205e-117"><xref:System.Windows.Documents.Underline> 要素</span><span class="sxs-lookup"><span data-stu-id="7205e-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="7205e-118">例</span><span class="sxs-lookup"><span data-stu-id="7205e-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
