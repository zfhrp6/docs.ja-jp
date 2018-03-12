---
title: "ref (C# リファレンス)"
ms.date: 05/30/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b1e926bd1d9c3a8e0525ed02d102f26e6ec9abd
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="ref-c-reference"></a>ref (C# リファレンス)

`ref` キーワードは、参照渡しで渡される値を示します。 このキーワードは、3 つの異なるコンテキストで使用されます。 

- メソッド シグネチャとメソッドの呼び出しで、参照によってメソッドに引数を渡します。 詳細については、「[参照渡しで引数を渡す](#passing-an-argument-by-reference)」を参照してください。

- メソッド シグネチャで、参照渡しで呼び出し元に値を返します。 詳細については、「[参照戻り値](#reference-return-values)」を参照してください。

- メンバーの本文で、参照戻り値が、呼び出し元によって変更される参照としてローカルに格納されることを示します。 詳細については、「[ref ローカル変数](#ref-locals)」を参照してください。

## <a name="passing-an-argument-by-reference"></a>参照渡しで引数を渡す

メソッドのパラメーター リストで使用した場合、`ref` キーワードは、引数を値ではなく、参照によって渡すことを示します。 参照渡しで渡すことにより、呼び出されたメソッドの引数に対する変更が、呼び出し元のメソッドに反映されます。 たとえば、呼び出し元がローカル変数の式、または配列要素のアクセス式を渡し、呼び出されたメソッドが ref パラメーターが参照するオブジェクトを置き換える場合、メソッドが戻ったときに呼び出し元のローカル変数または配列要素は新しいオブジェクトを参照します。

> [!NOTE]
>  参照渡しの概念と参照型の概念を混同しないでください。 2 つの概念は同じではありません。 メソッドのパラメーターは、値型か参照型かどうかに関係なく、`ref` によって変更できます。 参照渡しで渡される場合、値型はボックス化されません。  

`ref` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方が、次の例に示すように `ref` キーワードを明示的に使用する必要があります。  

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

`ref` パラメーターに渡す引数は、渡す前に初期化する必要があります。 これは、引数を渡す前に明示的に初期化する必要がない [out](out.md) パラメーターとは異なります。

クラスのメンバーは、`ref` と `out` だけが異なるシグネチャを持つことはできません。 1 つの型の 2 つのメンバー間の違いが、1 つには `ref` パラメーターがあり、もう 1 つには `out` パラメーターがあることのみの場合は、コンパイラ エラーが発生します。 たとえば、次のコードはコンパイルされません。  
  
 [!code-csharp[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 ただし、次の例に示すように、1 つのメソッドに `ref` または `out` パラメーターがあり、もう 1 つのメソッドに値パラメーターがある場合、メソッドをオーバーロードすることができます。
  
 [!code-csharp[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 非表示やオーバーライドなど、シグネチャの一致が必要な他の状況では、`ref` と `out` はシグネチャの一部であり互いに一致しません。  
  
 プロパティは変数ではありません。 プロパティはメソッドであり、`ref` パラメーターに渡すことはできません。  
  
 配列を渡す方法については、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の種類のメソッドには、`ref` キーワードと `out` キーワードを使用することはできません。  
  
-   [async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド。  
  
-   [yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド。  
  
## <a name="passing-an-argument-by-reference-an-example"></a>参照渡しで引数を渡す: 使用例

前の例は、参照によって値型を渡す例でした。 `ref` キーワードを使用して、参照渡しで参照型を渡すこともできます。 参照型を参照渡しで渡すと、呼び出されたメソッドは、参照パラメーターが呼び出し元で参照するオブジェクトに置換できます。 オブジェクトの格納場所は、参照パラメーターの値としてメソッドに渡されます。 パラメーターの格納場所の値を変更する場合は (新しいオブジェクトをポイント)、呼び出し元が参照する格納場所を変更することもできます。 次の例では、参照型のインスタンスを `ref` パラメーターとして渡します。   
  
 [!code-csharp[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

参照型を値渡しまたは参照渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)」を参照してください。
  
## <a name="reference-return-values"></a>参照戻り値

参照戻り値 (または ref 戻り値) は、メソッドから呼び出し元に参照渡しで返される値です。 つまり、呼び出し元はメソッドによって返される値を変更することができ、メソッドを格納するオブジェクトの状態にその変更が反映されます。 

参照戻り値は `ref` キーワードを使用して以下に定義されます。

- メソッド シグネチャ。 たとえば、次のメソッド シグネチャは、`GetCurrentPrice` メソッドが参照渡しで <xref:System.Decimal> 値を返すことを示しています。

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- メソッドの `return` ステートメントで返される変数と `return` トークンの間。 例:
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

呼び出し元がオブジェクトの状態を変更するには、[ref ローカル変数](#ref-locals)として明示的に定義した変数に参照戻り値を格納する必要があります。 

例については、「[ref 戻り値と ref ローカル変数](#a-ref-returns-and-ref-locals-example)」を参照してください。

## <a name="ref-locals"></a>ref ローカル変数

ref ローカル変数は、`return ref` を使用して返された値を参照するために使用します。  ref ローカル変数は、初期化して ref 戻り値に割り当てる必要があります。 ref ローカル変数の値に変更を加えると、参照渡しの値を返すメソッドのオブジェクトの状態に反映されます。

ref ローカル変数を定義するには、変数宣言の前と、参照渡しで値を返すメソッドの呼び出しの直前に、`ref` キーワードを使用します。 

たとえば、次のステートメントは、`GetEstimatedValue` という名前のメソッドによって返される ref ローカル変数を定義しています。

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

なお、`ref` キーワードは両方の位置で使用する必要があります。そうしないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>ref 戻り値と ref ローカル変数の使用例

次の例は、`Title` と `Author` という 2 つの <xref:System.String> フィールドを持つ `Book` クラスを定義しています。 また、`Book` オブジェクトのプライベート配列を含む `BookCollection` クラスも定義しています。 個々のブック オブジェクトは、`GetBookByTitle` メソッドを呼び出すことによって参照渡しで返されます。

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

呼び出し元が `GetBookByTitle` によって返される値を ref ローカル変数として格納する場合、呼び出し元が戻り値に加えた変更が `BookCollection` オブジェクトに反映されます。次の例を参照してください。

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
