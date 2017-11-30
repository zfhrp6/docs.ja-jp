---
title: "カルチャを認識しない配列の操作の実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="3166a-102">カルチャを認識しない配列の操作の実行</span><span class="sxs-lookup"><span data-stu-id="3166a-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="3166a-103">オーバー ロードが、<xref:System.Array.Sort%2A?displayProperty=nameWithType>と<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>メソッドは、既定値を使用してカルチャに依存した並べ替えを実行、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3166a-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3166a-104">これらのメソッドによって返されるカルチャに依存した結果は、並べ替え順序の違いによりカルチャごとに異なることができます。</span><span class="sxs-lookup"><span data-stu-id="3166a-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="3166a-105">カルチャに依存した動作を回避するを受け取るこのメソッドのオーバー ロードのいずれかの操作を使用して、`comparer`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="3166a-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="3166a-106">`comparer`パラメーターを指定します、<xref:System.Collections.IComparer>配列内の要素を比較するときに使用する実装。</span><span class="sxs-lookup"><span data-stu-id="3166a-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="3166a-107">パラメーターには、指定を使用してカスタムのロケールに依存しない比較演算子クラス<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="3166a-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3166a-108">「SortedList クラスを使用して、」サブトピックでカスタム ロケールに依存しない比較子クラスの例が提供される、[コレクション内のカルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="3166a-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="3166a-109">**注**渡す**CultureInfo.InvariantCulture**を比較するメソッドは、カルチャに依存しない比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="3166a-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="3166a-110">ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。</span><span class="sxs-lookup"><span data-stu-id="3166a-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="3166a-111">また、比較結果に基づいたセキュリティに関する決定もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3166a-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="3166a-112">非言語的な比較または結果ベースのセキュリティを決定するためのサポートは、アプリケーション メソッドを使用して、比較を受け付ける、<xref:System.StringComparison>値。</span><span class="sxs-lookup"><span data-stu-id="3166a-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="3166a-113">アプリケーションに渡す必要があります、<xref:System.StringComparison.Ordinal>です。</span><span class="sxs-lookup"><span data-stu-id="3166a-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3166a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3166a-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="3166a-115">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="3166a-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
