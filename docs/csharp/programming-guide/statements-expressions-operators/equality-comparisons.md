---
title: "等価比較 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 14
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 948bbc1b5b8535cc31ea362497fa69a816b43edc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="equality-comparisons-c-programming-guide"></a><span data-ttu-id="412d4-102">等価比較 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="412d4-102">Equality Comparisons (C# Programming Guide)</span></span>
<span data-ttu-id="412d4-103">2 つの値が等しいかどうかを比較することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="412d4-103">It is sometimes necessary to compare two values for equality.</span></span> <span data-ttu-id="412d4-104">そのような場合、*値が等価であること* (*等価性*と呼ばれる) をテストすることになります。等価性とは 2 つの変数に含まれる値が等しいことを意味します。</span><span class="sxs-lookup"><span data-stu-id="412d4-104">In some cases, you are testing for *value equality*, also known as *equivalence*, which means that the values that are contained by the two variables are equal.</span></span> <span data-ttu-id="412d4-105">また、2 つの変数がメモリ内の同一の基になるオブジェクトを参照しているかどうかを確認する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="412d4-105">In other cases, you have to determine whether two variables refer to the same underlying object in memory.</span></span> <span data-ttu-id="412d4-106">このタイプの等価は、*参照の等価性*または*同一性*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="412d4-106">This type of equality is called *reference equality*, or *identity*.</span></span> <span data-ttu-id="412d4-107">ここでは、2 種類の等価について説明します。また、詳細について他のトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="412d4-107">This topic describes these two kinds of equality and provides links to other topics for more information.</span></span>  
  
## <a name="reference-equality"></a><span data-ttu-id="412d4-108">参照の等価性</span><span class="sxs-lookup"><span data-stu-id="412d4-108">Reference Equality</span></span>  
 <span data-ttu-id="412d4-109">参照の等価とは、2 つのオブジェクト参照が同一の基になるオブジェクトを参照していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="412d4-109">Reference equality means that two object references refer to the same underlying object.</span></span> <span data-ttu-id="412d4-110">次の例に示すように、これは簡単な代入によって生じます。</span><span class="sxs-lookup"><span data-stu-id="412d4-110">This can occur through simple assignment, as shown in the following example.</span></span>  
  
 <span data-ttu-id="412d4-111">[!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="412d4-111">[!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]</span></span>  
  
 <span data-ttu-id="412d4-112">このコードでは、2 つのオブジェクトが作成されますが、代入ステートメント以降は、両方の参照が同一のオブジェクトを参照しています。</span><span class="sxs-lookup"><span data-stu-id="412d4-112">In this code, two objects are created, but after the assignment statement, both references refer to the same object.</span></span> <span data-ttu-id="412d4-113">したがって、参照の等価性があります。</span><span class="sxs-lookup"><span data-stu-id="412d4-113">Therefore they have reference equality.</span></span> <span data-ttu-id="412d4-114">2 つの参照が同じオブジェクトを参照しているかどうかを判断するには、<xref:System.Object.ReferenceEquals%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="412d4-114">Use the <xref:System.Object.ReferenceEquals%2A> method to determine whether two references refer to the same object.</span></span>  
  
 <span data-ttu-id="412d4-115">参照の等価性の概念は参照型のみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="412d4-115">The concept of reference equality applies only to reference types.</span></span> <span data-ttu-id="412d4-116">値型オブジェクトには参照の等価性がありません。これは、値型のインスタンスが変数に代入される場合、値のコピーが作成されるためです。</span><span class="sxs-lookup"><span data-stu-id="412d4-116">Value type objects cannot have reference equality because when an instance of a value type is assigned to a variable, a copy of the value is made.</span></span> <span data-ttu-id="412d4-117">そのため、ボックス化を解除した 2 つの構造体でメモリ内の同じ場所を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="412d4-117">Therefore you can never have two unboxed structs that refer to the same location in memory.</span></span> <span data-ttu-id="412d4-118">さらに、<xref:System.Object.ReferenceEquals%2A> を使用して 2 つの値型を比較する場合、オブジェクトに含まれている値がすべて同一である場合でも、結果は常に `false` になります。</span><span class="sxs-lookup"><span data-stu-id="412d4-118">Furthermore, if you use <xref:System.Object.ReferenceEquals%2A> to compare two value types, the result will always be `false`, even if the values that are contained in the objects are all identical.</span></span> <span data-ttu-id="412d4-119">これは、各変数が個別のオブジェクト インスタンスにボックス化されているためです。</span><span class="sxs-lookup"><span data-stu-id="412d4-119">This is because each variable is boxed into a separate object instance.</span></span> <span data-ttu-id="412d4-120">詳細については、「[方法: 参照の等価性 (同値) をテストする](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="412d4-120">For more information, see [How to: Test for Reference Equality (Identity)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span></span>  
  
## <a name="value-equality"></a><span data-ttu-id="412d4-121">値の等価性</span><span class="sxs-lookup"><span data-stu-id="412d4-121">Value Equality</span></span>  
 <span data-ttu-id="412d4-122">値が等価であるとは、2 つのオブジェクトが同じ値を含むことを意味します。</span><span class="sxs-lookup"><span data-stu-id="412d4-122">Value equality means that two objects contain the same value or values.</span></span> <span data-ttu-id="412d4-123">[int](../../../csharp/language-reference/keywords/int.md)、[bool](../../../csharp/language-reference/keywords/bool.md) などのプリミティブ値型では、値が等価であることをテストするのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="412d4-123">For primitive value types such as [int](../../../csharp/language-reference/keywords/int.md) or [bool](../../../csharp/language-reference/keywords/bool.md), tests for value equality are straightforward.</span></span> <span data-ttu-id="412d4-124">次の例に示すように、[==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="412d4-124">You can use the [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) operator, as shown in the following example.</span></span>  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 <span data-ttu-id="412d4-125">それ以外のほとんどの型については、値が等価であることをテストするのは、もっと複雑です。特定の型で等価性がどのように定義されるかを理解する必要があるからです。</span><span class="sxs-lookup"><span data-stu-id="412d4-125">For most other types, testing for value equality is more complex because it requires that you understand how the type defines it.</span></span> <span data-ttu-id="412d4-126">複数のフィールドまたはプロパティを含むクラスおよび構造体では、多くの場合、値が等価であるとは、すべてのフィールドまたはプロパティが同一の値を含むことであると定義されます。</span><span class="sxs-lookup"><span data-stu-id="412d4-126">For classes and structs that have multiple fields or properties, value equality is often defined to mean that all fields or properties have the same value.</span></span> <span data-ttu-id="412d4-127">たとえば、pointA.X が pointB.X と等しく、pointA.Y が pointB.Y と等しい場合、2 つの `Point` オブジェクトは等価であると定義されます。</span><span class="sxs-lookup"><span data-stu-id="412d4-127">For example, two `Point` objects might be defined to be equivalent if pointA.X is equal to pointB.X and pointA.Y is equal to pointB.Y.</span></span>  
  
 <span data-ttu-id="412d4-128">ただし、等価性を 1 つの型のすべてのフィールドに基づいて判断する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="412d4-128">However, there is no requirement that equivalence be based on all the fields in a type.</span></span> <span data-ttu-id="412d4-129">サブセットに基づいて判断できます。</span><span class="sxs-lookup"><span data-stu-id="412d4-129">It can be based on a subset.</span></span> <span data-ttu-id="412d4-130">所有していない型を比較する場合は、その型の等価性がどのように定義されるのかを明確に理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="412d4-130">When you compare types that you do not own, you should make sure to understand specifically how equivalence is defined for that type.</span></span> <span data-ttu-id="412d4-131">独自のクラスおよび構造体で値が等しいかどうかを定義する方法の詳細については、「[方法: 型の値の等価性を定義する](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="412d4-131">For more information about how to define value equality in your own classes and structs, see [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span></span>  
  
### <a name="value-equality-for-floating-point-values"></a><span data-ttu-id="412d4-132">浮動小数点値での値の等価性</span><span class="sxs-lookup"><span data-stu-id="412d4-132">Value Equality for Floating Point Values</span></span>  
 <span data-ttu-id="412d4-133">バイナリのコンピューター上での浮動小数点演算には誤差があるため、浮動小数点値 ([double](../../../csharp/language-reference/keywords/double.md) および [float](../../../csharp/language-reference/keywords/float.md)) の等価比較には問題があります。</span><span class="sxs-lookup"><span data-stu-id="412d4-133">Equality comparisons of floating point values ([double](../../../csharp/language-reference/keywords/double.md) and [float](../../../csharp/language-reference/keywords/float.md)) are problematic because of the imprecision of floating point arithmetic on binary computers.</span></span> <span data-ttu-id="412d4-134">詳細については、<xref:System.Double?displayProperty=fullName> のトピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="412d4-134">For more information, see the remarks in the topic <xref:System.Double?displayProperty=fullName>.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="412d4-135">関連トピック</span><span class="sxs-lookup"><span data-stu-id="412d4-135">Related Topics</span></span>  
  
|<span data-ttu-id="412d4-136">タイトル</span><span class="sxs-lookup"><span data-stu-id="412d4-136">Title</span></span>|<span data-ttu-id="412d4-137">説明</span><span class="sxs-lookup"><span data-stu-id="412d4-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="412d4-138">方法: 参照の等価性 (同値) をテストする</span><span class="sxs-lookup"><span data-stu-id="412d4-138">How to: Test for Reference Equality (Identity)</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|<span data-ttu-id="412d4-139">2 つの変数に参照の等価性があるかどうかを確認する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="412d4-139">Describes how to determine whether two variables have reference equality.</span></span>|  
|[<span data-ttu-id="412d4-140">方法: 型の値の等価性を定義する</span><span class="sxs-lookup"><span data-stu-id="412d4-140">How to: Define Value Equality for a Type</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|<span data-ttu-id="412d4-141">型の値の等価性にカスタムの定義を指定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="412d4-141">Describes how to provide a custom definition of value equality for a type.</span></span>|  
|[<span data-ttu-id="412d4-142">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="412d4-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)|<span data-ttu-id="412d4-143">C# 言語の重要な機能に関する詳細情報へのリンクを示します。また、.NET Framework 経由でアクセスできる C# の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="412d4-143">Provides links to detailed information about important C# language features and features that are available to C# through the .NET Framework.</span></span>|  
|[<span data-ttu-id="412d4-144">型</span><span class="sxs-lookup"><span data-stu-id="412d4-144">Types</span></span>](../../../csharp/programming-guide/types/index.md)|<span data-ttu-id="412d4-145">C# 型システムについて説明し、詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="412d4-145">Provides information about the C# type system and links to additional information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="412d4-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="412d4-146">See Also</span></span>  
 [<span data-ttu-id="412d4-147">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="412d4-147">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

