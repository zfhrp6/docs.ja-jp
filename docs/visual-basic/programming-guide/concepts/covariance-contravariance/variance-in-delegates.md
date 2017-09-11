---
title: "デリゲート (Visual Basic) の分散 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="96d19-102">デリゲート (Visual Basic) の分散</span><span class="sxs-lookup"><span data-stu-id="96d19-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="96d19-103">.NET framework 3.5 には、c# および Visual Basic でのすべてのデリゲートでのデリゲート型でメソッドのシグネチャに一致する、変性のサポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="96d19-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="96d19-104">割り当てることができるこの手段は、一致するシグネチャがあるメソッドだけでなくよりも強い派生型 (共変性) またはデリゲート型で指定されているよりも弱い派生型 (反変性) のパラメーターを受け取るを返すメソッドも代行させます。</span><span class="sxs-lookup"><span data-stu-id="96d19-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="96d19-105">これには、ジェネリックと非ジェネリック デリゲートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="96d19-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="96d19-106">たとえば、次のコードは、2 つのクラスと&2; つのデリゲート: ジェネリックと非ジェネリックです。</span><span class="sxs-lookup"><span data-stu-id="96d19-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="96d19-107">デリゲートを作成するときに、`SampleDelegate`または`SampleDelegate(Of A, R)`型、それらのデリゲートを次のいずれかに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="96d19-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 <span data-ttu-id="96d19-108">次のコード例は、メソッド シグネチャとデリゲート型の間の暗黙的な変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="96d19-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 <span data-ttu-id="96d19-109">例については、次を参照してください。[デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)と[用 Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。</span><span class="sxs-lookup"><span data-stu-id="96d19-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="96d19-110">ジェネリック型パラメーターの分散</span><span class="sxs-lookup"><span data-stu-id="96d19-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="96d19-111">.NET Framework 4 およびそれ以降は、分散に必要な個々 の型が継承されている場合、相互にジェネリック型パラメーターで指定された別の型を持つ汎用デリゲートを割り当てることができるように、デリゲートの間の暗黙的な変換を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="96d19-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="96d19-112">暗黙的な変換を有効にするのには、共変としてのデリゲートのジェネリック パラメーター明示的に宣言する必要がありますと反変性を使用して、`in`または`out`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="96d19-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="96d19-113">次のコード例では、共変のジェネリック型パラメーターを持つデリゲートを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="96d19-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 <span data-ttu-id="96d19-114">一致するようにのみ、変性のサポートを使用する場合、メソッドのシグネチャはデリゲート型し、使用しないでください、`in`と`out`キーワード、同一のラムダ式またはメソッドを持つデリゲートをインスタンス化することもありますが、別に&1; つのデリゲートを割り当てることはできませんを見つけることがあります。</span><span class="sxs-lookup"><span data-stu-id="96d19-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="96d19-115">次のコード例では`SampleGenericDelegate(Of String)`に明示的に変換できない`SampleGenericDelegate(Of Object)`いますが、`String`継承`Object`します。</span><span class="sxs-lookup"><span data-stu-id="96d19-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="96d19-116">この問題を解決するには、ジェネリック パラメーターをマークすることによって`T`で、`out`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="96d19-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="96d19-117">.NET framework の型パラメーターをバリアントを持つ汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="96d19-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="96d19-118">.NET framework 4 には、いくつかの既存の汎用デリゲートのジェネリック型パラメーターの分散のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="96d19-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="96d19-119">`Action`デリゲート、<xref:System>名前空間、たとえば、<xref:System.Action%601>と<xref:System.Action%602></xref:System.Action%602></xref:System.Action%601></xref:System></span><span class="sxs-lookup"><span data-stu-id="96d19-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="96d19-120">`Func`デリゲート、<xref:System>名前空間、たとえば、<xref:System.Func%601>と<xref:System.Func%602></xref:System.Func%602></xref:System.Func%601></xref:System></span><span class="sxs-lookup"><span data-stu-id="96d19-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="96d19-121"><xref:System.Predicate%601>委任します。</xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="96d19-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="96d19-122"><xref:System.Comparison%601>委任します。</xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="96d19-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="96d19-123"><xref:System.Converter%602>委任します。</xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="96d19-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="96d19-124">詳細と例については、次を参照してください。[用 Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。</span><span class="sxs-lookup"><span data-stu-id="96d19-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="96d19-125">汎用デリゲートのバリアント型パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="96d19-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="96d19-126">汎用デリゲートは共変または反変のジェネリック型パラメーター、そのことができますとして参照される場合、*バリアント汎用デリゲート*します。</span><span class="sxs-lookup"><span data-stu-id="96d19-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="96d19-127">宣言するジェネリック型パラメーター汎用デリゲートの共変性を使用して、`out`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="96d19-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="96d19-128">共変の型は、メソッド引数の型ではなく、メソッドの戻り値の型としてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="96d19-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="96d19-129">次のコード例では、共変のジェネリック デリゲートを宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="96d19-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
<span data-ttu-id="96d19-130"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="96d19-130"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="96d19-131">汎用デリゲートのジェネリック型パラメーターの反変性を宣言するにを使用して、`in`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="96d19-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="96d19-132">反変の型は、メソッドの戻り値の型としてではなく、メソッド引数の型としてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="96d19-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="96d19-133">次のコード例では、反変のジェネリック デリゲートを宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="96d19-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
<span data-ttu-id="96d19-134"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="96d19-134"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
> <span data-ttu-id="96d19-135"> `ByRef`Visual Basic でのパラメーターは、バリアント型としてマークすることはできません。</span><span class="sxs-lookup"><span data-stu-id="96d19-135"> `ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="96d19-136">異なる型のパラメーターが、同じデリゲート内での分散とジェネリックの共変性の両方をサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="96d19-136">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="96d19-137">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="96d19-137">This is shown in the following example.</span></span>  
  
<span data-ttu-id="96d19-138"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="96d19-138"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="96d19-139">インスタンス化とバリアント汎用デリゲートの呼び出し</span><span class="sxs-lookup"><span data-stu-id="96d19-139">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="96d19-140">インスタンス化し、インスタンス化し、ロケールに依存しないデリゲートの呼び出しと同様、バリアント型のデリゲートを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="96d19-140">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="96d19-141">次の例では、ラムダ式によって、デリゲートがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="96d19-141">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
<span data-ttu-id="96d19-142"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="96d19-142"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="96d19-143">バリアント汎用デリゲートを組み合わせる</span><span class="sxs-lookup"><span data-stu-id="96d19-143">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="96d19-144">バリアント型のデリゲートを結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96d19-144">You should not combine variant delegates.</span></span> <span data-ttu-id="96d19-145"><xref:System.Delegate.Combine%2A>メソッド variant デリゲート変換はサポートされないため、まったく同じ型であるデリゲートが必要です</xref:System.Delegate.Combine%2A>。</span><span class="sxs-lookup"><span data-stu-id="96d19-145">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="96d19-146">これにより、実行時に例外を使用してデリゲートを結合するときに、<xref:System.Delegate.Combine%2A>メソッド (c# および Visual Basic) またはを使用して、 `+` (C# の場合)、次のコード例に示す演算子</xref:System.Delegate.Combine%2A>。</span><span class="sxs-lookup"><span data-stu-id="96d19-146">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
<span data-ttu-id="96d19-147"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="96d19-147"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="96d19-148">値と参照型のジェネリック型パラメーターの分散</span><span class="sxs-lookup"><span data-stu-id="96d19-148">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="96d19-149">ジェネリック型パラメーターの分散は参照型のみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="96d19-149">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="96d19-150">たとえば、`DVariant(Of Int)`に暗黙的に変換できない`DVariant(Of Object)`または`DVariant(Of Long)`整数が値型であるためです。</span><span class="sxs-lookup"><span data-stu-id="96d19-150">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="96d19-151">次の例では、その差異でジェネリック型パラメーターはサポートされていません値型です。</span><span class="sxs-lookup"><span data-stu-id="96d19-151">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="96d19-152">Visual Basic での厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="96d19-152">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="96d19-153">厳密でないデリゲート変換によりより柔軟にデリゲート型でメソッド署名を照合できます。</span><span class="sxs-lookup"><span data-stu-id="96d19-153">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="96d19-154">たとえば、パラメーターの指定を省略してメソッドをデリゲートに割り当てるときに、関数の戻り値を省略できます。</span><span class="sxs-lookup"><span data-stu-id="96d19-154">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="96d19-155">詳細については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。</span><span class="sxs-lookup"><span data-stu-id="96d19-155">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d19-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="96d19-156">See Also</span></span>  
 <span data-ttu-id="96d19-157">[ジェネリック](https://msdn.microsoft.com/library/ms172192) </span><span class="sxs-lookup"><span data-stu-id="96d19-157">[Generics](https://msdn.microsoft.com/library/ms172192) </span></span>  
<span data-ttu-id="96d19-158"> [Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="96d19-158"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
