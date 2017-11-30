---
title: "カルチャを認識しない文字列操作の実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e703e9adc531b7d1695d3e9bbed61a2c0f62ad31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="dcb1c-102">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="dcb1c-102">Performing Culture-Insensitive String Operations</span></span>
<span data-ttu-id="dcb1c-103">既定ではカルチャに依存した文字列の操作を実行するほとんどの .NET Framework メソッドには、明示的に渡すことで使用するカルチャを指定することを許可するメソッド オーバー ロードが用意されて、<xref:System.Globalization.CultureInfo>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="dcb1c-104">これらのオーバーロードによって、大文字小文字のマップおよび並べ替え規則のカルチャによる違いを排除し、カルチャを認識しない結果を確保できます。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="dcb1c-105">ここでは、既定ではカルチャを認識する .NET Framework のメソッドを使用して、カルチャを認識しない文字列操作を実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcb1c-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dcb1c-106">In This Section</span></span>  
 [<span data-ttu-id="dcb1c-107">カルチャを認識しない文字列比較の実行</span><span class="sxs-lookup"><span data-stu-id="dcb1c-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="dcb1c-108">使用する方法について説明します、<xref:System.String.Compare%2A?displayProperty=nameWithType>と<xref:System.String.CompareTo%2A?displayProperty=nameWithType>カルチャを認識しない文字列比較を実行するメソッド。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="dcb1c-109">カルチャを認識しない大文字と小文字の変更の実行</span><span class="sxs-lookup"><span data-stu-id="dcb1c-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="dcb1c-110">使用する方法について説明します、 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>、 <xref:System.String.ToLower%2A?displayProperty=nameWithType>、 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>、および<xref:System.Char.ToLower%2A?displayProperty=nameWithType>カルチャに依存しないケース変更を実行するメソッド。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="dcb1c-111">カルチャを認識しないコレクションの操作の実行</span><span class="sxs-lookup"><span data-stu-id="dcb1c-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="dcb1c-112">使用する方法について説明します、 <xref:System.Collections.CaseInsensitiveComparer>、<xref:System.Collections.CaseInsensitiveHashCodeProvider>クラス、 <xref:System.Collections.SortedList>、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>と<xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>コレクションでカルチャに依存しない操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="dcb1c-113">カルチャを認識しない配列の操作の実行</span><span class="sxs-lookup"><span data-stu-id="dcb1c-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="dcb1c-114">使用する方法について説明します、<xref:System.Array.Sort%2A?displayProperty=nameWithType>と<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>配列内のカルチャに依存しない操作を実行するメソッド。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dcb1c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcb1c-115">Related Sections</span></span>  
 [<span data-ttu-id="dcb1c-116">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="dcb1c-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="dcb1c-117">文字列操作を実行する際にカルチャに注意する理由について説明し、カルチャを認識する操作を実行するときとカルチャを認識しない操作を実行するときのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="dcb1c-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>
