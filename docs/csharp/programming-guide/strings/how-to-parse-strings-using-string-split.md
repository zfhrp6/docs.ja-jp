---
title: "方法: String.Split を使用して文字列を解析する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="f232b-102">方法: String.Split を使用して文字列を解析する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f232b-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="f232b-103"><xref:System.String.Split%2A?displayProperty=nameWithType> メソッドを使用して文字列を解析する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="f232b-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f232b-104">入力として、 <xref:System.String.Split%2A> は、ターゲット文字列から対象の部分文字列を区切る文字を示す文字配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f232b-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="f232b-105">関数は、部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="f232b-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="f232b-106">この例ではスペース、コンマ、ピリオド、コロン、およびタブを使用しています。すべて、これらの区切り文字を格納した配列で <xref:System.String.Split%2A>に渡されます。</span><span class="sxs-lookup"><span data-stu-id="f232b-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="f232b-107">ターゲット文字列の文に含まれている各単語は、結果の文字列の配列とは別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f232b-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f232b-108">例</span><span class="sxs-lookup"><span data-stu-id="f232b-108">Example</span></span>  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f232b-109">例</span><span class="sxs-lookup"><span data-stu-id="f232b-109">Example</span></span>  
 <span data-ttu-id="f232b-110">既定では、対象の文字列内に区切り文字が 2 つ連続して現れた場合、String.Split は空の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="f232b-110">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="f232b-111">オプションの StringSplitOptions.RemoveEmptyEntries パラメーターを渡すと、出力から空の文字列を除外することができます。</span><span class="sxs-lookup"><span data-stu-id="f232b-111">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="f232b-112">String.Split は、文字列の配列 (1 つの文字ではなく、対象の文字列を解析するための区切り記号として機能する文字シーケンス) を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="f232b-112">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f232b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f232b-113">See Also</span></span>  
 [<span data-ttu-id="f232b-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f232b-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f232b-115">文字列</span><span class="sxs-lookup"><span data-stu-id="f232b-115">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="f232b-116">.NET Framework 正規表現</span><span class="sxs-lookup"><span data-stu-id="f232b-116">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)
