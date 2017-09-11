---
title: "方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fb05d1702c75be8fd224ee0f34d7d8d3fe71f207
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="9a69d-102">方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9a69d-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="9a69d-103">文字列の検索には、<xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a69d-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> class can be used to search strings.</span></span> <span data-ttu-id="9a69d-104">単純な検索から、正規表現を活用した複雑な検索まで、さまざまな検索があります。</span><span class="sxs-lookup"><span data-stu-id="9a69d-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="9a69d-105"><xref:System.Text.RegularExpressions.Regex> クラスを使用して文字列を検索する 2 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9a69d-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="9a69d-106">詳細については、「[.NET Framework の正規表現](https://msdn.microsoft.com/library/hs600312)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a69d-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a69d-107">例</span><span class="sxs-lookup"><span data-stu-id="9a69d-107">Example</span></span>  
 <span data-ttu-id="9a69d-108">次のコードは、大文字と小文字を区別せずに配列の文字列を単純に検索するコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9a69d-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="9a69d-109">静的メソッド <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> では、検索する文字列と、検索パターンを含む文字列を前提として、検索を実行します。</span><span class="sxs-lookup"><span data-stu-id="9a69d-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="9a69d-110">この場合、3 つ目の引数を使用して、大文字と小文字の区別を無視することを示します。</span><span class="sxs-lookup"><span data-stu-id="9a69d-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="9a69d-111">詳細については、「<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a69d-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="9a69d-112">[!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a69d-112">[!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a69d-113">例</span><span class="sxs-lookup"><span data-stu-id="9a69d-113">Example</span></span>  
 <span data-ttu-id="9a69d-114">次のコードは、正規表現を使用して、配列の各文字列の形式を検証するコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9a69d-114">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="9a69d-115">各文字列が電話番号の形式であることが検証されます。つまり、3 グループの数値がダッシュで区切られ、最初の 2 グループには 3 桁の数値が含まれ、3 つ目のグループには 4 桁の数値が含まれることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="9a69d-115">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="9a69d-116">この操作は、正規表現 `^\\d{3}-\\d{3}-\\d{4}$` を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="9a69d-116">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="9a69d-117">詳細については、「[正規表現言語 - クイック リファレンス](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9a69d-117">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 <span data-ttu-id="9a69d-118">[!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a69d-118">[!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a69d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a69d-119">See Also</span></span>  
 <span data-ttu-id="9a69d-120"><xref:System.Text.RegularExpressions.Regex?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9a69d-120"><xref:System.Text.RegularExpressions.Regex?displayProperty=fullName></span></span>   
 <span data-ttu-id="9a69d-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a69d-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9a69d-122">[文字列](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a69d-122">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="9a69d-123">[.NET Framework 正規表現](https://msdn.microsoft.com/library/hs600312) </span><span class="sxs-lookup"><span data-stu-id="9a69d-123">[.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312) </span></span>  
 [<span data-ttu-id="9a69d-124">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="9a69d-124">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)

