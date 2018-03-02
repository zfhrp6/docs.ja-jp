---
title: ".NET での文字列の埋め込み"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea903c1f950e7c226e043c1fa7276a66126b2512
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="76ab8-102">.NET での文字列の埋め込み</span><span class="sxs-lookup"><span data-stu-id="76ab8-102">Padding Strings in .NET</span></span>
<span data-ttu-id="76ab8-103">ある文字の先頭または末尾に文字を埋め込み、合計を指定の長さにするとき、元の文字列で構成される新しい文字列を次の <xref:System.String> メソッドの 1 つを利用して作成します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="76ab8-104">埋め込み文字にはスペースや指定した文字を利用できます。結果的に、右揃えまたは左揃えのように見えます。</span><span class="sxs-lookup"><span data-stu-id="76ab8-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="76ab8-105">メソッド名</span><span class="sxs-lookup"><span data-stu-id="76ab8-105">Method name</span></span>|<span data-ttu-id="76ab8-106">使用</span><span class="sxs-lookup"><span data-stu-id="76ab8-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="76ab8-107">文字列の先頭に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="76ab8-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="76ab8-108">文字列の末尾に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="76ab8-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="76ab8-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="76ab8-109">PadLeft</span></span>  
 <span data-ttu-id="76ab8-110"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> メソッドでは、元の文字列の先頭に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="76ab8-111"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> メソッドでは、空白文字が埋め込み文字として利用されます。<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> メソッドでは、独自の埋め込み文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="76ab8-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="76ab8-112">次のコード例では、<xref:System.String.PadLeft%2A> メソッドを利用し、長さが 20 文字の新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="76ab8-113">この例は、コンソールに "`--------Hello World!`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="76ab8-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="76ab8-114">PadRight</span></span>  
 <span data-ttu-id="76ab8-115"><xref:System.String.PadRight%2A?displayProperty=nameWithType> メソッドでは、元の文字列の末尾に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="76ab8-116"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> メソッドでは、空白文字が埋め込み文字として利用されます。<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> メソッドでは、独自の埋め込み文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="76ab8-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="76ab8-117">次のコード例では、<xref:System.String.PadRight%2A> メソッドを利用し、長さが 20 文字の新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="76ab8-118">この例は、コンソールに "`Hello World!--------`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="76ab8-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="76ab8-119">参照</span><span class="sxs-lookup"><span data-stu-id="76ab8-119">See Also</span></span>  
 [<span data-ttu-id="76ab8-120">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="76ab8-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
