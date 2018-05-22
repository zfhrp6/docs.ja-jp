---
title: カルチャを認識しない配列の操作の実行
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4d732d64eecff72403c455c14b68c3aec1b5407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="f4cb1-102">カルチャを認識しない配列の操作の実行</span><span class="sxs-lookup"><span data-stu-id="f4cb1-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="f4cb1-103"><xref:System.Array.Sort%2A?displayProperty=nameWithType> メソッドと <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> メソッドのオーバーロードは、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> プロパティを使用して、カルチャを認識する並べ替えを既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f4cb1-104">これらのメソッドで返されたカルチャを認識した結果は、並べ替え順序の違いに起因し、カルチャによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="f4cb1-105">カルチャを認識した動作を回避するには、`comparer` パラメーターを受け入れる、このメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="f4cb1-106">`comparer` パラメーターによって、配列の要素を比較するときに使用する <xref:System.Collections.IComparer> 実装が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="f4cb1-107">このパラメーターには、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を使用するカスタム invariant comparer クラスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f4cb1-108">カスタム invariant comparer クラスの例は、「[カルチャを認識しないコレクションの操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)」トピックのサブトピック「SortedList クラスの使用」にあります。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="f4cb1-109">**注** **CultureInfo.InvariantCulture** を比較メソッドに渡すと、カルチャを認識しない比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="f4cb1-110">ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="f4cb1-111">また、比較結果に基づいたセキュリティに関する決定もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="f4cb1-112">非言語的な比較や、結果に基づくセキュリティに関する決定については、アプリケーションは <xref:System.StringComparison> 値を受け入れる比較メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="f4cb1-113">アプリケーションは <xref:System.StringComparison.Ordinal> を渡します。</span><span class="sxs-lookup"><span data-stu-id="f4cb1-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4cb1-114">参照</span><span class="sxs-lookup"><span data-stu-id="f4cb1-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="f4cb1-115">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="f4cb1-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
