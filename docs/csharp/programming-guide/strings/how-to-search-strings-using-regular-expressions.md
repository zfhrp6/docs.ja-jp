---
title: "方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="59e64-102">方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="59e64-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="59e64-103">文字列の検索には、<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="59e64-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="59e64-104">単純な検索から、正規表現を活用した複雑な検索まで、さまざまな検索があります。</span><span class="sxs-lookup"><span data-stu-id="59e64-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="59e64-105"><xref:System.Text.RegularExpressions.Regex> クラスを使用して文字列を検索する 2 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="59e64-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="59e64-106">詳細については、「[.NET Framework の正規表現](https://msdn.microsoft.com/library/hs600312)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59e64-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59e64-107">例</span><span class="sxs-lookup"><span data-stu-id="59e64-107">Example</span></span>  
 <span data-ttu-id="59e64-108">次のコードは、大文字と小文字を区別せずに配列の文字列を単純に検索するコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="59e64-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="59e64-109">静的メソッド <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> では、検索する文字列と、検索パターンを含む文字列を前提として、検索を実行します。</span><span class="sxs-lookup"><span data-stu-id="59e64-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="59e64-110">この場合、3 つ目の引数を使用して、大文字と小文字の区別を無視することを示します。</span><span class="sxs-lookup"><span data-stu-id="59e64-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="59e64-111">詳細については、「<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59e64-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="59e64-112">例</span><span class="sxs-lookup"><span data-stu-id="59e64-112">Example</span></span>  
 <span data-ttu-id="59e64-113">次のコードは、正規表現を使用して、配列の各文字列の形式を検証するコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="59e64-113">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="59e64-114">各文字列が電話番号の形式であることが検証されます。つまり、3 グループの数値がダッシュで区切られ、最初の 2 グループには 3 桁の数値が含まれ、3 つ目のグループには 4 桁の数値が含まれることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="59e64-114">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="59e64-115">この操作は、正規表現 `^\\d{3}-\\d{3}-\\d{4}$` を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="59e64-115">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="59e64-116">詳細については、「[正規表現言語 - クイック リファレンス](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59e64-116">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="59e64-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="59e64-117">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [<span data-ttu-id="59e64-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="59e64-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="59e64-119">文字列</span><span class="sxs-lookup"><span data-stu-id="59e64-119">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="59e64-120">.NET Framework 正規表現</span><span class="sxs-lookup"><span data-stu-id="59e64-120">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)  
 [<span data-ttu-id="59e64-121">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="59e64-121">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
