---
title: where (ジェネリック型制約) (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a>where (ジェネリック型制約) (C# リファレンス)
ジェネリック型定義では、ジェネリック宣言で定義されている型パラメーターの引数として使用できる型に対する制約を指定する場合に `where` 句を使用します。 たとえば、型パラメーター `T` が <xref:System.IComparable%601> インターフェイスを実装するように、次のように `MyGenericClass` ジェネリック クラスを宣言できます。  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  クエリ式での where 句の詳細については、「[where 句](../../../csharp/language-reference/keywords/where-clause.md)」を参照してください。  
  
 `where` 句には、インターフェイス制約だけでなく基底クラス制約も含めることができます。基底クラス制約は、ジェネリック型の型引数として使用する型には、基底クラスとして指定されているクラス (または基底クラス自体) が含まれている必要があることを指定します。 このような制約を使用する場合は、型パラメーターに関する制約よりも前に制約を記述する必要があります。  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` 句には、コンストラクター制約を含めることもできます。 新しい演算子を使用して、型パラメーターのインスタンスを作成することができます。ただし、その場合は、型パラメーターにコンストラクター制約 `new()` で制約を指定する必要があります。 [new() 制約](../../../csharp/language-reference/keywords/new-constraint.md)に基づいて、コンパイラは、指定されている型引数には、アクセス可能なパラメーターなしの (または既定の) コンストラクターが必要であることを認識します。 例:  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` 制約は `where` 句の最後に示されます。  
  
 複数の型パラメーターがある場合には、型パラメーターごとに `where` 句を 1 つずつ使用します。次に例を示します。  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 次に示すように、ジェネリック メソッドの型パラメーターにも制約を適用できます。  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 デリゲートに対する型パラメーター制約を記述する構文は、メソッドの構文と同じである点に注意してください。  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 汎用デリゲートについては、「[汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)」を参照してください。  
  
 制約の構文と使用方法の詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [new 制約](../../../csharp/language-reference/keywords/new-constraint.md)  
 [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
