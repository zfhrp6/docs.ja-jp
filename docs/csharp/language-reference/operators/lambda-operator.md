---
title: "=&gt; 演算子 (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "=>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ラムダ演算子 [C#]"
  - "=> 演算子 [C#]"
  - "ラムダ式 [C#]、=> 演算子"
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# =&gt; 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`=>` トークンはラムダ演算子と呼ばれます。  これは、左側の入力変数を右側のラムダ本体から分けるために*ラムダ式*で使用されます。  ラムダ式はインライン式の一種で匿名メソッドと似ていますが、それよりも柔軟性があります。この式はメソッド構文で表される LINQ クエリで広く使用されています。  詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 次の例では、文字列の配列の最も短い文字列の長さを検索、表示、2 とおりの方法を示します。  この例の最初の部分は `words` の配列の各要素にラムダ式 \(`w => w.Length`\) を適用し、最小の長さを確認するには <xref:System.Linq.Enumerable.Min%2A> のメソッドを使用します。  比較のために、例の 2 番目の部分は同じ機能を実行するために長いソリューションを使用するクエリ構文示します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## 解説  
 `=>` 演算子と代入演算子 \(`=`\) は優先順位が同じで、結合規則が右から左です。  
  
 入力変数の型を明示的に指定できますが、コンパイラが型を推論するようにします; いずれの場合も、変数はコンパイル時に厳密に型指定されます。  型を指定するときは、次の例に示すようにかっこ内の型名と変数名を囲む必要があります。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## 使用例  
 次の例は、2 個の引数を受け取る標準クエリ演算子の <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> のオーバーロードのラムダ式を記述する方法を示します。  ラムダ式には複数のパラメーターがあるため、パラメーターはかっこで囲む必要があります。  2 番目のパラメーター \(`index`は、コレクションの現在の要素のインデックスを表します。  `Where` の式は、長さが配列内のインデックス位置よりも、すべての文字列を返します。  
  
```c#  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Compare the following code, which arrives at the same list of short  
    // digits but takes more work to get there.  
    Console.WriteLine("\nExample that uses a for loop:");  
    List<string> shortDigits2 = new List<string>();  
    for (var i = 0; i < digits.Length; i++)  
    {  
        if (digits[i].Length < i)  
            shortDigits2.Add(digits[i]);  
    }  
  
    foreach (var d in shortDigits2)  
    {  
        Console.WriteLine(d);  
    }  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
  
    // Example that uses a for loop:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)