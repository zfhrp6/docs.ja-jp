---
title: out (ジェネリック修飾子) (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269615"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="d92c7-102">out (ジェネリック修飾子) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d92c7-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="d92c7-103">ジェネリック型パラメーターの `out` キーワードは、型パラメーターが共変であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d92c7-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="d92c7-104">`out` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="d92c7-105">共変性は、ジェネリック パラメーターによって指定された型よりも強い派生型を使用できるようにする機能です。</span><span class="sxs-lookup"><span data-stu-id="d92c7-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="d92c7-106">これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。</span><span class="sxs-lookup"><span data-stu-id="d92c7-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="d92c7-107">共変性および反変性は参照型ではサポートされますが、値の型ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d92c7-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="d92c7-108">共変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、型パラメーターによって指定された型よりも強い派生型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="d92c7-109">たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IEnumerable%601> では T 型が共変なので、特別な変換メソッドを使用しなくても `IEnumerable(Of String)` 型のオブジェクトを `IEnumerable(Of Object)` 型のオブジェクトに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="d92c7-110">共変のデリゲートには、型は同じでありながらより強い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="d92c7-111">詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92c7-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d92c7-112">例</span><span class="sxs-lookup"><span data-stu-id="d92c7-112">Example</span></span>  
 <span data-ttu-id="d92c7-113">次の例では、共変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d92c7-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="d92c7-114">また、共変のインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="d92c7-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="d92c7-115">ジェネリック インターフェイスでは、次の条件を満たす場合に型パラメーターを共変として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="d92c7-116">型パラメーターがインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用されない。</span><span class="sxs-lookup"><span data-stu-id="d92c7-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d92c7-117">この規則には例外が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="d92c7-117">There is one exception to this rule.</span></span> <span data-ttu-id="d92c7-118">共変のインターフェイスで反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、共変の型をこのデリゲートのジェネリック型パラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="d92c7-119">共変および反変の汎用デリゲートの詳細については、「[デリゲートの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」および「[Func および Action 汎用デリゲートでの分散の使用](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d92c7-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="d92c7-120">型パラメーターがインターフェイス メソッドのジェネリック制約として使用されない。</span><span class="sxs-lookup"><span data-stu-id="d92c7-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d92c7-121">例</span><span class="sxs-lookup"><span data-stu-id="d92c7-121">Example</span></span>  
 <span data-ttu-id="d92c7-122">次の例では、共変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d92c7-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="d92c7-123">また、デリゲート型を暗黙的に変換する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="d92c7-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="d92c7-124">汎用デリゲートでは、メソッドの戻り値の型としてのみ使用され、メソッド引数には使用されない型を共変として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d92c7-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d92c7-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d92c7-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d92c7-126">参照</span><span class="sxs-lookup"><span data-stu-id="d92c7-126">See Also</span></span>  
 [<span data-ttu-id="d92c7-127">ジェネリック インターフェイスの分散</span><span class="sxs-lookup"><span data-stu-id="d92c7-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="d92c7-128">in</span><span class="sxs-lookup"><span data-stu-id="d92c7-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="d92c7-129">修飾子</span><span class="sxs-lookup"><span data-stu-id="d92c7-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
