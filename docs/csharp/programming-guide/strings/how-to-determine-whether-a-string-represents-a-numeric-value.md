---
title: "方法: 文字列が数値を表しているかどうかを確認する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2f89f4a4771625389a04f5c92829c91d66eb207
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="3adac-102">方法: 文字列が数値を表しているかどうかを確認する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3adac-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="3adac-103">文字列が指定された数値型の有効な表現であるかどうかを確認するには、静的 `TryParse` メソッドを使用します。このメソッドには、すべてのプリミティブ数値型が実装されており、また <xref:System.DateTime>、<xref:System.Net.IPAddress> などの型も実装されています。</span><span class="sxs-lookup"><span data-stu-id="3adac-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="3adac-104">次の例では、"108" が有効な [int](../../../csharp/language-reference/keywords/int.md) かどうかを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3adac-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="3adac-105">文字列が数値以外の文字、または指定した型で表すには大きすぎる (または小さすぎる) 数値の場合、`TryParse` は false を返し、out パラメーターを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="3adac-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="3adac-106">それ以外の場合は true を返し、out パラメーターを文字列の数値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3adac-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3adac-107">文字列が数値文字列だけを含んでいても、使用する `TryParse` メソッドの型として有効ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3adac-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="3adac-108">たとえば、"256" は `byte` の有効値ではありませんが、`int` としては有効です。</span><span class="sxs-lookup"><span data-stu-id="3adac-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="3adac-109">" 98.6" は `int` の有効値ではありませんが、有効な `decimal` です。</span><span class="sxs-lookup"><span data-stu-id="3adac-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3adac-110">例</span><span class="sxs-lookup"><span data-stu-id="3adac-110">Example</span></span>  
 <span data-ttu-id="3adac-111">次の例では、`long` 値、`byte` 値、および `decimal` 値の文字列表現を指定して `TryParse` を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3adac-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 <span data-ttu-id="3adac-112">[!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3adac-112">[!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3adac-113">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="3adac-113">Robust Programming</span></span>  
 <span data-ttu-id="3adac-114">プリミティブ数値型は、`Parse` 静的メソッドも実装します。このメソッドは、文字列が有効な数値でない場合は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3adac-114">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="3adac-115">一般に、数値が有効でない場合は単に false を返す `TryParse` の方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="3adac-115">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3adac-116">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3adac-116">.NET Framework Security</span></span>  
 <span data-ttu-id="3adac-117">テキスト ボックス、コンボ ボックスなどのコントロールからのユーザー入力を検証するには、常に `TryParse` メソッドまたは `Parse` メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="3adac-117">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3adac-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3adac-118">See Also</span></span>  
 <span data-ttu-id="3adac-119">[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md) </span><span class="sxs-lookup"><span data-stu-id="3adac-119">[How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md) </span></span>  
 <span data-ttu-id="3adac-120">[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md) </span><span class="sxs-lookup"><span data-stu-id="3adac-120">[How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md) </span></span>  
 <span data-ttu-id="3adac-121">[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) </span><span class="sxs-lookup"><span data-stu-id="3adac-121">[How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) </span></span>  
 <span data-ttu-id="3adac-122">[数値文字列の解析](../../../standard/base-types/parsing-numeric.md) </span><span class="sxs-lookup"><span data-stu-id="3adac-122">[Parsing Numeric Strings](../../../standard/base-types/parsing-numeric.md) </span></span>  
 [<span data-ttu-id="3adac-123">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="3adac-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

