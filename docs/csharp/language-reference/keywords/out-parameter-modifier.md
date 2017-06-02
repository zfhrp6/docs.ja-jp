---
title: "out パラメーター修飾子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: a2f2e9b9239836b051820bda66523822e95cdf52
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="out-parameter-modifier-c-reference"></a>out パラメーター修飾子 (C# リファレンス)
`out` キーワードによって、参照により引数が渡されます。 これは、[ref](../../../csharp/language-reference/keywords/ref.md) キーワードと似ていますが、`ref` では、変数を初期化してから渡す必要があります。 `out` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方で `out` キーワードを明示的に使用する必要があります。 例:  
  
 [!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> `out` キーワードは、ジェネリック型パラメーターと共に使用すると、型パラメーターが共変であることを指定することもできます。 このコンテキストでの `out` キーワードの使用方法の詳細については、「[out (ジェネリック修飾子)](../../../csharp/language-reference/keywords/out-generic-modifier.md)」を参照してください。
  
 `out` の引数として渡される変数は、メソッド呼び出しで渡される前に初期化する必要はありません。 ただし、呼び出されたメソッドでは、メソッドから制御が返される前に値を割り当てる必要があります。  
  
 `ref` キーワードと `out` キーワードは実行時の動作が異なりますが、コンパイル時に、メソッド シグネチャの一部とは見なされません。 したがって、唯一の違いが、1 つのメソッドは `ref` 引数を使用し、もう一方のメソッドは `out` 引数を使用することである場合、メソッドはオーバーロードできません。 たとえば、次のコードはコンパイルされません。  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
ただし、一方のメソッドが `ref` 引数または `out` 引数を受け取り、もう一方のメソッドがどちらの引数も使用しない場合は、オーバーロードを実行できます。この例を次に示します。  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 プロパティは変数ではないため、`out` パラメーターとして渡すことはできません。  
  
 配列を渡す方法については、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の種類のメソッドには、`ref` キーワードと `out` キーワードを使用することはできません。  
  
-   [async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド。  
  
-   [yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド。  

## <a name="declaring-out-arguments"></a>`out` 引数の宣言   

 `out` 引数を含むメソッドを宣言すると、メソッドで複数の値を返す場合に便利です。 次の例では `out` を使用して、1 つのメソッド呼び出しで 3 つの変数を返します。 3 番目の引数が null に割り当てられることに注意してください。 これにより、必要に応じてメソッドが値を返すことができます。  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 [Try パターン](https://docs.microsoft.com/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md)には、操作が成功したか失敗したかを示す `bool` を返す処理と、操作によって生成された値を `out` 引数で返す処理が含まれます。 @System.DateTime.TryParse(System.String,@System.DateTime) メソッドなど、多くの解析メソッドでこのパターンが使用されます。
   
## <a name="calling-a-method-with-an-out-argument"></a>`out` 引数を含むメソッドの呼び出し

C# 6 以前では、変数を別のステートメントで宣言してから `out` 引数として渡す必要があります。 次の例では、`number` という名前の変数を宣言してから、文字列を数値に変換する [Int32.TryParse](xref:System.Int32.TryParse(System.String,@System.Int32) メソッドに渡しています。

 [!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

C# 7 以降では、`out` 変数を、別の変数宣言内ではなく、メソッド呼び出しの引数リスト内で宣言できます。 これにより、よりコンパクトで読みやすいコードが生成されます。また、メソッド呼び出しの前に誤って変数に値を割り当てることもなくなります。 次の例は前の例と似ていますが、[Int32.TryParse](xref:System.Int32.TryParse(System.String,@System.Int32) メソッドの呼び出しで `number` 変数を定義している点が異なります。

 [!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
前の例では、`number` 変数は `int` として厳密に型指定されています。 次の例のように、暗黙的に型指定されたローカル変数を宣言することもできます。

 [!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)
