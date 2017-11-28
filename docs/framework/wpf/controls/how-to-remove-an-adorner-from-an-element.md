---
title: "方法 : 要素から装飾を削除する"
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
helpviewer_keywords: adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe11dc8df1a29518ba05792877bd26670f96b29d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a><span data-ttu-id="28c8e-102">方法 : 要素から装飾を削除する</span><span class="sxs-lookup"><span data-stu-id="28c8e-102">How to: Remove an Adorner from an Element</span></span>
<span data-ttu-id="28c8e-103">この例は、プログラムから、指定した特定のガイドを削除する方法を示しています。<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="28c8e-103">This example shows how to programmatically remove a specific adorner from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28c8e-104">例</span><span class="sxs-lookup"><span data-stu-id="28c8e-104">Example</span></span>  
 <span data-ttu-id="28c8e-105">この詳細なコード例では、最初のガイドを削除によって返される装飾の配列に<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>です。</span><span class="sxs-lookup"><span data-stu-id="28c8e-105">This verbose code example removes the first adorner in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="28c8e-106">この例の発生時に装飾を取得する、<xref:System.Windows.UIElement>という*myTextBox*です。</span><span class="sxs-lookup"><span data-stu-id="28c8e-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="28c8e-107">呼び出しで、要素が指定されている場合<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>、装飾を持たない`null`が返されます。</span><span class="sxs-lookup"><span data-stu-id="28c8e-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="28c8e-108">このコードは明示的に null 配列をチェックしが、null 配列は比較的一般的である必要なアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="28c8e-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a><span data-ttu-id="28c8e-109">例</span><span class="sxs-lookup"><span data-stu-id="28c8e-109">Example</span></span>  
 <span data-ttu-id="28c8e-110">この圧縮されたコード例は、機能的には、上記の詳細な例です。</span><span class="sxs-lookup"><span data-stu-id="28c8e-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="28c8e-111">このコードに明示的に確認しません null 配列の場合は、可能であればを<xref:System.NullReferenceException>例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28c8e-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="28c8e-112">このコードが、null 配列はまれである必要なアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="28c8e-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a><span data-ttu-id="28c8e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="28c8e-113">See Also</span></span>  
 [<span data-ttu-id="28c8e-114">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="28c8e-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
