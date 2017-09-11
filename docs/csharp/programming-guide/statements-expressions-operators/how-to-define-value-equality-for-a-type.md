---
title: "方法: 型の値の等価性を定義する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
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
ms.openlocfilehash: e008be022765ff7d2bb440f0a37193b882038b76
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a><span data-ttu-id="5c702-102">方法: 型の値の等価性を定義する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5c702-102">How to: Define Value Equality for a Type (C# Programming Guide)</span></span>
<span data-ttu-id="5c702-103">クラスまたは構造体を定義する場合は、型に値の等価性 (同値) のカスタム定義を作成することが有用かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5c702-103">When you define a class or struct, you decide whether it makes sense to create a custom definition of value equality (or equivalence) for the type.</span></span> <span data-ttu-id="5c702-104">通常、値の等価性を実装するのは、その型のオブジェクトがある種のコレクションに追加されることが想定されている場合、または、そのオブジェクトの主な目的が一連のフィールドまたはプロパティを格納することである場合です。</span><span class="sxs-lookup"><span data-stu-id="5c702-104">Typically, you implement value equality when objects of the type are expected to be added to a collection of some sort, or when their primary purpose is to store a set of fields or properties.</span></span> <span data-ttu-id="5c702-105">値の等価性は、型のすべてのフィールドおよびプロパティの比較に基づいて定義できます。また、サブセットに基づいて定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="5c702-105">You can base your definition of value equality on a comparison of all the fields and properties in the type, or you can base the definition on a subset.</span></span> <span data-ttu-id="5c702-106">ただし、いずれの場合も、クラスおよび構造体の両方について、等価性を保証する 5 つの条件に従って実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c702-106">But in either case, and in both classes and structs, your implementation should follow the five guarantees of equivalence:</span></span>  
  
1.  <span data-ttu-id="5c702-107">x.`Equals`(x) は `true.` を返します。これは再帰プロパティと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5c702-107">x.`Equals`(x) returns `true.` This is called the reflexive property.</span></span>  
  
2.  <span data-ttu-id="5c702-108">x.`Equals`(y) は、y.`Equals`(x) と同じ値を返します。</span><span class="sxs-lookup"><span data-stu-id="5c702-108">x.`Equals`(y) returns the same value as y.`Equals`(x).</span></span> <span data-ttu-id="5c702-109">これは対照プロパティと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5c702-109">This is called the symmetric property.</span></span>  
  
