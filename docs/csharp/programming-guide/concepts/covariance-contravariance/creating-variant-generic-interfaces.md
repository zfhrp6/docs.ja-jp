---
title: バリアント ジェネリック インターフェイスの作成 (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 882bd0aa4497a99b2cf80e96f13f433ae74aad59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323740"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="d065d-102">バリアント ジェネリック インターフェイスの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="d065d-102">Creating Variant Generic Interfaces (C#)</span></span>
<span data-ttu-id="d065d-103">インターフェイスのジェネリック型パラメーターは、共変または反変として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d065d-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="d065d-104">"*共変性*" により、インターフェイス メソッドの戻り値の型の派生を、ジェネリック型パラメーターで定義されている型よりも強くすることができます。</span><span class="sxs-lookup"><span data-stu-id="d065d-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="d065d-105">"*反変性*" により、インターフェイス メソッドの引数の型の派生を、ジェネリック パラメーターで指定されている型よりも弱くすることができます。</span><span class="sxs-lookup"><span data-stu-id="d065d-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="d065d-106">共変または反変のジェネリック型パラメーターを持つジェネリック インターフェイスは、"*バリアント*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d065d-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d065d-107">.NET Framework 4 では、既存のいくつかのジェネリック インターフェイスに対して、変性のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="d065d-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="d065d-108">.NET Framework のバリアント インターフェイスの一覧については、「[ジェネリック インターフェイスの分散 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d065d-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="d065d-109">バリアント ジェネリック インターフェイスの宣言</span><span class="sxs-lookup"><span data-stu-id="d065d-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="d065d-110">バリアント ジェネリック インターフェイスは、ジェネリック型パラメーターの `in` キーワードと `out` キーワードを使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d065d-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d065d-111">C# の `ref`、`in`、`out` パラメーターは、バリアントにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d065d-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="d065d-112">また、値の型も変性をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d065d-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="d065d-113">ジェネリック型パラメーターを共変として宣言するには、`out` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d065d-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="d065d-114">共変の型は、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="d065d-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="d065d-115">型がインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用されない。</span><span class="sxs-lookup"><span data-stu-id="d065d-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="d065d-116">この例を以下に示します。ここでは、型 `R` が共変として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="d065d-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     <span data-ttu-id="d065d-117">この規則には例外が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="d065d-117">There is one exception to this rule.</span></span> <span data-ttu-id="d065d-118">反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、型をデリゲートのジェネリック型パラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="d065d-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="d065d-119">次の例では、型 `R` によって示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="d065d-120">詳細については、「[デリゲートの分散 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」および「[Func および Action 汎用デリゲートでの分散の使用 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d065d-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   <span data-ttu-id="d065d-121">型がインターフェイス メソッドのジェネリック制約として使用されない。</span><span class="sxs-lookup"><span data-stu-id="d065d-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="d065d-122">これを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-122">This is illustrated in the following code.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 <span data-ttu-id="d065d-123">ジェネリック型パラメーターを反変として宣言するには、`in` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d065d-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="d065d-124">反変の型は、メソッド引数の型としてのみ使用でき、インターフェイス メソッドの戻り値の型として使用できません。</span><span class="sxs-lookup"><span data-stu-id="d065d-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="d065d-125">また、反変の型はジェネリック制約にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d065d-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="d065d-126">次のコードでは、反変のインターフェイスを宣言し、そのメソッドの 1 つにジェネリック制約を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 <span data-ttu-id="d065d-127">次のコード例に示すように、同一インターフェイス内の異なる型パラメーターで、共変性と反変性の両方をサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d065d-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="d065d-128">バリアント ジェネリック インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="d065d-128">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="d065d-129">バリアント ジェネリック インターフェイスをクラスに実装する場合は、インバリアント インターフェイスに使用するのと同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d065d-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="d065d-130">次のコード例では、共変のインターフェイスをジェネリック クラスに実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
```csharp  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 <span data-ttu-id="d065d-131">バリアント インターフェイスを実装するクラスは不変です。</span><span class="sxs-lookup"><span data-stu-id="d065d-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="d065d-132">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-132">For example, consider the following code.</span></span>  
  
```csharp  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="d065d-133">バリアント ジェネリック インターフェイスの拡張</span><span class="sxs-lookup"><span data-stu-id="d065d-133">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="d065d-134">バリアント ジェネリック インターフェイスを拡張するときは、`in` キーワードと `out` キーワードを使用して、派生インターフェイスで変性をサポートするかどうかを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d065d-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="d065d-135">コンパイラでは、拡張されているインターフェイスからの変性の推論は行われません。</span><span class="sxs-lookup"><span data-stu-id="d065d-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="d065d-136">たとえば、次のようなインターフェイスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="d065d-136">For example, consider the following interfaces.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 <span data-ttu-id="d065d-137">`IInvariant<T>` インターフェイスのジェネリック型パラメーター `T` は不変であるのに対して、`IExtCovariant<out T>` の型パラメーターは共変ですが、どちらのインターフェイスでも同じインターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="d065d-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="d065d-138">これと同じ規則が、反変のジェネリック型パラメーターにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="d065d-138">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="d065d-139">拡張インターフェイスのジェネリック型パラメーター `T` が不変であれば、ジェネリック型パラメーター `T` が共変のインターフェイスと反変のインターフェイスの両方を拡張する 1 つのインターフェイスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d065d-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="d065d-140">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-140">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 <span data-ttu-id="d065d-141">ただし、一方のインターフェイスでジェネリック型パラメーター `T` が共変として宣言されている場合は、それを拡張インターフェイスで反変として宣言することはできません。その逆についても同様です。</span><span class="sxs-lookup"><span data-stu-id="d065d-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="d065d-142">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="d065d-142">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="d065d-143">あいまいさの回避</span><span class="sxs-lookup"><span data-stu-id="d065d-143">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="d065d-144">バリアント ジェネリック インターフェイスの実装時には、変性によってあいまいさが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d065d-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="d065d-145">このような状況は回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d065d-145">This should be avoided.</span></span>  
  
 <span data-ttu-id="d065d-146">たとえば、同一のバリアント ジェネリック インターフェイスを、異なるジェネリック型パラメーターを使用して 1 つのクラスに明示的に実装すると、あいまいさが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d065d-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="d065d-147">この場合、コンパイラでエラーは生成されませんが、実行時にどのインターフェイスの実装が選択されるかは明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="d065d-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="d065d-148">これにより、コードで特定しにくいバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d065d-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="d065d-149">次のコード例について考えます。</span><span class="sxs-lookup"><span data-stu-id="d065d-149">Consider the following code example.</span></span>  
  
```csharp  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 <span data-ttu-id="d065d-150">この例では、`pets.GetEnumerator` メソッドで `Cat` と `Dog` がどのように選択されるかが明らかではありません。</span><span class="sxs-lookup"><span data-stu-id="d065d-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="d065d-151">そのため、コードで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d065d-151">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d065d-152">参照</span><span class="sxs-lookup"><span data-stu-id="d065d-152">See Also</span></span>  
 [<span data-ttu-id="d065d-153">ジェネリック インターフェイスの分散 (C#)</span><span class="sxs-lookup"><span data-stu-id="d065d-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="d065d-154">Func および Action 汎用デリゲートでの分散の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="d065d-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
