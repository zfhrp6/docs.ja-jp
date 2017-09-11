---
title: "out (ジェネリック修飾子) (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
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
ms.sourcegitcommit: 775e4512a5ff31c7059961f6332c6bdc0dc5247a
ms.openlocfilehash: a560a0307723d32750a7e26ad4ee1afec360a849
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="f7316-102">out (ジェネリック修飾子) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f7316-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="f7316-103">ジェネリック型パラメーターの `out` キーワードは、型パラメーターが共変であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7316-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="f7316-104">`out` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7316-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="f7316-105">共変性は、ジェネリック パラメーターによって指定された型よりも強い派生型を使用できるようにする機能です。</span><span class="sxs-lookup"><span data-stu-id="f7316-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="f7316-106">これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。</span><span class="sxs-lookup"><span data-stu-id="f7316-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="f7316-107">共変性および反変性は参照型ではサポートされますが、値の型ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f7316-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="f7316-108">共変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、型パラメーターによって指定された型よりも強い派生型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="f7316-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="f7316-109">たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IEnumerable%601> では T 型が共変なので、特別な変換メソッドを使用しなくても `IEnumerabe(Of String)` 型のオブジェクトを `IEnumerable(Of Object)` 型のオブジェクトに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f7316-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="f7316-110">共変のデリゲートには、型は同じでありながらより強い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f7316-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="f7316-111">詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7316-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7316-112">例</span><span class="sxs-lookup"><span data-stu-id="f7316-112">Example</span></span>  
 <span data-ttu-id="f7316-113">次の例では、共変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7316-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="f7316-114">また、共変のインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="f7316-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 <span data-ttu-id="f7316-115">[!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f7316-115">[!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]</span></span>  
  
 <span data-ttu-id="f7316-116">ジェネリック インターフェイスでは、次の条件を満たす場合に型パラメーターを共変として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="f7316-116">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="f7316-117">型パラメーターがインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用されない。</span><span class="sxs-lookup"><span data-stu-id="f7316-117">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7316-118">この規則には例外が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="f7316-118">There is one exception to this rule.</span></span> <span data-ttu-id="f7316-119">共変のインターフェイスで反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、共変の型をこのデリゲートのジェネリック型パラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7316-119">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="f7316-120">共変および反変の汎用デリゲートの詳細については、「[デリゲートの分散](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)」および「[Func および Action 汎用デリゲートでの分散の使用](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7316-120">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) and [Using Variance for Func and Action Generic Delegates](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).</span></span>  
  
-   <span data-ttu-id="f7316-121">型パラメーターがインターフェイス メソッドのジェネリック制約として使用されない。</span><span class="sxs-lookup"><span data-stu-id="f7316-121">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7316-122">例</span><span class="sxs-lookup"><span data-stu-id="f7316-122">Example</span></span>  
 <span data-ttu-id="f7316-123">次の例では、共変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7316-123">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="f7316-124">また、デリゲート型を暗黙的に変換する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="f7316-124">It also shows how to implicitly convert delegate types.</span></span>  
  
 <span data-ttu-id="f7316-125">[!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f7316-125">[!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]</span></span>  
  
 <span data-ttu-id="f7316-126">汎用デリゲートでは、メソッドの戻り値の型としてのみ使用され、メソッド引数には使用されない型を共変として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="f7316-126">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f7316-127">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f7316-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f7316-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7316-128">See Also</span></span>  
 <span data-ttu-id="f7316-129">[ジェネリック インターフェイスの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="f7316-129">[Variance in Generic Interfaces](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) </span></span>  
 <span data-ttu-id="f7316-130">[in](../../../csharp/language-reference/keywords/in-generic-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="f7316-130">[in](../../../csharp/language-reference/keywords/in-generic-modifier.md) </span></span>  
 [<span data-ttu-id="f7316-131">修飾子</span><span class="sxs-lookup"><span data-stu-id="f7316-131">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