3.  <span data-ttu-id="5c702-110">(x.`Equals`(y) && y.`Equals`(z)) が `true` を返す場合は、x.`Equals`(z) も `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="5c702-110">if (x.`Equals`(y) && y.`Equals`(z)) returns `true`, then x.`Equals`(z) returns `true`.</span></span> <span data-ttu-id="5c702-111">これは推移的プロパティと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5c702-111">This is called the transitive property.</span></span>  
  
4.  <span data-ttu-id="5c702-112">x.`Equals`(y) が連続して呼び出された場合は、x および y によって参照されるオブジェクトが変更されていない限り、同じ値を返します。</span><span class="sxs-lookup"><span data-stu-id="5c702-112">Successive invocations of x.`Equals`(y) return the same value as long as the objects referenced by x and y are not modified.</span></span>  
  
5.  <span data-ttu-id="5c702-113">x.`Equals`(null) は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="5c702-113">x.`Equals`(null) returns `false`.</span></span> <span data-ttu-id="5c702-114">ただし、null.Equals(null) は例外をスローするため、上の 2 番目の規則には従っていません。</span><span class="sxs-lookup"><span data-stu-id="5c702-114">However, null.Equals(null) throws an exception; it does not obey rule number two above.</span></span>  
  
 <span data-ttu-id="5c702-115">構造体を定義すると、<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> メソッドの <xref:System.ValueType?displayProperty=fullName> オーバーライドから継承された値の等価性が既定で実装されます。</span><span class="sxs-lookup"><span data-stu-id="5c702-115">Any struct that you define already has a default implementation of value equality that it inherits from the <xref:System.ValueType?displayProperty=fullName> override of the <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> method.</span></span> <span data-ttu-id="5c702-116">この実装では、リフレクションを使用して、型のフィールドとプロパティをすべて調べます。</span><span class="sxs-lookup"><span data-stu-id="5c702-116">This implementation uses reflection to examine all the fields and properties in the type.</span></span> <span data-ttu-id="5c702-117">この実装によって正しい結果が生成されますが、その型専用に記述したカスタム実装と比較すると、処理にかなり時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="5c702-117">Although this implementation produces correct results, it is relatively slow compared to a custom implementation that you write specifically for the type.</span></span>  
  
 <span data-ttu-id="5c702-118">値の等価性に関する実装の詳細は、クラスと構造体で異なりますが、</span><span class="sxs-lookup"><span data-stu-id="5c702-118">The implementation details for value equality are different for classes and structs.</span></span> <span data-ttu-id="5c702-119">等価性を実装するための基本的な手順については、両方とも同じです。</span><span class="sxs-lookup"><span data-stu-id="5c702-119">However, both classes and structs require the same basic steps for implementing equality:</span></span>  
  
1.  <span data-ttu-id="5c702-120">[仮想](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5c702-120">Override the [virtual](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> method.</span></span> <span data-ttu-id="5c702-121">ほとんどの場合、`bool Equals( object obj )` の実装には、<xref:System.IEquatable%601?displayProperty=fullName> インターフェイスの実装である型固有の `Equals` メソッドを呼び出すだけで済みます </span><span class="sxs-lookup"><span data-stu-id="5c702-121">In most cases, your implementation of `bool Equals( object obj )` should just call into the type-specific `Equals` method that is the implementation of the <xref:System.IEquatable%601?displayProperty=fullName> interface.</span></span> <span data-ttu-id="5c702-122">(手順 2 を参照)。</span><span class="sxs-lookup"><span data-stu-id="5c702-122">(See step 2.)</span></span>  
  
2.  <span data-ttu-id="5c702-123">型固有の `Equals` メソッドを指定して、<xref:System.IEquatable%601?displayProperty=fullName> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5c702-123">Implement the <xref:System.IEquatable%601?displayProperty=fullName> interface by providing a type-specific `Equals` method.</span></span> <span data-ttu-id="5c702-124">ここで実際の等価性の比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="5c702-124">This is where the actual equivalence comparison is performed.</span></span> <span data-ttu-id="5c702-125">たとえば、型のフィールドを 1 ～ 2 個だけ比較することで等価性を定義できます。</span><span class="sxs-lookup"><span data-stu-id="5c702-125">For example, you might decide to define equality by comparing only one or two fields in your type.</span></span> <span data-ttu-id="5c702-126">`Equals` から例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="5c702-126">Do not throw exceptions from `Equals`.</span></span> <span data-ttu-id="5c702-127">クラスの場合に限り、このメソッドはクラスで宣言されているフィールドのみを調べます。</span><span class="sxs-lookup"><span data-stu-id="5c702-127">For classes only: This method should examine only fields that are declared in the class.</span></span> <span data-ttu-id="5c702-128">基底クラスに含まれるフィールドを調べるには、`base.Equals` を呼び出す必要があります </span><span class="sxs-lookup"><span data-stu-id="5c702-128">It should call `base.Equals` to examine fields that are in the base class.</span></span> <span data-ttu-id="5c702-129">(<xref:System.Object> から型が直接継承された場合は、この呼び出しを行わないでください。<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> の <xref:System.Object> 実装では参照の等価性チェックが実行されるためです)。</span><span class="sxs-lookup"><span data-stu-id="5c702-129">(Do not do this if the type inherits directly from <xref:System.Object>, because the <xref:System.Object> implementation of <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> performs a reference equality check.)</span></span>  
  
3.  <span data-ttu-id="5c702-130">推奨、ただし省略可能: [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 演算子および [!=](../../../csharp/language-reference/operators/not-equal-operator.md) 演算子をオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="5c702-130">Optional but recommended: Overload the [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) and [!=](../../../csharp/language-reference/operators/not-equal-operator.md) operators.</span></span>  
  
4.  <span data-ttu-id="5c702-131">値の等価性を持つ 2 つのオブジェクトによって同じハッシュ コードが生成されるように、<xref:System.Object.GetHashCode%2A?displayProperty=fullName> をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5c702-131">Override <xref:System.Object.GetHashCode%2A?displayProperty=fullName> so that two objects that have value equality produce the same hash code.</span></span>  
  
5.  <span data-ttu-id="5c702-132">省略可能: "大なり" または "小なり" の定義をサポートするには、型に対して <xref:System.IComparable%601> インターフェイスを実装したうえで、[<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) 演算子および [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) 演算子をオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="5c702-132">Optional: To support definitions for "greater than" or "less than," implement the <xref:System.IComparable%601> interface for your type, and also overload the [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) and [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) operators.</span></span>  
  
 <span data-ttu-id="5c702-133">次に示す最初の例は、クラスの実装です。</span><span class="sxs-lookup"><span data-stu-id="5c702-133">The first example that follows shows a class implementation.</span></span> <span data-ttu-id="5c702-134">2 番目の例は、構造体の実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c702-134">The second example shows a struct implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c702-135">例</span><span class="sxs-lookup"><span data-stu-id="5c702-135">Example</span></span>  
 <span data-ttu-id="5c702-136">次の例は、クラス (参照型) で値の等価性を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c702-136">The following example shows how to implement value equality in a class (reference type).</span></span>  
  
 <span data-ttu-id="5c702-137">[!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c702-137">[!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]</span></span>  
  
 <span data-ttu-id="5c702-138">クラス (参照型) の場合、両方の <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> メソッドの既定の実装で、参照の等価性の比較は実行されますが、値の等価性のチェックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="5c702-138">On classes (reference types), the default implementation of both <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> methods performs a reference equality comparison, not a value equality check.</span></span> <span data-ttu-id="5c702-139">実装が仮想メソッドをオーバーライドする場合、その目的は、仮想メソッドに値の等価性のセマンティクスを提供することです。</span><span class="sxs-lookup"><span data-stu-id="5c702-139">When an implementer overrides the virtual method, the purpose is to give it value equality semantics.</span></span>  
  
 <span data-ttu-id="5c702-140">`==` 演算子と `!=` 演算子は、オーバーロードされなくてもクラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c702-140">The `==` and `!=` operators can be used with classes even if the class does not overload them.</span></span> <span data-ttu-id="5c702-141">ただし、既定の動作として参照の等価性のチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="5c702-141">However, the default behavior is to perform a reference equality check.</span></span> <span data-ttu-id="5c702-142">クラスで `Equals` メソッドをオーバーロードする場合は、`==` 演算子と `!=` 演算子をオーバーロードすることをお勧めしますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="5c702-142">In a class, if you overload the `Equals` method, you should overload the `==` and `!=` operators, but it is not required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c702-143">例</span><span class="sxs-lookup"><span data-stu-id="5c702-143">Example</span></span>  
 <span data-ttu-id="5c702-144">次の例は、構造体 (値型) で値の等価性を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c702-144">The following example shows how to implement value equality in a struct (value type):</span></span>  
  
 <span data-ttu-id="5c702-145">[!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5c702-145">[!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]</span></span>  
  
 <span data-ttu-id="5c702-146">構造体の場合、<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> (<xref:System.ValueType?displayProperty=fullName> でオーバーライドされるバージョン) の既定の実装で、リフレクションを使用して値の等価性のチェックが実行され、型のすべてのフィールドの値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="5c702-146">For structs, the default implementation of <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> (which is the overridden version in <xref:System.ValueType?displayProperty=fullName>) performs a value equality check by using reflection to compare the values of every field in the type.</span></span> <span data-ttu-id="5c702-147">実装が構造体の仮想 `Equals` メソッドをオーバーライドする場合、その目的は、値の等価性のチェックをより効率的に実行することと、オプションで、構造体のフィールドまたはプロパティの一部のサブセットに基づいて比較を行うことです。</span><span class="sxs-lookup"><span data-stu-id="5c702-147">When an implementer overrides the virtual `Equals` method in a struct, the purpose is to provide a more efficient means of performing the value equality check and optionally to base the comparison on some subset of the struct's field or properties.</span></span>  
  
 <span data-ttu-id="5c702-148">[==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 演算子および [!=](../../../csharp/language-reference/operators/not-equal-operator.md) 演算子は、構造体が明示的にその演算子をオーバーロードしない限り、その構造体を操作できません。</span><span class="sxs-lookup"><span data-stu-id="5c702-148">The [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) and [!=](../../../csharp/language-reference/operators/not-equal-operator.md) operators cannot operate on a struct unless the struct explicitly overloads them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c702-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c702-149">See Also</span></span>  
 <span data-ttu-id="5c702-150">[等価比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="5c702-150">[Equality Comparisons](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md) </span></span>  
 [<span data-ttu-id="5c702-151">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5c702-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

