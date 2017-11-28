---
title: "Override キーワードと New キーワードを使用する場合について (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b4d53f16f046839d56bc1dc37f7b2d8816c5956f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="16441-102">Override キーワードと New キーワードを使用する場合について (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="16441-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="16441-103">C# では、派生クラスのメソッドを基底クラスのメソッドと同じ名前にすることができます。</span><span class="sxs-lookup"><span data-stu-id="16441-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="16441-104">[new](../../../csharp/language-reference/keywords/new.md) および [override](../../../csharp/language-reference/keywords/override.md) キーワードを使って、メソッドでの処理を指定できます。</span><span class="sxs-lookup"><span data-stu-id="16441-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="16441-105">`override` 修飾子は基底クラスのメソッドを "*拡張*" し、`new` 修飾子は "*隠ぺい*" します。</span><span class="sxs-lookup"><span data-stu-id="16441-105">The `override` modifier *extends* the base class method, and the `new` modifier *hides* it.</span></span> <span data-ttu-id="16441-106">このトピックの例ではその違いを示します。</span><span class="sxs-lookup"><span data-stu-id="16441-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="16441-107">コンソール アプリケーションで、次の 2 つのクラス `BaseClass` と `DerivedClass` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="16441-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="16441-108">`DerivedClass` は `BaseClass` を継承します。</span><span class="sxs-lookup"><span data-stu-id="16441-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 <span data-ttu-id="16441-109">`Main` メソッドで、変数 `bc`、`dc`、`bcdc` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="16441-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
-   <span data-ttu-id="16441-110">`bc` は `BaseClass` 型であり、その値は `BaseClass` です。</span><span class="sxs-lookup"><span data-stu-id="16441-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
-   <span data-ttu-id="16441-111">`dc` は `DerivedClass` 型であり、その値は `DerivedClass` です。</span><span class="sxs-lookup"><span data-stu-id="16441-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
-   <span data-ttu-id="16441-112">`bcdc` は `BaseClass` 型であり、その値は `DerivedClass` です。</span><span class="sxs-lookup"><span data-stu-id="16441-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="16441-113">この変数には注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16441-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="16441-114">`bc` と `bcdc` は `BaseClass` 型なので、キャストを使わない限り、直接アクセスできるのは `Method1` だけです。</span><span class="sxs-lookup"><span data-stu-id="16441-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="16441-115">変数 `dc` は、`Method1` と `Method2` の両方にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="16441-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="16441-116">これらの関係を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="16441-116">These relationships are shown in the following code.</span></span>  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 <span data-ttu-id="16441-117">次に、以下の `Method2` メソッドを `BaseClass` に追加します。</span><span class="sxs-lookup"><span data-stu-id="16441-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="16441-118">このメソッドのシグネチャは、`DerivedClass` の `Method2` メソッドのシグネチャと一致します。</span><span class="sxs-lookup"><span data-stu-id="16441-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="16441-119">`BaseClass` に `Method2` メソッドを追加したので、次のコードに示すように、`BaseClass` の変数 `bc` および `bcdc` に 2 つめの呼び出しステートメントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="16441-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="16441-120">プロジェクトをビルドすると、`BaseClass` に `Method2` メソッドを追加したことで警告が発生するようになります。</span><span class="sxs-lookup"><span data-stu-id="16441-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="16441-121">警告の内容は、`DerivedClass` の `Method2` メソッドが `BaseClass` の `Method2` メソッドを隠ぺいしているというものです。</span><span class="sxs-lookup"><span data-stu-id="16441-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="16441-122">それが意図する結果である場合は、`Method2` の定義で `new` キーワードを使うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="16441-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="16441-123">または、どちらかの `Method2` メソッドの名前を変更して警告を解決することもできますが、実用的ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="16441-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="16441-124">`new` を追加する前に、プログラムを実行して、追加した呼び出しステートメントによって生成される出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="16441-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="16441-125">次のような結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16441-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="16441-126">`new` キーワードは、その出力を生成する関係を維持しますが、警告を抑制します。</span><span class="sxs-lookup"><span data-stu-id="16441-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="16441-127">`BaseClass` 型の変数は引き続き `BaseClass` のメンバーにアクセスし、`DerivedClass` 型の変数は引き続き最初に `DerivedClass` のメンバーにアクセスした後、`BaseClass` から継承されたメンバーを考慮します。</span><span class="sxs-lookup"><span data-stu-id="16441-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="16441-128">警告を抑制するには、次のコードで示すように、`DerivedClass` での `Method2` の定義に `new` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="16441-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="16441-129">修飾子を追加する位置は、`public` の前でも後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="16441-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="16441-130">もう一度プログラムを実行し、出力が変わらないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="16441-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="16441-131">また、警告が表示されなくなったことを確認します。</span><span class="sxs-lookup"><span data-stu-id="16441-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="16441-132">`new` を使うことにより、それによって修飾されるメンバーが基底クラスから継承されたメンバーを隠ぺいすることを了解していることを明示します。</span><span class="sxs-lookup"><span data-stu-id="16441-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="16441-133">継承による名前の非表示について詳しくは、「[new 修飾子](../../../csharp/language-reference/keywords/new-modifier.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16441-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="16441-134">この動作を `override` を使ったときの効果と比較するため、次のメソッドを `DerivedClass` に追加します。</span><span class="sxs-lookup"><span data-stu-id="16441-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="16441-135">`override` 修飾子を追加する位置は、`public` の前でも後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="16441-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="16441-136">`BaseClass` での `Method1` の定義に `virtual` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="16441-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="16441-137">`virtual` 修飾子を追加する位置は、`public` の前でも後でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="16441-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="16441-138">プロジェクトを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="16441-138">Run the project again.</span></span> <span data-ttu-id="16441-139">次の出力の最後の 2 行に特に注意してください。</span><span class="sxs-lookup"><span data-stu-id="16441-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="16441-140">`override` 修飾子を使うことで、`bcdc` は、`DerivedClass` で定義されている `Method1` メソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="16441-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="16441-141">通常、これは継承階層での必要な動作です。</span><span class="sxs-lookup"><span data-stu-id="16441-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="16441-142">派生クラスから作成される値を持つオブジェクトには、派生クラスで定義されているメソッドを使うことが必要とされます。</span><span class="sxs-lookup"><span data-stu-id="16441-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="16441-143">そのような動作は、`override` を使って基底クラスのメソッドを拡張することで実現できます。</span><span class="sxs-lookup"><span data-stu-id="16441-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="16441-144">ここまでの例をすべて含んだコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="16441-144">The following code contains the full example.</span></span>  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="16441-145">次の例では、異なるコンテキストでの同様の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="16441-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="16441-146">この例では、3 つのクラスが定義されています。基底クラス `Car` と、それから派生される 2 つのクラス `ConvertibleCar` と `Minivan` です。</span><span class="sxs-lookup"><span data-stu-id="16441-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="16441-147">基底クラスには、`DescribeCar` メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="16441-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="16441-148">このメソッドは、車の基本的な説明を表示した後、`ShowDetails` を呼び出して追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="16441-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="16441-149">これら 3 つのクラスのそれぞれで、`ShowDetails` メソッドが定義されています。</span><span class="sxs-lookup"><span data-stu-id="16441-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="16441-150">`new` 修飾子は、`ConvertibleCar` クラスで `ShowDetails` を定義するために使われています。</span><span class="sxs-lookup"><span data-stu-id="16441-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="16441-151">`override` 修飾子は、`Minivan` クラスで `ShowDetails` を定義するために使われています。</span><span class="sxs-lookup"><span data-stu-id="16441-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 <span data-ttu-id="16441-152">この例では、どちらのバージョンの `ShowDetails` が呼び出されるかをテストします。</span><span class="sxs-lookup"><span data-stu-id="16441-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="16441-153">次の `TestCars1` メソッドでは、各クラスのインスタンスを宣言した後、各インスタンスの `DescribeCar` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="16441-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 <span data-ttu-id="16441-154">`TestCars1` で生成される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16441-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="16441-155">`car2` の結果に特に注目してください。予測していた内容と違っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16441-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="16441-156">オブジェクトの型は `ConvertibleCar` ですが、`DescribeCar` は `ConvertibleCar` クラスで定義されているバージョンの `ShowDetails` にアクセスしていません。これは、このメソッドが、`override` 修飾子ではなく `new` 修飾子を使って宣言されているためです。</span><span class="sxs-lookup"><span data-stu-id="16441-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="16441-157">結果として、`ConvertibleCar` オブジェクトでは `Car` オブジェクトと同じ説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16441-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="16441-158">`Minivan` オブジェクトである `car3` の結果と比べてみてください。</span><span class="sxs-lookup"><span data-stu-id="16441-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="16441-159">この場合は、`Minivan` で宣言されている `ShowDetails` メソッドは、`Car` クラスで宣言されている `ShowDetails` メソッドをオーバーライドし、表示されるのはミニバンの説明です。</span><span class="sxs-lookup"><span data-stu-id="16441-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="16441-160">`TestCars2` は、`Car` 型のオブジェクトのリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="16441-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="16441-161">オブジェクトの値は、`Car`、`ConvertibleCar`、`Minivan` の各クラスからインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="16441-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="16441-162">`DescribeCar` は、リストの各要素に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="16441-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="16441-163">次のコードは、`TestCars2` の定義です。</span><span class="sxs-lookup"><span data-stu-id="16441-163">The following code shows the definition of `TestCars2`.</span></span>  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 <span data-ttu-id="16441-164">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16441-164">The following output is displayed.</span></span> <span data-ttu-id="16441-165">`TestCars1` によって表示される出力と同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="16441-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="16441-166">オブジェクトの型が `ConvertibleCar` であるか (`TestCars1` の場合)、`Car` であるか (`TestCars2` の場合) にかかわらず、`ConvertibleCar` クラスの `ShowDetails` メソッドは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="16441-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="16441-167">逆に、`car3` は、型が `Minivan` でも `Car` でも、`Minivan` クラスの `ShowDetails` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="16441-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="16441-168">メソッド `TestCars3` と `TestCars4` でこの例は終わりです。</span><span class="sxs-lookup"><span data-stu-id="16441-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="16441-169">これらのメソッドは、最初は型 `ConvertibleCar` および `Minivan` として宣言されているオブジェクトから (`TestCars3`)、次に型 `Car` として宣言されているオブジェクトから (`TestCars4`)、`ShowDetails` を直接呼び出します。</span><span class="sxs-lookup"><span data-stu-id="16441-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="16441-170">次のコードは、これら 2 つのメソッドの定義です。</span><span class="sxs-lookup"><span data-stu-id="16441-170">The following code defines these two methods.</span></span>  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 <span data-ttu-id="16441-171">これらのメソッドからは次のような出力が生成され、これはこのトピックの最初の例からの結果に対応します。</span><span class="sxs-lookup"><span data-stu-id="16441-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 <span data-ttu-id="16441-172">完全なプロジェクトとその出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="16441-172">The following code shows the complete project and its output.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="16441-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="16441-173">See Also</span></span>  
 [<span data-ttu-id="16441-174">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="16441-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="16441-175">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="16441-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="16441-176">Override キーワードと New キーワードによるバージョン管理</span><span class="sxs-lookup"><span data-stu-id="16441-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="16441-177">base</span><span class="sxs-lookup"><span data-stu-id="16441-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="16441-178">abstract</span><span class="sxs-lookup"><span data-stu-id="16441-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
