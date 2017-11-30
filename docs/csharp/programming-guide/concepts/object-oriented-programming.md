---
title: "オブジェクト指向プログラミング (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a7f30293bb2d50981353badfb7e373b60dcfeec
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="b2485-102">オブジェクト指向プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="b2485-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="b2485-103">C# は、カプセル化、継承、ポリモーフィズムなど、オブジェクト指向プログラミングを完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="b2485-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="b2485-104">"*カプセル化*" とは、関連するプロパティ、メソッド、およびその他のメンバーのグループが 1 つの単位またはオブジェクトとして扱われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b2485-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="b2485-105">"*継承*" は、既存のクラスに基づいて新しいクラスを作成する機能です。</span><span class="sxs-lookup"><span data-stu-id="b2485-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="b2485-106">"*ポリモーフィズム*" とは、同じプロパティまたはメソッドを異なる方法で実装している複数のクラスを、交換して使用できることです。</span><span class="sxs-lookup"><span data-stu-id="b2485-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="b2485-107">このセクションでは、次の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2485-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="b2485-108">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b2485-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="b2485-109">クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="b2485-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="b2485-110">プロパティとフィールド</span><span class="sxs-lookup"><span data-stu-id="b2485-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="b2485-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="b2485-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="b2485-112">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b2485-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="b2485-113">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="b2485-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="b2485-114">イベント</span><span class="sxs-lookup"><span data-stu-id="b2485-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="b2485-115">入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="b2485-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="b2485-116">アクセス修飾子とアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="b2485-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="b2485-117">クラスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="b2485-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="b2485-118">静的クラスとメンバー</span><span class="sxs-lookup"><span data-stu-id="b2485-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="b2485-119">匿名型</span><span class="sxs-lookup"><span data-stu-id="b2485-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="b2485-120">継承</span><span class="sxs-lookup"><span data-stu-id="b2485-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="b2485-121">メンバーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="b2485-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="b2485-122">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2485-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="b2485-123">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="b2485-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="b2485-124">デリゲート</span><span class="sxs-lookup"><span data-stu-id="b2485-124">Delegates</span></span>](#Delegates)  
  
##  <span data-ttu-id="b2485-125"><a name="Classes"></a> クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b2485-125"><a name="Classes"></a> Classes and Objects</span></span>  
 <span data-ttu-id="b2485-126">"*クラス*" という用語と "*オブジェクト*" という用語は同じ意味で使われる場合がありますが、実際には、クラスはオブジェクトの "*型*" を表すのに対し、オブジェクトはクラスの使用可能な "*インスタンス*" です。</span><span class="sxs-lookup"><span data-stu-id="b2485-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="b2485-127">そのため、オブジェクトを作成する操作は "*インスタンス化*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b2485-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="b2485-128">設計図との対比を使って説明すると、クラスは設計図であり、オブジェクトはその設計図を基にした建築物です。</span><span class="sxs-lookup"><span data-stu-id="b2485-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="b2485-129">クラスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="b2485-130">C# には、"*構造体*" と呼ばれる軽量バージョンのクラスも用意されています。構造体は、大きいオブジェクト配列を作成する必要があり、その配列に使用されるメモリの量を抑えたい場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b2485-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="b2485-131">構造体を定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="b2485-132">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-133">class</span><span class="sxs-lookup"><span data-stu-id="b2485-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="b2485-134">struct</span><span class="sxs-lookup"><span data-stu-id="b2485-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <span data-ttu-id="b2485-135"><a name="Members"></a> クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="b2485-135"><a name="Members"></a> Class Members</span></span>  
 <span data-ttu-id="b2485-136">各クラスには、さまざまな "*クラス メンバー*" を含めることができます。クラス メンバーには、クラスのデータを記述するプロパティ、クラスの動作を定義するメソッド、異なるクラスやオブジェクト間で通信するためのイベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2485-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <span data-ttu-id="b2485-137"><a name="Properties"></a> プロパティとフィールド</span><span class="sxs-lookup"><span data-stu-id="b2485-137"><a name="Properties"></a> Properties and Fields</span></span>  
 <span data-ttu-id="b2485-138">フィールドとプロパティは、オブジェクトに格納されている情報を表します。</span><span class="sxs-lookup"><span data-stu-id="b2485-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="b2485-139">フィールドは、直接読み取ったり設定したりできるので変数と似ています。</span><span class="sxs-lookup"><span data-stu-id="b2485-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="b2485-140">フィールドを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-140">To define a field:</span></span>  
  
```csharp  
Class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="b2485-141">プロパティには get プロシージャと set プロシージャがあり、これらを使用することで値の設定方法や戻り値をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="b2485-142">C# では、プロパティ値を格納するプライベート フィールドを作成するか、または自動実装プロパティと呼ばれる手法を使用できます。自動実装プロパティでは、値を格納するフィールドが背後で自動的に作成され、プロパティ プロシージャの基本的なロジックが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="b2485-143">自動実装プロパティを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="b2485-144">プロパティ値の読み取りと書き込みのために追加の操作を実行する必要がある場合は、プロパティ値を格納するフィールドを定義し、値を格納および取得する基本的なロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="b2485-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 <span data-ttu-id="b2485-145">ほとんどのプロパティには、プロパティ値の設定と取得を行うための両方のメソッドまたはプロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="b2485-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="b2485-146">ただし、読み取り専用または書き込み専用のプロパティを作成して、プロパティの変更や読み取りを制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="b2485-147">C# では、`get` プロパティ メソッドまたは `set` プロパティ メソッドを省略します。</span><span class="sxs-lookup"><span data-stu-id="b2485-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="b2485-148">ただし、自動実装プロパティを読み取り専用または書き込み専用にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b2485-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="b2485-149">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-150">get</span><span class="sxs-lookup"><span data-stu-id="b2485-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="b2485-151">set</span><span class="sxs-lookup"><span data-stu-id="b2485-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <span data-ttu-id="b2485-152"><a name="Methods"></a> メソッド</span><span class="sxs-lookup"><span data-stu-id="b2485-152"><a name="Methods"></a> Methods</span></span>  
 <span data-ttu-id="b2485-153">"*メソッド*" は、オブジェクトが実行できる処理です。</span><span class="sxs-lookup"><span data-stu-id="b2485-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="b2485-154">クラスのメソッドを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="b2485-155">クラスには、同じメソッドに対して、パラメーターの数やパラメーターの型が異なる複数の実装 ("*オーバーロード*") を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b2485-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="b2485-156">メソッドをオーバーロードするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="b2485-157">ほとんどの場合、メソッドはクラス定義内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="b2485-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="b2485-158">ただし、C# では、既存のクラスの実際の定義の外部にメソッドを追加できる "*拡張メソッド*" がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b2485-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="b2485-159">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-160">メソッド</span><span class="sxs-lookup"><span data-stu-id="b2485-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="b2485-161">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="b2485-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <span data-ttu-id="b2485-162"><a name="Constructors"></a> コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b2485-162"><a name="Constructors"></a> Constructors</span></span>  
 <span data-ttu-id="b2485-163">コンストラクターは、特定の型のオブジェクトを作成するときに自動的に実行されるクラス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b2485-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="b2485-164">コンストラクターは、通常、新しいオブジェクトのデータ メンバーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b2485-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="b2485-165">コンストラクターは、クラスの作成時に 1 回だけ実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="b2485-166">また、コンストラクター内のコードは常に、クラス内の他のすべてのコードより先に実行されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="b2485-167">他のメソッドと同じように、コンストラクターにも複数のオーバーロードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="b2485-168">クラスのコンストラクターを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="b2485-169">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-169">For more information, see:</span></span>  
  
 <span data-ttu-id="b2485-170">「[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)」。</span><span class="sxs-lookup"><span data-stu-id="b2485-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <span data-ttu-id="b2485-171"><a name="Finalizers"></a> ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="b2485-171"><a name="Finalizers"></a> Finalizers</span></span>  
 <span data-ttu-id="b2485-172">ファイナライザーは、クラスのインスタンスを破棄するために使います。</span><span class="sxs-lookup"><span data-stu-id="b2485-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="b2485-173">.NET Framework では、アプリケーション内のマネージ オブジェクトのメモリの割り当てと解放は、ガベージ コレクターによって自動的に管理されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="b2485-174">ただし、アプリケーションで作成されるアンマネージ リソースを適切にクリーンアップするために、ファイナライザーも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b2485-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="b2485-175">1 つのクラスに定義できるファイナライザーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="b2485-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="b2485-176">.NET Framework のファイナライザーおよびガベージ コレクションについて詳しくは、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2485-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <span data-ttu-id="b2485-177"><a name="Events"></a> イベント</span><span class="sxs-lookup"><span data-stu-id="b2485-177"><a name="Events"></a> Events</span></span>  
 <span data-ttu-id="b2485-178">クラスやオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。</span><span class="sxs-lookup"><span data-stu-id="b2485-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="b2485-179">イベントを送信する (発生させる) クラスは "*パブリッシャー*" と呼ばれ、イベントを受信する (処理する) クラスは "*サブスクライバー*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b2485-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="b2485-180">イベント、およびイベントの発生と処理の詳細については、「[イベント](../../../standard/events/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2485-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="b2485-181">クラスでイベントを宣言するには、[event](../../../csharp/language-reference/keywords/event.md) キーワードを使います。</span><span class="sxs-lookup"><span data-stu-id="b2485-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="b2485-182">イベントを発生させるには、イベント デリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2485-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="b2485-183">イベントをサブスクライブするには、`+=` 演算子を使用します。イベント サブスクリプションを解除するには、`-=` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2485-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <span data-ttu-id="b2485-184"><a name="NestedClasses"></a> 入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="b2485-184"><a name="NestedClasses"></a> Nested Classes</span></span>  
 <span data-ttu-id="b2485-185">別のクラス内で定義されているクラスを "*入れ子になったクラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="b2485-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="b2485-186">既定では、入れ子になったクラスはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="b2485-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="b2485-187">入れ子になったクラスのインスタンスを作成するには、コンテナー クラスの名前に続けて、ドットと入れ子になったクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2485-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <span data-ttu-id="b2485-188"><a name="AccessModifiers"></a> アクセス修飾子とアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="b2485-188"><a name="AccessModifiers"></a> Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="b2485-189">すべてのクラスおよびクラス メンバーでは、"*アクセス修飾子*" を使って、他のクラスに提供するアクセス レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="b2485-190">次のアクセス修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="b2485-191">C# の修飾子</span><span class="sxs-lookup"><span data-stu-id="b2485-191">C# Modifier</span></span>|<span data-ttu-id="b2485-192">定義</span><span class="sxs-lookup"><span data-stu-id="b2485-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="b2485-193">public</span><span class="sxs-lookup"><span data-stu-id="b2485-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="b2485-194">この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="b2485-195">private</span><span class="sxs-lookup"><span data-stu-id="b2485-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="b2485-196">この型またはメンバーには、同じクラスのコードのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="b2485-197">protected</span><span class="sxs-lookup"><span data-stu-id="b2485-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="b2485-198">この型またはメンバーには、同じクラスまたは派生クラスのコードのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="b2485-199">internal</span><span class="sxs-lookup"><span data-stu-id="b2485-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="b2485-200">この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="b2485-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="b2485-201">内部の保護</span><span class="sxs-lookup"><span data-stu-id="b2485-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="b2485-202">この型またはメンバーには、同じアセンブリ内の任意のコード、または別のアセンブリ内の任意の派生クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="b2485-203">保護されたプライベート</span><span class="sxs-lookup"><span data-stu-id="b2485-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="b2485-204">型またはメンバーは、同じクラスまたは基底クラスのアセンブリ内で派生クラスでのコードでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="b2485-205">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2485-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <span data-ttu-id="b2485-206"><a name="InstantiatingClasses"></a> クラスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="b2485-206"><a name="InstantiatingClasses"></a> Instantiating Classes</span></span>  
 <span data-ttu-id="b2485-207">オブジェクトを作成するには、クラスをインスタンス化する (クラスのインスタンスを作成する) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2485-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="b2485-208">クラスをインスタンス化した後は、インスタンスのプロパティやフィールドに値を割り当てたり、クラスのメソッドを呼び出したりできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="b2485-209">クラスのインスタンス化のプロセスでプロパティに値を割り当てるには、オブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2485-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="b2485-210">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-211">new 演算子</span><span class="sxs-lookup"><span data-stu-id="b2485-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="b2485-212">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="b2485-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <span data-ttu-id="b2485-213"><a name="Static"></a> 静的クラスとメンバー</span><span class="sxs-lookup"><span data-stu-id="b2485-213"><a name="Static"></a> Static Classes and Members</span></span>  
 <span data-ttu-id="b2485-214">クラスの静的メンバーは、クラスのすべてのインスタンスで共有されるプロパティ、プロシージャ、またはフィールドです。</span><span class="sxs-lookup"><span data-stu-id="b2485-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="b2485-215">静的メンバーを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="b2485-216">静的メンバーにアクセスするには、クラスのオブジェクトを作成せずにクラスの名前を使います。</span><span class="sxs-lookup"><span data-stu-id="b2485-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="b2485-217">C# の静的クラスには静的メンバーだけがあり、インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="b2485-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="b2485-218">また、静的メンバーから、非静的のプロパティ、フィールド、またはメソッドにアクセスすることもできません。</span><span class="sxs-lookup"><span data-stu-id="b2485-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="b2485-219">詳しくは、「[static](../../../csharp/language-reference/keywords/static.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2485-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <span data-ttu-id="b2485-220"><a name="AnonymousTypes"></a> 匿名型</span><span class="sxs-lookup"><span data-stu-id="b2485-220"><a name="AnonymousTypes"></a> Anonymous Types</span></span>  
 <span data-ttu-id="b2485-221">匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="b2485-222">クラスは、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="b2485-223">このクラスには使用可能な名前がなく、オブジェクトの宣言時に指定したプロパティが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="b2485-224">匿名型のインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="b2485-225">詳しくは、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2485-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <span data-ttu-id="b2485-226"><a name="Inheritance"></a> 継承</span><span class="sxs-lookup"><span data-stu-id="b2485-226"><a name="Inheritance"></a> Inheritance</span></span>  
 <span data-ttu-id="b2485-227">継承を使用すると、他のクラスで定義されている動作を再利用、拡張、および変更する新しいクラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="b2485-228">メンバーが継承される側のクラスを "*基底クラス*" と呼び、メンバーを継承する側のクラスを "*派生クラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="b2485-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="b2485-229">ただし、C# のすべてのクラスは、.NET のクラス階層構造をサポートしてすべてのクラスに下位レベルのサービスを提供する <xref:System.Object> クラスを暗黙的に継承します。</span><span class="sxs-lookup"><span data-stu-id="b2485-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2485-230">C# は多重継承をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b2485-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="b2485-231">つまり、派生クラスに対して指定できる基底クラスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="b2485-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="b2485-232">基底クラスを継承するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 <span data-ttu-id="b2485-233">既定では、すべてのクラスが継承可能になります。</span><span class="sxs-lookup"><span data-stu-id="b2485-233">By default all classes can be inherited.</span></span> <span data-ttu-id="b2485-234">ただし、クラスを基底クラスとして使用できないように指定したり、基底クラスとしてのみ使用できるクラスを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="b2485-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="b2485-235">クラスを基底クラスとして使用できないように指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="b2485-236">クラスが基底クラスとしてのみ使用され、インスタンス化できないように指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="b2485-237">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-238">sealed</span><span class="sxs-lookup"><span data-stu-id="b2485-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="b2485-239">abstract</span><span class="sxs-lookup"><span data-stu-id="b2485-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <span data-ttu-id="b2485-240"><a name="Overriding"></a> メンバーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="b2485-240"><a name="Overriding"></a> Overriding Members</span></span>  
 <span data-ttu-id="b2485-241">既定では、派生クラスは基底クラスのすべてのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="b2485-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="b2485-242">継承したメンバーの動作を変更する場合は、そのメンバーをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2485-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="b2485-243">つまり、派生クラスに、メソッド、プロパティ、またはイベントの新しい実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="b2485-244">プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2485-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="b2485-245">C# の修飾子</span><span class="sxs-lookup"><span data-stu-id="b2485-245">C# Modifier</span></span>|<span data-ttu-id="b2485-246">定義</span><span class="sxs-lookup"><span data-stu-id="b2485-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="b2485-247">virtual</span><span class="sxs-lookup"><span data-stu-id="b2485-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="b2485-248">派生クラスでのクラス メンバーのオーバーライドを許可します。</span><span class="sxs-lookup"><span data-stu-id="b2485-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="b2485-249">override</span><span class="sxs-lookup"><span data-stu-id="b2485-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="b2485-250">基底クラスで定義されている仮想メンバー (オーバーライドできるメンバー) をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b2485-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="b2485-251">abstract</span><span class="sxs-lookup"><span data-stu-id="b2485-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="b2485-252">派生クラスでのクラス メンバーのオーバーライドを必須にします。</span><span class="sxs-lookup"><span data-stu-id="b2485-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="b2485-253">new 修飾子</span><span class="sxs-lookup"><span data-stu-id="b2485-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="b2485-254">基底クラスから継承されたメンバーを隠ぺいします。</span><span class="sxs-lookup"><span data-stu-id="b2485-254">Hides a member inherited from a base class</span></span>|  
  
##  <span data-ttu-id="b2485-255"><a name="Interfaces"></a> インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2485-255"><a name="Interfaces"></a> Interfaces</span></span>  
 <span data-ttu-id="b2485-256">インターフェイスは、クラスと同様にプロパティ、メソッド、およびイベントのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="b2485-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="b2485-257">ただし、クラスとは異なり、インターフェイスは実装を提供しません。</span><span class="sxs-lookup"><span data-stu-id="b2485-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="b2485-258">インターフェイスはクラスによって実装され、クラスとは別のエンティティとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="b2485-259">インターフェイスを実装するクラスは、そのインターフェイスのあらゆる機能を定義に従って厳密に実装する必要があります。この点で、インターフェイスはコントラクトを表しています。</span><span class="sxs-lookup"><span data-stu-id="b2485-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="b2485-260">インターフェイスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="b2485-261">クラスにインターフェイスを実装するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="b2485-262">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="b2485-263">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2485-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="b2485-264">interface</span><span class="sxs-lookup"><span data-stu-id="b2485-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <span data-ttu-id="b2485-265"><a name="Generics"></a> ジェネリック</span><span class="sxs-lookup"><span data-stu-id="b2485-265"><a name="Generics"></a> Generics</span></span>  
 <span data-ttu-id="b2485-266">.NET Framework のクラス、構造体、インターフェイス、およびメソッドは、格納または使用できるオブジェクトの型を定義する "*型パラメーター*" を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="b2485-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="b2485-267">ジェネリックの最も一般的な例として、コレクションがあります。コレクションには、その中に格納されるオブジェクトの型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="b2485-268">ジェネリック クラスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-268">To define a generic class:</span></span>  
  
```csharp  
Public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="b2485-269">ジェネリック クラスのインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="b2485-270">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-271">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="b2485-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="b2485-272">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="b2485-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <span data-ttu-id="b2485-273"><a name="Delegates"></a> デリゲート</span><span class="sxs-lookup"><span data-stu-id="b2485-273"><a name="Delegates"></a> Delegates</span></span>  
 <span data-ttu-id="b2485-274">"*デリゲート*" は、メソッド シグネチャを定義する型であり、互換性のあるシグネチャを持つ任意のメソッドへの参照を提供できます。</span><span class="sxs-lookup"><span data-stu-id="b2485-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="b2485-275">メソッドは、デリゲートを使用して起動する (呼び出す) ことができます。</span><span class="sxs-lookup"><span data-stu-id="b2485-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="b2485-276">デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2485-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2485-277">イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。</span><span class="sxs-lookup"><span data-stu-id="b2485-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="b2485-278">デリゲートを使用したイベント処理について詳しくは、「[イベント](../../../standard/events/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b2485-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="b2485-279">デリゲートを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="b2485-280">デリゲートで指定されたシグネチャに一致するメソッドへの参照を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b2485-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 <span data-ttu-id="b2485-281">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b2485-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b2485-282">デリゲート</span><span class="sxs-lookup"><span data-stu-id="b2485-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="b2485-283">delegate</span><span class="sxs-lookup"><span data-stu-id="b2485-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2485-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2485-284">See Also</span></span>  
 [<span data-ttu-id="b2485-285">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b2485-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
