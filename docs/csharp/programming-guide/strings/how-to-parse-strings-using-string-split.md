---
title: "方法: String.Split を使用して文字列を解析する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: 17
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
ms.sourcegitcommit: d74c1d0760d4e776c2cf4c7dea1dac060c85a83c
ms.openlocfilehash: e25dbf6b86c82808622377c0618cd956541c6e09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="46795-102">方法: String.Split を使用して文字列を解析する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="46795-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="46795-103"><xref:System.String.Split%2A?displayProperty=fullName> メソッドを使用して文字列を解析する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="46795-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="46795-104">入力として、 <xref:System.String.Split%2A> は、ターゲット文字列から対象の部分文字列を区切る文字を示す文字配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="46795-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="46795-105">関数は、部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="46795-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="46795-106">この例ではスペース、コンマ、ピリオド、コロン、およびタブを使用しています。すべて、これらの区切り文字を格納した配列で <xref:System.String.Split%2A>に渡されます。</span><span class="sxs-lookup"><span data-stu-id="46795-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="46795-107">ターゲット文字列の文に含まれている各単語は、結果の文字列の配列とは別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="46795-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46795-108">例</span><span class="sxs-lookup"><span data-stu-id="46795-108">Example</span></span>  
 <span data-ttu-id="46795-109">[!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="46795-109">[!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="46795-110">例</span><span class="sxs-lookup"><span data-stu-id="46795-110">Example</span></span>  
 <span data-ttu-id="46795-111">既定では、対象の文字列内に区切り文字が 2 つ連続して現れた場合、String.Split は空の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="46795-111">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="46795-112">オプションの StringSplitOptions.RemoveEmptyEntries パラメーターを渡すと、出力から空の文字列を除外することができます。</span><span class="sxs-lookup"><span data-stu-id="46795-112">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="46795-113">String.Split は、文字列の配列 (1 つの文字ではなく、対象の文字列を解析するための区切り記号として機能する文字シーケンス) を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="46795-113">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="46795-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="46795-114">See Also</span></span>  
 <span data-ttu-id="46795-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="46795-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="46795-116">[文字列](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="46795-116">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 [<span data-ttu-id="46795-117">.NET Framework 正規表現</span><span class="sxs-lookup"><span data-stu-id="46795-117">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)

