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
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a>方法: String.Split を使用して文字列を解析する (C# プログラミング ガイド)
<xref:System.String.Split%2A?displayProperty=nameWithType> メソッドを使用して文字列を解析する方法を次のコード例に示します。 入力として、 <xref:System.String.Split%2A> は、ターゲット文字列から対象の部分文字列を区切る文字を示す文字配列を受け取ります。  関数は、部分文字列を含む配列を返します。  
  
 この例ではスペース、コンマ、ピリオド、コロン、およびタブを使用しています。すべて、これらの区切り文字を格納した配列で <xref:System.String.Split%2A>に渡されます。  ターゲット文字列の文に含まれている各単語は、結果の文字列の配列とは別に表示されます。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a>例  
 既定では、対象の文字列内に区切り文字が 2 つ連続して現れた場合、String.Split は空の文字列を返します。  オプションの StringSplitOptions.RemoveEmptyEntries パラメーターを渡すと、出力から空の文字列を除外することができます。  
  
 String.Split は、文字列の配列 (1 つの文字ではなく、対象の文字列を解析するための区切り記号として機能する文字シーケンス) を受け取ることができます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [文字列](../../../csharp/programming-guide/strings/index.md)  
 [.NET Framework 正規表現](https://msdn.microsoft.com/library/hs600312)
