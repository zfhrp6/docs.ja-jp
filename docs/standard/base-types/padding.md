---
title: .NET での文字列の埋め込み
ms.date: 03/15/2018
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8b71908d817625ca38f3b53a10fc20e9103ee15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="19c80-102">.NET での文字列の埋め込み</span><span class="sxs-lookup"><span data-stu-id="19c80-102">Padding Strings in .NET</span></span>

<span data-ttu-id="19c80-103">ある文字の先頭または末尾に文字を埋め込み、合計を指定の長さにするとき、元の文字列で構成される新しい文字列を次の <xref:System.String> メソッドの 1 つを利用して作成します。</span><span class="sxs-lookup"><span data-stu-id="19c80-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="19c80-104">埋め込み文字は、スペースまたは指定した文字にすることができます。</span><span class="sxs-lookup"><span data-stu-id="19c80-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="19c80-105">結果の文字列は右揃えまたは左揃えのように見えます。</span><span class="sxs-lookup"><span data-stu-id="19c80-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="19c80-106">元の文字列の長さが既に必要な合計の長さ以上である場合、埋め込みメソッドは元の文字列をそのまま返します。詳細については、<xref:System.String.PadLeft%2A?displayProperty=nameWithType> および <xref:System.String.PadRight%2A?displayProperty=nameWithType> メソッドの 2 つのオーバーロードの**戻り値**に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="19c80-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="19c80-107">メソッド名</span><span class="sxs-lookup"><span data-stu-id="19c80-107">Method name</span></span>|<span data-ttu-id="19c80-108">使用</span><span class="sxs-lookup"><span data-stu-id="19c80-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="19c80-109">文字列の先頭に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="19c80-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="19c80-110">文字列の末尾に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="19c80-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="19c80-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="19c80-111">PadLeft</span></span>  
 <span data-ttu-id="19c80-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> メソッドでは、元の文字列の先頭に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="19c80-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="19c80-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> メソッドでは、空白文字が埋め込み文字として利用されます。<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> メソッドでは、独自の埋め込み文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="19c80-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="19c80-114">次のコード例では、<xref:System.String.PadLeft%2A> メソッドを利用し、長さが 20 文字の新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="19c80-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="19c80-115">この例は、コンソールに "`--------Hello World!`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="19c80-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="19c80-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="19c80-116">PadRight</span></span>  
 <span data-ttu-id="19c80-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> メソッドでは、元の文字列の末尾に埋め込み文字をつなげ、合計を指定の長さにすることで新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="19c80-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="19c80-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> メソッドでは、空白文字が埋め込み文字として利用されます。<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> メソッドでは、独自の埋め込み文字を指定できます。</span><span class="sxs-lookup"><span data-stu-id="19c80-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="19c80-119">次のコード例では、<xref:System.String.PadRight%2A> メソッドを利用し、長さが 20 文字の新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="19c80-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="19c80-120">この例は、コンソールに "`Hello World!--------`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="19c80-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="19c80-121">参照</span><span class="sxs-lookup"><span data-stu-id="19c80-121">See Also</span></span>  
 [<span data-ttu-id="19c80-122">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="19c80-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
