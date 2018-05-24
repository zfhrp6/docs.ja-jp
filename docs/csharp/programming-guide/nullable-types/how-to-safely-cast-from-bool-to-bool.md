---
title: '方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
ms.openlocfilehash: e04e34abd477730f9dd01486ec6bddcde4943edc
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)
Null 許容 `bool?` 型は、`true`、`false`、`null` の 3 つの異なる値を格納できます。 そのため、`bool?` 型は、`if`、`for`、`while` などの条件文で使用できません。 たとえば、次のコードはコンパイラ エラーになります。  
  
```csharp  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 コンパイルできないのは、条件文のコンテキストで `null` の意味があいまいだからです。 条件付きステートメントで `bool?` を使用するにはまず、その <xref:System.Nullable%601.HasValue%2A> プロパティをチェックしてその値が `null` でないことを確認します。次に、`bool` にキャストします。 詳細については、「[bool](../../../csharp/language-reference/keywords/bool.md)」を参照してください。 `bool?` でキャストを実行するときに値が `null` になっていると、条件テストで <xref:System.InvalidOperationException> がスローされます。 次の例は、`bool?` から `bool` に安全にキャストするための 1 つの方法を示しています。  
  
## <a name="example"></a>例  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [リテラル キーワード](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
 [??演算子](../../../csharp/language-reference/operators/null-coalescing-operator.md)
