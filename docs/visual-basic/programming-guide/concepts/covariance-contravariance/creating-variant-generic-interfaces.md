---
title: "バリアント ジェネリック インターフェイス (Visual Basic) を作成する |Microsoft ドキュメント"
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
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a2cbf0a204a5a3af45f55a14c011518c7021f5b4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="creating-variant-generic-interfaces-visual-basic"></a><span data-ttu-id="43cc1-102">バリアント ジェネリック インターフェイス (Visual Basic) の作成</span><span class="sxs-lookup"><span data-stu-id="43cc1-102">Creating Variant Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="43cc1-103">共変性のインターフェイスのジェネリック型パラメーターを宣言するまたは反変です。</span><span class="sxs-lookup"><span data-stu-id="43cc1-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="43cc1-104">*ジェネリックの共変性*インターフェイス メソッドのジェネリック型パラメーターで定義されているよりも戻り値の型の派生を許可します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="43cc1-105">*反変性*インターフェイス メソッドには、ジェネリック パラメーターで指定されているよりも弱い派生の引数の型を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="43cc1-106">ジェネリック インターフェイスを持つ共変または反変のジェネリック型パラメーターと呼ばれる*バリアント*します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43cc1-107">.NET framework 4 には、いくつかの既存のジェネリック インターフェイスの分散のサポートが導入されました。</span><span class="sxs-lookup"><span data-stu-id="43cc1-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="43cc1-108">.NET Framework のバリアントのインターフェイスの一覧で、次を参照してください。[ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="43cc1-109">バリアント ジェネリック インターフェイスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="43cc1-110">バリアント ジェネリック インターフェイスを宣言するにを使用して、`in`と`out`ジェネリック型パラメーターのキーワードです。</span><span class="sxs-lookup"><span data-stu-id="43cc1-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43cc1-111"> `ByRef`Visual Basic でのパラメーターは、バリアント型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-111"> `ByRef` parameters in Visual Basic cannot be variant.</span></span> <span data-ttu-id="43cc1-112">また、値型では、分散はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="43cc1-113">宣言するジェネリック型パラメーター共変性を使用して、`out`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="43cc1-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="43cc1-114">共変の型は、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="43cc1-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="43cc1-115">型がインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用できません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="43cc1-116">これで、次の例に示すは種類`R`共変で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="43cc1-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     <span data-ttu-id="43cc1-117">この規則には例外が&1; つあります。</span><span class="sxs-lookup"><span data-stu-id="43cc1-117">There is one exception to this rule.</span></span> <span data-ttu-id="43cc1-118">メソッド パラメーターとして反変のジェネリック デリゲートをした場合は、デリゲートのジェネリック型パラメーターとして型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="43cc1-119">型でその例を示します`R`次の例です。</span><span class="sxs-lookup"><span data-stu-id="43cc1-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="43cc1-120">詳細については、次を参照してください。[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)と[用 Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-120">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   <span data-ttu-id="43cc1-121">種類は、インターフェイス メソッドのジェネリック制約として使用されません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="43cc1-122">これは、次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-122">This is illustrated in the following code.</span></span>  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 <span data-ttu-id="43cc1-123">使用してジェネリック型パラメーターの反変性を宣言することができます、`in`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="43cc1-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="43cc1-124">反変の型は、インターフェイス メソッドの戻り値の型としてではなく、メソッド引数の型としてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="43cc1-125">反変の型は、ジェネリック制約にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="43cc1-126">次のコードでは、反変のインターフェイスを宣言し、そのメソッドのいずれかに汎用的な制約を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 <span data-ttu-id="43cc1-127">次のコード例のようには、同じインターフェイスが異なる型のパラメーターの共変性と反変性の両方をサポートすることもです。</span><span class="sxs-lookup"><span data-stu-id="43cc1-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 <span data-ttu-id="43cc1-128">Visual Basic では、デリゲート型を指定することがなくバリアント インターフェイスのイベントを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-128">In Visual Basic, you can't declare events in variant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="43cc1-129">また、variant インターフェイスがクラス、列挙、または構造体で入れ子になっている必要しますが、インターフェイスを入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-129">Also, a variant interface can't have nested classes, enums, or structures, but it can have nested interfaces.</span></span> <span data-ttu-id="43cc1-130">これは、次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-130">This is illustrated in the following code.</span></span>  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="43cc1-131">バリアント ジェネリック インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-131">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="43cc1-132">クラスのバリアント ジェネリック インターフェイスを実装するには、ロケールに依存しないインターフェイスに使用されるのと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-132">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="43cc1-133">次のコード例では、ジェネリック クラスに、共変のインターフェイスを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-133">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 <span data-ttu-id="43cc1-134">バリアント型のインターフェイスを実装するクラスは変化しません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-134">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="43cc1-135">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-135">For example, consider the following code.</span></span>  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="43cc1-136">バリアント ジェネリック インターフェイスの拡張</span><span class="sxs-lookup"><span data-stu-id="43cc1-136">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="43cc1-137">使用する必要があるバリアント ジェネリック インターフェイスを拡張するときに、`in`と`out`派生インターフェイスで変性をサポートするかどうかを明示的に指定するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="43cc1-137">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="43cc1-138">コンパイラは、拡張されているインターフェイスからの差異を推論できません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-138">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="43cc1-139">たとえば、次のインターフェイスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="43cc1-139">For example, consider the following interfaces.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="43cc1-140">`Invariant(Of T)`インターフェイス、ジェネリック型パラメーター`T`バリアントで`IExtCovariant (Of Out T)`型パラメーターが共変で両方のインターフェイスは、同じインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-140">In the `Invariant(Of T)` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant (Of Out T)`the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="43cc1-141">同じ規則には、反変のジェネリック型パラメーターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-141">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="43cc1-142">ジェネリック型パラメーターで、インターフェイスを拡張するインターフェイスを作成する`T`が共変とインターフェイスのジェネリック型パラメーターの場合の反変、拡張の場合は、インターフェイス`T`バリアント型ではありません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-142">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="43cc1-143">これは、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-143">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 <span data-ttu-id="43cc1-144">ただし、ジェネリック型パラメーター`T`は&1; つのインターフェイスの宣言と共変は宣言できません反変拡張するインターフェイスまたはその逆です。</span><span class="sxs-lookup"><span data-stu-id="43cc1-144">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="43cc1-145">これは、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-145">This is illustrated in the following code example.</span></span>  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="43cc1-146">あいまいさを回避します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-146">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="43cc1-147">バリアント ジェネリック インターフェイスを実装するときに分散できる場合もありますわかりにくくなる場合します。</span><span class="sxs-lookup"><span data-stu-id="43cc1-147">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="43cc1-148">このような状況は回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43cc1-148">This should be avoided.</span></span>  
  
 <span data-ttu-id="43cc1-149">たとえば、1 つのクラスで明示的に別のジェネリック型パラメーターを持つ同じバリアント ジェネリック インターフェイスを実装する場合のあいまいさを作成できます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-149">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="43cc1-150">コンパイラ エラーは発生しませんが、ここでは、するインターフェイスの実装は、実行時に選択が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="43cc1-150">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="43cc1-151">これにより、コードで軽度のバグです。</span><span class="sxs-lookup"><span data-stu-id="43cc1-151">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="43cc1-152">次のコード例を検討してください。</span><span class="sxs-lookup"><span data-stu-id="43cc1-152">Consider the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43cc1-153">`Option Strict Off`、Visual Basic では、あいまいなインターフェイスの実装がある場合に、コンパイラの警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-153">With `Option Strict Off`, Visual Basic generates a compiler warning when there is an ambiguous interface implementation.</span></span> <span data-ttu-id="43cc1-154">`Option Strict On`、Visual Basic コンパイラ エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="43cc1-154">With `Option Strict On`, Visual Basic generates a compiler error.</span></span>  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 <span data-ttu-id="43cc1-155">この例では指定されていないか、`pets.GetEnumerator`メソッドによって選択される`Cat`と`Dog`です。</span><span class="sxs-lookup"><span data-stu-id="43cc1-155">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="43cc1-156">これにより、コードで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="43cc1-156">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43cc1-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="43cc1-157">See Also</span></span>  
 <span data-ttu-id="43cc1-158">[ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="43cc1-158">[Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) </span></span>  
<span data-ttu-id="43cc1-159"> [Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="43cc1-159"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
