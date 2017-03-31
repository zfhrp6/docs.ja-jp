---
title: "=&gt; 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a75967e61d2c674e87e321de1fb6e4062cca4f19
ms.lasthandoff: 03/13/2017

---
# <a name="gt-operator-c-reference"></a>=&gt; 演算子 (C# リファレンス)
`=>` トークンはラムダ演算子と呼ばれます。 これは、左側の入力変数を右側のラムダ本体から分けるために*ラムダ式*で使用されます。 ラムダ式はインライン式の一種で匿名メソッドと似ていますが、それよりも柔軟性があります。この式はメソッド構文で表される LINQ クエリで広く使用されています。 詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 次の例では、文字列の配列の最も短い文字列の長さを検索して表示する 2 とおりの方法を示します。 この例の最初の部分では、`words` の配列の各要素にラムダ式 (`w => w.Length`) を適用し、<xref:System.Linq.Enumerable.Min%2A> メソッドを使用して最小の長さを検索します。 比較のために、例の 2 番目の部分では、同じ機能を実行するためにクエリ構文を使用する長いソリューションを示します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="remarks"></a>コメント  
 `=>` 演算子と代入演算子 (`=`) は優先順位が同じで、結合規則が右から左です。  
  
 入力変数の型を明示的に指定することができます。また、コンパイラで型を推測することもできます。いずれの場合も、変数はコンパイル時に厳密に型指定されます。 型を指定する場合は、次の例のように、型名と変数名をかっこで囲む必要があります。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example"></a>例  
 次の例は、2 つの引数を受け取る標準クエリ演算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> のオーバーロードのラムダ式を記述する方法を示しています。 ラムダ式には複数のパラメーターがあるため、パラメーターをかっこで囲む必要があります。 2 番目のパラメーター `index` は、コレクション内の現在の要素のインデックスを表します。 `Where` 式は、長さが配列内のインデックスの位置より短い文字列をすべて返します。  
  
```cs  
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
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
