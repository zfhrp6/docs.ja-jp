---
title: "where (ジェネリック型制約) (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
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
ms.openlocfilehash: 8e81640ee56ed672bb09242a070fdf167740874b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="f305c-102">where (ジェネリック型制約) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f305c-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="f305c-103">ジェネリック型定義では、ジェネリック宣言で定義されている型パラメーターの引数として使用できる型に対する制約を指定する場合に `where` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="f305c-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="f305c-104">たとえば、型パラメーター `T` が <xref:System.IComparable%601> インターフェイスを実装するように、次のように `MyGenericClass` ジェネリック クラスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="f305c-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="f305c-105">クエリ式での where 句の詳細については、「[where 句](../../../csharp/language-reference/keywords/where-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f305c-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="f305c-106">`where` 句には、インターフェイス制約だけでなく基底クラス制約も含めることができます。基底クラス制約は、ジェネリック型の型引数として使用する型には、基底クラスとして指定されているクラス (または基底クラス自体) が含まれている必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f305c-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="f305c-107">このような制約を使用する場合は、型パラメーターに関する制約よりも前に制約を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f305c-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 <span data-ttu-id="f305c-108">[!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f305c-108">[!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]</span></span>  
  
 <span data-ttu-id="f305c-109">`where` 句には、コンストラクター制約を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f305c-109">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="f305c-110">新しい演算子を使用して、型パラメーターのインスタンスを作成することができます。ただし、その場合は、型パラメーターにコンストラクター制約 `new()` で制約を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f305c-110">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="f305c-111">[new() 制約](../../../csharp/language-reference/keywords/new-constraint.md)に基づいて、コンパイラは、指定されている型引数には、アクセス可能なパラメーターなしの (または既定の) コンストラクターが必要であることを認識します。</span><span class="sxs-lookup"><span data-stu-id="f305c-111">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="f305c-112">例:</span><span class="sxs-lookup"><span data-stu-id="f305c-112">For example:</span></span>  
  
 <span data-ttu-id="f305c-113">[!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f305c-113">[!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]</span></span>  
  
 <span data-ttu-id="f305c-114">`new()` 制約は `where` 句の最後に示されます。</span><span class="sxs-lookup"><span data-stu-id="f305c-114">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="f305c-115">複数の型パラメーターがある場合には、型パラメーターごとに `where` 句を 1 つずつ使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f305c-115">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 <span data-ttu-id="f305c-116">[!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f305c-116">[!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]</span></span>  
  
 <span data-ttu-id="f305c-117">次に示すように、ジェネリック メソッドの型パラメーターにも制約を適用できます。</span><span class="sxs-lookup"><span data-stu-id="f305c-117">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="f305c-118">デリゲートに対する型パラメーター制約を記述する構文は、メソッドの構文と同じである点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f305c-118">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="f305c-119">汎用デリゲートについては、「[汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f305c-119">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="f305c-120">制約の構文と使用方法の詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f305c-120">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f305c-121">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f305c-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f305c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f305c-122">See Also</span></span>  
 <span data-ttu-id="f305c-123">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f305c-123">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f305c-124">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f305c-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f305c-125">[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="f305c-125">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="f305c-126">[new 制約](../../../csharp/language-reference/keywords/new-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="f305c-126">[new Constraint](../../../csharp/language-reference/keywords/new-constraint.md) </span></span>  
 [<span data-ttu-id="f305c-127">型パラメーターの制約</span><span class="sxs-lookup"><span data-stu-id="f305c-127">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)

