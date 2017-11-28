---
title: "in (ジェネリック修飾子) (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="8bce6-102">in (ジェネリック修飾子) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8bce6-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="8bce6-103">ジェネリック型パラメーターの `in` キーワードは、型パラメーターが反変であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bce6-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="8bce6-104">`in` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8bce6-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="8bce6-105">反変性は、ジェネリック パラメーターによって指定された型よりも弱い派生型を使用できるようにする機能です。</span><span class="sxs-lookup"><span data-stu-id="8bce6-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="8bce6-106">これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。</span><span class="sxs-lookup"><span data-stu-id="8bce6-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="8bce6-107">ジェネリック型パラメーターの共変性および反変性は参照型ではサポートされますが、値型ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8bce6-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="8bce6-108">型をジェネリック インターフェイスまたはデリゲートで反変として宣言できるのは、メソッド引数の型としてのみ使用され、メソッドの戻り値の型としては使用されない場合です。</span><span class="sxs-lookup"><span data-stu-id="8bce6-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="8bce6-109">`Ref` パラメーターと `out` パラメーターをバリアントにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8bce6-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="8bce6-110">反変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、インターフェイス型パラメーターによって指定された型よりも弱い派生型の引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8bce6-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="8bce6-111">たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IComparer%601> インターフェイスでは T 型が反変なので、`Employee` が `Person` を継承する場合、特別な変換メソッドを使用しなくても `IComparer(Of Person)` 型のオブジェクトを `IComparer(Of Employee)` 型のオブジェクトに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8bce6-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="8bce6-112">反変のデリゲートには、型は同じでありながらより弱い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8bce6-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="8bce6-113">詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8bce6-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bce6-114">例</span><span class="sxs-lookup"><span data-stu-id="8bce6-114">Example</span></span>  
 <span data-ttu-id="8bce6-115">次の例では、反変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8bce6-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="8bce6-116">また、このインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="8bce6-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8bce6-117">例</span><span class="sxs-lookup"><span data-stu-id="8bce6-117">Example</span></span>  
 <span data-ttu-id="8bce6-118">次の例では、反変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8bce6-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="8bce6-119">また、デリゲート型を暗黙的に変換する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="8bce6-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8bce6-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="8bce6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8bce6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bce6-121">See Also</span></span>  
 [<span data-ttu-id="8bce6-122">out</span><span class="sxs-lookup"><span data-stu-id="8bce6-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="8bce6-123">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="8bce6-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="8bce6-124">修飾子</span><span class="sxs-lookup"><span data-stu-id="8bce6-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
