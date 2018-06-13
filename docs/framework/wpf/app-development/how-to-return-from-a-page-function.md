---
title: '方法 : ページ関数から戻る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- returning from page functions [WPF]
- page functions [WPF], returning from
- functions [WPF], returning from
ms.assetid: 87804905-7e8f-417b-b0e3-5622da686396
ms.openlocfilehash: 3251b373b11dc7682235251b6d82e22705456737
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545512"
---
# <a name="how-to-return-from-a-page-function"></a><span data-ttu-id="3dacd-102">方法 : ページ関数から戻る</span><span class="sxs-lookup"><span data-stu-id="3dacd-102">How to: Return from a Page Function</span></span>
<span data-ttu-id="3dacd-103">この例では、ページ関数から結果を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3dacd-103">This example shows how to return a result from a page function.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dacd-104">例</span><span class="sxs-lookup"><span data-stu-id="3dacd-104">Example</span></span>  
 <span data-ttu-id="3dacd-105">ページ関数から返すを呼び出す必要がある<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>のインスタンスを渡すと<xref:System.Windows.Navigation.ReturnEventArgs%601>です。</span><span class="sxs-lookup"><span data-stu-id="3dacd-105">To return from a page function, you need to call <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> and pass an instance of <xref:System.Windows.Navigation.ReturnEventArgs%601>.</span></span>  
  
 [!code-xaml[HOWTOPageFunctionSnippets#PageFunctionReturnAResultXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml#pagefunctionreturnaresultxaml1)]  
[!code-xaml[HOWTOPageFunctionSnippets#PageFunctionReturnAResultXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml#pagefunctionreturnaresultxaml2)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#PageFunctionReturnAResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/GetStringPageFunction.xaml.cs#pagefunctionreturnaresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#PageFunctionReturnAResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/GetStringPageFunction.xaml.vb#pagefunctionreturnaresultcodebehind)]  
  
## <a name="see-also"></a><span data-ttu-id="3dacd-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dacd-106">See Also</span></span>  
 <xref:System.Windows.Navigation.PageFunction%601>
