---
title: "方法 : 要素からすべての装飾を削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f7bb16c2cd641579706609ff14ca16cc57bd620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a><span data-ttu-id="4a37f-102">方法 : 要素からすべての装飾を削除する</span><span class="sxs-lookup"><span data-stu-id="4a37f-102">How to: Remove all Adorners from an Element</span></span>
<span data-ttu-id="4a37f-103">この例は、プログラムから、指定したすべての装飾を削除する方法を示しています。<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="4a37f-103">This example shows how to programmatically remove all adorners from a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a37f-104">例</span><span class="sxs-lookup"><span data-stu-id="4a37f-104">Example</span></span>  
 <span data-ttu-id="4a37f-105">この詳細なコード例はすべての装飾によって返される装飾の配列に<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>です。</span><span class="sxs-lookup"><span data-stu-id="4a37f-105">This verbose code example removes all of the adorners in the array of adorners returned by <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.</span></span>  <span data-ttu-id="4a37f-106">この例の発生時に装飾を取得する、<xref:System.Windows.UIElement>という*myTextBox*です。</span><span class="sxs-lookup"><span data-stu-id="4a37f-106">This example happens to retrieve the adorners on a <xref:System.Windows.UIElement> named *myTextBox*.</span></span>  <span data-ttu-id="4a37f-107">呼び出しで、要素が指定されている場合<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>、装飾を持たない`null`が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a37f-107">If the element specified in the call to <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> has no adorners, `null` is returned.</span></span>  <span data-ttu-id="4a37f-108">このコードは明示的に null 配列をチェックしが、null 配列は比較的一般的である必要なアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="4a37f-108">This code explicitly checks for a null array, and is best suited for applications where a null array is expected to be relatively common.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a><span data-ttu-id="4a37f-109">例</span><span class="sxs-lookup"><span data-stu-id="4a37f-109">Example</span></span>  
 <span data-ttu-id="4a37f-110">この圧縮されたコード例は、機能的には、上記の詳細な例です。</span><span class="sxs-lookup"><span data-stu-id="4a37f-110">This condensed code example is functionally equivalent to the verbose example shown above.</span></span> <span data-ttu-id="4a37f-111">このコードに明示的に確認しません null 配列の場合は、可能であればを<xref:System.NullReferenceException>例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4a37f-111">This code does not explicitly check for a null array, so it is possible that a <xref:System.NullReferenceException> exception may be raised.</span></span>  <span data-ttu-id="4a37f-112">このコードが、null 配列はまれである必要なアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="4a37f-112">This code is best suited for applications where a null array is expected to be rare.</span></span>  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a><span data-ttu-id="4a37f-113">参照</span><span class="sxs-lookup"><span data-stu-id="4a37f-113">See Also</span></span>  
 [<span data-ttu-id="4a37f-114">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="4a37f-114">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
