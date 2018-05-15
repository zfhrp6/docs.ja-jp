---
title: デリゲート (Visual Basic) の分散
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: d857f120be0fe810489ba69edb55af9cc0dd6940
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="244d5-102">デリゲート (Visual Basic) の分散</span><span class="sxs-lookup"><span data-stu-id="244d5-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="244d5-103">.NET framework 3.5 には、c# および Visual Basic でのすべてのデリゲートでのデリゲート型でメソッドのシグネチャの一致の分散のサポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="244d5-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="244d5-104">つまり、シグネチャが一致するメソッドだけでなく、デリゲート型で指定された型よりも強い派生型を返す (共変性) メソッドや、弱い派生型のパラメーターを受け取る (反変性) メソッドを、デリゲートに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="244d5-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="244d5-105">これには、汎用デリゲートと非汎用デリゲートの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="244d5-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="244d5-106">たとえば、次のコードについて考えます。このコードには、2 つのクラスと、汎用と非汎用の 2 つのデリゲートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="244d5-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="244d5-107">`SampleDelegate` 型または `SampleDelegate(Of A, R)` 型のデリゲートを作成する場合、そのデリゲートには、次のいずれかのメソッドを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="244d5-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="244d5-108">次のコード例は、メソッド シグネチャとデリゲート型の間の暗黙的な変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="244d5-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="244d5-109">例については、次を参照してください。[デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)と[Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)です。</span><span class="sxs-lookup"><span data-stu-id="244d5-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="244d5-110">ジェネリック型パラメーターの分散</span><span class="sxs-lookup"><span data-stu-id="244d5-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="244d5-111">.NET Framework 4 およびそれ以降の型がで必要と互いから継承されている場合、互いにさまざまな型のジェネリック型パラメーターで指定された汎用デリゲートを割り当てることができるように、デリゲートの間の暗黙的な変換が有効にできます。分散します。</span><span class="sxs-lookup"><span data-stu-id="244d5-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="244d5-112">暗黙的な変換を有効にするには、`in` キーワードまたは `out` キーワードを使用して、デリゲートでジェネリック パラメーターを共変または反変として明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="244d5-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="244d5-113">次のコード例は、共変のジェネリック型パラメーターが指定されたデリゲートを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="244d5-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="244d5-114">分散サポートのみを使用してメソッド シグネチャをデリゲート型に一致させ、`in` キーワードと `out` キーワードを使用しない場合、同等のラムダ式かメソッドを使用すれば、デリゲートをインスタンス化できることがありますが、デリゲートを別のデリゲートに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="244d5-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="244d5-115">次のコード例で`SampleGenericDelegate(Of String)`に明示的に変換できない`SampleGenericDelegate(Of Object)`ですが、`String`継承`Object`です。</span><span class="sxs-lookup"><span data-stu-id="244d5-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="244d5-116">この問題を修正するには、ジェネリック パラメーター `T` を `out` キーワードでマークします。</span><span class="sxs-lookup"><span data-stu-id="244d5-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="244d5-117">.NET Framework のバリアント型パラメーターが含まれる汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="244d5-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="244d5-118">.NET Framework 4 では、既存の複数の汎用デリゲートで、ジェネリック型パラメーターに対して分散サポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="244d5-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="244d5-119"><xref:System> 名前空間の `Action` デリゲート。<xref:System.Action%601>、<xref:System.Action%602> など</span><span class="sxs-lookup"><span data-stu-id="244d5-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="244d5-120"><xref:System> 名前空間の `Func` デリゲート。<xref:System.Func%601>、<xref:System.Func%602> など</span><span class="sxs-lookup"><span data-stu-id="244d5-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="244d5-121"><xref:System.Predicate%601> デリゲート</span><span class="sxs-lookup"><span data-stu-id="244d5-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="244d5-122"><xref:System.Comparison%601> デリゲート</span><span class="sxs-lookup"><span data-stu-id="244d5-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="244d5-123"><xref:System.Converter%602> デリゲート</span><span class="sxs-lookup"><span data-stu-id="244d5-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="244d5-124">詳細と例については、次を参照してください。 [Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)です。</span><span class="sxs-lookup"><span data-stu-id="244d5-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="244d5-125">汎用デリゲートのバリアント型パラメーターの宣言</span><span class="sxs-lookup"><span data-stu-id="244d5-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="244d5-126">汎用デリゲートに共変または反変のジェネリック型パラメーターがある場合、そのデリゲートは "*バリアント汎用デリゲート*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="244d5-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="244d5-127">汎用デリゲートのジェネリック型パラメーターを共変として宣言するには、`out` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="244d5-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="244d5-128">共変の型は、メソッドの戻り値の型としてのみ使用できます。メソッド引数の型として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="244d5-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="244d5-129">共変の汎用デリゲートを宣言する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="244d5-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 <span data-ttu-id="244d5-130">汎用デリゲートのジェネリック型パラメーターを反変として宣言するには、`in` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="244d5-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="244d5-131">反変の型は、メソッド引数の型としてのみ使用できます。メソッドの戻り値の型として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="244d5-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="244d5-132">反変の汎用デリゲートを宣言する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="244d5-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="244d5-133">`ByRef` Visual Basic でのパラメーターは、バリアント型としてマークできません。</span><span class="sxs-lookup"><span data-stu-id="244d5-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="244d5-134">同じデリゲートで、型パラメーターが異なる場合は、分散と共変性の両方をサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="244d5-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="244d5-135">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="244d5-135">This is shown in the following example.</span></span>  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="244d5-136">バリアント汎用デリゲートのインスタンス化と呼び出し</span><span class="sxs-lookup"><span data-stu-id="244d5-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="244d5-137">バリアント デリゲートのインスタンス化および呼び出しは、インバリアント デリゲートのインスタンス化および呼び出しと同様に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="244d5-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="244d5-138">次の例では、ラムダ式によってデリゲートをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="244d5-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="244d5-139">バリアント汎用デリゲートの結合</span><span class="sxs-lookup"><span data-stu-id="244d5-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="244d5-140">バリアント デリゲートの結合はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="244d5-140">You should not combine variant delegates.</span></span> <span data-ttu-id="244d5-141"><xref:System.Delegate.Combine%2A> メソッドはバリアント デリゲートの変換をサポートしていないため、デリゲートが厳密に同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="244d5-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="244d5-142">これにより、実行時例外を使用してデリゲートを結合するときに、<xref:System.Delegate.Combine%2A>メソッド (c# および Visual Basic) またはを使用して、`+`演算子 (c#)、次のコード例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="244d5-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="244d5-143">値型と参照型でのジェネリック型パラメーターの分散</span><span class="sxs-lookup"><span data-stu-id="244d5-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="244d5-144">ジェネリック型パラメーターの分散がサポートされるのは参照型だけです。</span><span class="sxs-lookup"><span data-stu-id="244d5-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="244d5-145">たとえば、`DVariant(Of Int)`に暗黙的に変換できない`DVariant(Of Object)`または`DVariant(Of Long)`整数が値型であるためです。</span><span class="sxs-lookup"><span data-stu-id="244d5-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="244d5-146">次の例は、値型ではジェネリック型パラメーターの分散がサポートされないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="244d5-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="244d5-147">Visual Basic の厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="244d5-147">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="244d5-148">厳密でないデリゲート変換より柔軟にデリゲート型でメソッドのシグネチャの一致を使用できます。</span><span class="sxs-lookup"><span data-stu-id="244d5-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="244d5-149">たとえば、これによりパラメーターの仕様を省略し、デリゲートにメソッドを割り当てるときに、関数の戻り値を省略できます。</span><span class="sxs-lookup"><span data-stu-id="244d5-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="244d5-150">詳細については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)です。</span><span class="sxs-lookup"><span data-stu-id="244d5-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244d5-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="244d5-151">See Also</span></span>  
 [<span data-ttu-id="244d5-152">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="244d5-152">Generics</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="244d5-153">Func および Action 汎用デリゲートでの分散の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="244d5-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
