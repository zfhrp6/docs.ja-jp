---
title: "where (ジェネリック型制約) (C# リファレンス)"
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="6491d-102">where (ジェネリック型制約) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6491d-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="6491d-103">ジェネリック型定義では、ジェネリック宣言で定義されている型パラメーターの引数として使用できる型に対する制約を指定する場合に `where` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="6491d-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="6491d-104">たとえば、型パラメーター `T` が <xref:System.IComparable%601> インターフェイスを実装するように、次のように `MyGenericClass` ジェネリック クラスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="6491d-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="6491d-105">クエリ式での where 句の詳細については、「[where 句](../../../csharp/language-reference/keywords/where-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6491d-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="6491d-106">`where` 句には、インターフェイス制約だけでなく基底クラス制約も含めることができます。基底クラス制約は、ジェネリック型の型引数として使用する型には、基底クラスとして指定されているクラス (または基底クラス自体) が含まれている必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6491d-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="6491d-107">このような制約を使用する場合は、型パラメーターに関する制約よりも前に制約を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6491d-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 <span data-ttu-id="6491d-108">`where` 句には、コンストラクター制約を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="6491d-108">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="6491d-109">新しい演算子を使用して、型パラメーターのインスタンスを作成することができます。ただし、その場合は、型パラメーターにコンストラクター制約 `new()` で制約を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6491d-109">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="6491d-110">[new() 制約](../../../csharp/language-reference/keywords/new-constraint.md)に基づいて、コンパイラは、指定されている型引数には、アクセス可能なパラメーターなしの (または既定の) コンストラクターが必要であることを認識します。</span><span class="sxs-lookup"><span data-stu-id="6491d-110">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="6491d-111">例:</span><span class="sxs-lookup"><span data-stu-id="6491d-111">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 <span data-ttu-id="6491d-112">`new()` 制約は `where` 句の最後に示されます。</span><span class="sxs-lookup"><span data-stu-id="6491d-112">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="6491d-113">複数の型パラメーターがある場合には、型パラメーターごとに `where` 句を 1 つずつ使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6491d-113">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 <span data-ttu-id="6491d-114">次に示すように、ジェネリック メソッドの型パラメーターにも制約を適用できます。</span><span class="sxs-lookup"><span data-stu-id="6491d-114">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="6491d-115">デリゲートに対する型パラメーター制約を記述する構文は、メソッドの構文と同じである点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6491d-115">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="6491d-116">汎用デリゲートについては、「[汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6491d-116">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="6491d-117">制約の構文と使用方法の詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6491d-117">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6491d-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6491d-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6491d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6491d-119">See Also</span></span>  
 [<span data-ttu-id="6491d-120">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6491d-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6491d-121">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6491d-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6491d-122">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="6491d-122">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="6491d-123">new 制約</span><span class="sxs-lookup"><span data-stu-id="6491d-123">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="6491d-124">型パラメーターの制約</span><span class="sxs-lookup"><span data-stu-id="6491d-124">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
