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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="7e80b-102">.NET での文字列の埋め込み</span><span class="sxs-lookup"><span data-stu-id="7e80b-102">Padding Strings in .NET</span></span>
<span data-ttu-id="7e80b-103">次のいずれかを使用して<xref:System.String>先頭または末尾に指定された合計の長さを文字で埋められますが、元の文字列で構成される新しい文字列を作成するメソッド。</span><span class="sxs-lookup"><span data-stu-id="7e80b-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="7e80b-104">埋め込み文字にはスペースや指定した文字を利用できます。結果的に、右揃えまたは左揃えのように見えます。</span><span class="sxs-lookup"><span data-stu-id="7e80b-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="7e80b-105">メソッド名</span><span class="sxs-lookup"><span data-stu-id="7e80b-105">Method name</span></span>|<span data-ttu-id="7e80b-106">用途</span><span class="sxs-lookup"><span data-stu-id="7e80b-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="7e80b-107">文字列の先頭に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="7e80b-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="7e80b-108">文字列の末尾に文字を埋め込み、合計を指定の長さにします。</span><span class="sxs-lookup"><span data-stu-id="7e80b-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="7e80b-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="7e80b-109">PadLeft</span></span>  
 <span data-ttu-id="7e80b-110"><xref:System.String.PadLeft%2A?displayProperty=nameWithType>メソッドは、指定された合計の長さを実現するために、元の文字列に先行するための十分な埋め込み文字を連結して新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e80b-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="7e80b-111"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>メソッドは、埋め込み文字として空白文字を使用し、<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>メソッドでは、独自の埋め込み文字を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7e80b-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="7e80b-112">次のコード例では、 <xref:System.String.PadLeft%2A> 20 文字である新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e80b-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="7e80b-113">この例は、コンソールに "`--------Hello World!`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="7e80b-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="7e80b-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="7e80b-114">PadRight</span></span>  
 <span data-ttu-id="7e80b-115"><xref:System.String.PadRight%2A?displayProperty=nameWithType>メソッドは、指定された合計の長さを実現するために、元の文字列に十分な末尾の埋め込み文字を連結して新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e80b-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="7e80b-116"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>メソッドは、埋め込み文字として空白文字を使用し、<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>メソッドでは、独自の埋め込み文字を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7e80b-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="7e80b-117">次のコード例では、 <xref:System.String.PadRight%2A> 20 文字である新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e80b-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="7e80b-118">この例は、コンソールに "`Hello World!--------`" と出力します。</span><span class="sxs-lookup"><span data-stu-id="7e80b-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7e80b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e80b-119">See Also</span></span>  
 [<span data-ttu-id="7e80b-120">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="7e80b-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
